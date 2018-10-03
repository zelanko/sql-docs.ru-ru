---
title: Свойство PropertyIdx (класс ClientNetworkProtocolProperty) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- PropertyIdx Property (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- PropertyIdx property
ms.assetid: d7845962-ac68-4435-9c59-70ec450fec88
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 47cb12cd6ea733f1e89ac51c9062b7e65b93b3d1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670602"
---
# <a name="propertyidx-property-clientnetworkprotocolproperty-class"></a>Свойство PropertyIdx (класс ClientNetworkProtocolProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает или задает значение индекса свойства в массиве свойств, на которое ссылается свойство [Properties (класс ClientNetworkProtocol)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/properties-property-clientnetworkprotocol-class.md) объекта [ClientNetworkProtocol Class](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.PropertyIdx [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ClientNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) , который представляет атрибут сетевого протокола, используемого [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , задающее значение индекса массива для текущего свойства.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка клиентских протоколов](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
