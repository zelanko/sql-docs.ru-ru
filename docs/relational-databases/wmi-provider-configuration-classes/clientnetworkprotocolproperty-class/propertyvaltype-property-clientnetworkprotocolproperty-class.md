---
title: Свойство PropertyValType (класс ClientNetworkProtocolProperty) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PropertyValType Property (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- PropertyValType property
ms.assetid: 624b9bdd-ed93-4140-bd4e-00d714a2558c
caps.latest.revision: 31
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 01d3faa197b9d0fb826528202cee7c03bccadb80
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="propertyvaltype-property-clientnetworkprotocolproperty-class"></a>Свойство PropertyValType (класс ClientNetworkProtocolProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает тип данных значения, хранящегося в свойстве, на которое ссылается значение свойства [PropertyIdx (класс ClientNetworkProtocolProperty)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/propertyidx-property-clientnetworkprotocolproperty-class.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.PropertyValType [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 A [класса ClientNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) , который представляет атрибут сетевого протокола, используемого [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , представляющее тип данных для значения свойства.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Настройка клиентских протоколов](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
