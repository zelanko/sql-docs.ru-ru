---
description: Свойство ProtocolName (класс ClientNetworkProtocolProperty)
title: Свойство ProtocolName (класс clientnetworkprotocolproperty)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolName Property (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolName property
ms.assetid: 77c53201-4fab-481e-9b3b-57d0b8b83113
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0f8d790da05fb4a73aab0c96f1b35a56c26158b4
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537210"
---
# <a name="protocolname-property-clientnetworkprotocolproperty-class"></a>Свойство ProtocolName (класс ClientNetworkProtocolProperty)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Возвращает имя протокола, владеющего текущим свойством, на которое ссылается значение свойства [PropertyIdx (класс ClientNetworkProtocolProperty)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/propertyidx-property-clientnetworkprotocolproperty-class.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ProtocolName [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ClientNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) , который представляет атрибут сетевого протокола, используемого [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Строковое значение, указывающее имя протокола, которому принадлежит свойство.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка клиентских протоколов](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
