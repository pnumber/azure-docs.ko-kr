---
title: 가상 네트워크 피어링으로 가상 네트워크 연결 - Azure CLI | Microsoft Docs
description: 가상 네트워크 피어링을 사용하여 가상 네트워크를 연결하는 방법을 알아봅니다.
services: virtual-network
documentationcenter: virtual-network
author: jimdial
manager: jeconnoc
editor: ''
tags: azure-resource-manager
ms.assetid: ''
ms.service: virtual-network
ms.devlang: azurecli
ms.topic: ''
ms.tgt_pltfrm: virtual-network
ms.workload: infrastructure
ms.date: 03/13/2018
ms.author: jdial
ms.custom: ''
ms.openlocfilehash: bbf2e757e2d9ad76c59394ba0138a61fd4029d15
ms.sourcegitcommit: 8aab1aab0135fad24987a311b42a1c25a839e9f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2018
---
# <a name="connect-virtual-networks-with-virtual-network-peering-using-the-azure-cli"></a>Azure CLI를 사용하여 가상 네트워크 피어링으로 가상 네트워크 연결

가상 네트워크 피어링을 사용하여 가상 네트워크를 서로 연결할 수 있습니다. 가상 네트워크가 피어링되면 두 가상 네트워크에 있는 리소스가 같은 가상 네트워크에 있는 리소스인 것처럼 같은 대기 시간 및 대역폭으로 서로 통신할 수 있습니다. 이 문서에서는 다음 방법을 설명합니다.

> [!div class="checklist"]
> * 두 가상 네트워크 만들기
> * 가상 네트워크 피어링을 사용하여 두 가상 네트워크 연결
> * 각 가상 네트워크에 VM(가상 머신) 배포
> * VM 간 통신

Azure 구독이 아직 없는 경우 시작하기 전에 [무료 계정](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)을 만듭니다.

[!INCLUDE [cloud-shell-try-it.md](../../includes/cloud-shell-try-it.md)]

CLI를 로컬로 설치하여 사용하도록 선택한 경우 이 빠른 시작에서는 Azure CLI 버전 2.0.28 이상을 실행해야 합니다. 버전을 확인하려면 `az --version`을 실행합니다. 설치 또는 업그레이드해야 하는 경우 [Azure CLI 2.0 설치](/cli/azure/install-azure-cli)를 참조하세요. 

## <a name="create-virtual-networks"></a>가상 네트워크 만들기

가상 네트워크를 만들기 전에 가상 네트워크에 대한 리소스 그룹과 이 아티클에서 만든 다른 모든 리소스를 만들어야 합니다. [az group create](/cli/azure/group#az_group_create)를 사용하여 리소스 그룹을 만듭니다. 다음 예제에서는 *eastus* 위치에 *myResourceGroup*이라는 리소스 그룹을 만듭니다.

```azurecli-interactive 
az group create --name myResourceGroup --location eastus
```

[az network vnet create](/cli/azure/network/vnet#az_network_vnet_create)를 사용하여 가상 네트워크를 만듭니다. 다음 예제에서는 주소 접두사 *10.0.0.0/16*을 사용하는 *myVirtualNetwork1*이라는 가상 네트워크를 만듭니다.

```azurecli-interactive 
az network vnet create \
  --name myVirtualNetwork1 \
  --resource-group myResourceGroup \
  --address-prefixes 10.0.0.0/16 \
  --subnet-name Subnet1 \
  --subnet-prefix 10.0.0.0/24
```

주소 접두사 *10.1.0.0/16*을 포함하는 *myVirtualNetwork2*라는 가상 네트워크를 만듭니다.

```azurecli-interactive 
az network vnet create \
  --name myVirtualNetwork2 \
  --resource-group myResourceGroup \
  --address-prefixes 10.1.0.0/16 \
  --subnet-name Subnet1 \
  --subnet-prefix 10.1.0.0/24
```

## <a name="peer-virtual-networks"></a>가상 네트워크 피어링

가상 네트워크 ID 간에 피어링이 설정됩니다. 따라서 먼저 [az network vnet show](/cli/azure/network/vnet#az_network_vnet_show)를 사용하여 각 가상 네트워크의 ID를 가져오고 ID를 변수에 저장해야 합니다.

```azurecli-interactive
# Get the id for myVirtualNetwork1.
vNet1Id=$(az network vnet show \
  --resource-group myResourceGroup \
  --name myVirtualNetwork1 \
  --query id --out tsv)

# Get the id for myVirtualNetwork2.
vNet2Id=$(az network vnet show \
  --resource-group myResourceGroup \
  --name myVirtualNetwork2 \
  --query id \
  --out tsv)
```

[az network vnet peering create](/cli/azure/network/vnet/peering#az_network_vnet_peering_create)를 사용하여 *myVirtualNetwork1*에서 *myVirtualNetwork2*로 피어링을 만듭니다. `--allow-vnet-access` 매개 변수를 지정하지 않으면 피어링이 설정되지만 이를 통해 통신이 전달될 수 없습니다.

```azurecli-interactive
az network vnet peering create \
  --name myVirtualNetwork1-myVirtualNetwork2 \
  --resource-group myResourceGroup \
  --vnet-name myVirtualNetwork1 \
  --remote-vnet-id $vNet2Id \
  --allow-vnet-access
```

이전 명령 실행 후 반환된 출력에서 **peeringState**는 *Initiated*로 표시됩니다. *myVirtualNetwork2*에서 *myVirtualNetwork1*으로 피어링을 만들 때까지 해당 피어링은 *Initiated* 상태를 유지합니다. *myVirtualNetwork2*에서 *myVirtualNetwork1*으로 피어링을 만듭니다. 

```azurecli-interactive
az network vnet peering create \
  --name myVirtualNetwork2-myVirtualNetwork1 \
  --resource-group myResourceGroup \
  --vnet-name myVirtualNetwork2 \
  --remote-vnet-id $vNet1Id \
  --allow-vnet-access
```

이전 명령 실행 후 반환된 출력에서 **peeringState**는 *Connected*로 표시됩니다. 또한 Azure에서 *myVirtualNetwork1-myVirtualNetwork2* 피어링의 피어링 상태가 *Connected*로 변경되었습니다. [az network vnet peering show](/cli/azure/network/vnet/peering#az_network_vnet_peering_show)를 사용하여 *myVirtualNetwork1-myVirtualNetwork2* 피어링에 대한 피어링 상태가 *Connected*로 변경되었는지 확인합니다.

```azurecli-interactive
az network vnet peering show \
  --name myVirtualNetwork1-myVirtualNetwork2 \
  --resource-group myResourceGroup \
  --vnet-name myVirtualNetwork1 \
  --query peeringState
```

두 가상 네트워크의 피어링에 대한 **peeringState**가 *Connected*가 될 때까지, 한 가상 네트워크의 리소스는 다른 가상 네트워크의 리소스와 통신할 수 없습니다. 

## <a name="create-virtual-machines"></a>가상 머신 만들기

이후 단계에서 서로 통신할 수 있도록 각 가상 네트워크에서 VM을 만듭니다.

### <a name="create-the-first-vm"></a>첫 번째 VM 만들기

[az vm create](/cli/azure/vm#az_vm_create)로 VM을 만듭니다. 다음 예제에서는 *myVirtualNetwork1* 가상 네트워크에 이름이 *myVm1*인 VM을 만듭니다. 또한 기본 키 위치에 SSH 키가 없는 경우 해당 명령이 이 키를 만듭니다. 특정 키 집합을 사용하려면 `--ssh-key-value` 옵션을 사용합니다. `--no-wait` 옵션은 백그라운드에서 VM을 만들기 때문에 다음 단계를 계속 진행할 수 있습니다.

```azurecli-interactive
az vm create \
  --resource-group myResourceGroup \
  --name myVm1 \
  --image UbuntuLTS \
  --vnet-name myVirtualNetwork1 \
  --subnet Subnet1 \
  --generate-ssh-keys \
  --no-wait
```

### <a name="create-the-second-vm"></a>두 번째 VM 만들기

*myVirtualNetwork2* 가상 네트워크에 VM을 만듭니다.

```azurecli-interactive 
az vm create \
  --resource-group myResourceGroup \
  --name myVm2 \
  --image UbuntuLTS \
  --vnet-name myVirtualNetwork2 \
  --subnet Subnet1 \
  --generate-ssh-keys
```

VM을 만드는 데 몇 분이 걸립니다. VM을 만든 후 Azure CLI는 다음 예제와 비슷한 정보를 표시합니다. 

```azurecli 
{
  "fqdns": "",
  "id": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVm2",
  "location": "eastus",
  "macAddress": "00-0D-3A-23-9A-49",
  "powerState": "VM running",
  "privateIpAddress": "10.1.0.4",
  "publicIpAddress": "13.90.242.231",
  "resourceGroup": "myResourceGroup"
}
```

**publicIpAddress**를 기록해 둡니다. 이 주소는 이후 단계에서 인터넷을 통해 VM에 액세스하는 데 사용됩니다.

## <a name="communicate-between-vms"></a>VM 간 통신

다음 명령을 사용하여 *myVm2* VM으로 SSH 세션을 만듭니다. `<publicIpAddress>`를 VM의 공용 IP 주소로 바꿉니다. 이전 예제의 공용 IP 주소는*13.90.242.231*입니다.

```bash 
ssh <publicIpAddress>
```

*myVirtualNetwork1*에서 VM을 ping합니다.

```bash 
ping 10.0.0.4 -c 4
```

4개의 응답을 받게 됩니다. 

*myVm2* VM에 대한 SSH 세션을 닫습니다. 

## <a name="clean-up-resources"></a>리소스 정리

더 이상 필요하지 않은 경우 [az group delete](/cli/azure/group#az_group_delete)를 사용하여 리소스 그룹 및 그룹에 포함된 모든 리소스를 제거합니다.

```azurecli-interactive 
az group delete --name myResourceGroup --yes
```

**<a name="register"></a>전역 가상 네트워크 피어링 미리 보기에 등록**

동일한 지역의 가상 네트워크 피어링은 일반 공급됩니다. 서로 다른 지역에서 가상 네트워크를 피어링하는 기능은 현재 미리 보기 상태입니다. 사용 가능한 지역에 대해서는 [가상 네트워크 업데이트](https://azure.microsoft.com/updates/?product=virtual-network)를 참조하세요. 여러 지역에 걸쳐 가상 네트워크를 피어링하려면 먼저 (피어링하려는 각 가상 네트워크가 있는 구독 내에서) 다음 단계를 완료하여 미리 보기에 등록해야 합니다.

1. 다음 명령을 입력하여 미리 보기에 등록합니다.

  ```azurecli-interactive
  az feature register --name AllowGlobalVnetPeering --namespace Microsoft.Network
  az provider register --name Microsoft.Network
  ```

2. 다음 명령을 입력하여 미리 보기에 등록되었는지 확인합니다.

  ```azurecli-interactive
  az feature show --name AllowGlobalVnetPeering --namespace Microsoft.Network
  ```

  이전 명령을 입력한 후에 받은 **RegistrationState** 출력이 두 구독에 대해 **Registered**가 되기 전에 다른 지역의 가상 네트워크를 피어링하려고 하면 피어링이 실패합니다.

## <a name="next-steps"></a>다음 단계

이 아티클에서는 가상 네트워크 피어링을 사용하여 두 네트워크를 연결하는 방법을 배웠습니다. 이 문서에서는 가상 네트워크 피어링을 사용하여 동일한 Azure 위치에 있는 두 네트워크를 연결하는 방법을 배웠습니다. [다른 Azure 구독](create-peering-different-subscriptions.md#portal)의 [다른 지역](#register)에 있는 가상 네트워크를 피어링하고 피어링을 사용하여 [허브 및 스포크 네트워크 디자인](/azure/architecture/reference-architectures/hybrid-networking/hub-spoke?toc=%2fazure%2fvirtual-network%2ftoc.json#vnet-peering)을 만들 수도 있습니다. 프로덕션 가상 네트워크를 피어링하기 전에, [피어링 개요](virtual-network-peering-overview.md), [피어링 관리](virtual-network-manage-peering.md) 및 [가상 네트워크 제한](../azure-subscription-service-limits.md?toc=%2fazure%2fvirtual-network%2ftoc.json#azure-resource-manager-virtual-networking-limits)에 충분히 익숙해지는 것이 좋습니다.

VPN을 통해 [자신의 컴퓨터를 가상 네트워크에 연결](../vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal.md?toc=%2fazure%2fvirtual-network%2ftoc.json)하고, 가상 네트워크 또는 피어링된 가상 네트워크의 리소스와 상호 작용할 수 있습니다. 재사용이 가능한 스크립트에 대한 스크립트 샘플을 계속 진행하여 가상 네트워크 아티클에 설명된 많은 태스크를 완료할 수 있습니다.

> [!div class="nextstepaction"]
> [가상 네트워크 스크립트 예제](../networking/cli-samples.md?toc=%2fazure%2fvirtual-network%2ftoc.json)
