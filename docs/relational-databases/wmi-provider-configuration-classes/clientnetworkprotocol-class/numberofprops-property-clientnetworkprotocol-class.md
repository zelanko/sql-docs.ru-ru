---
description: Свойство NumberOfProps (класс ClientNetworkProtocol)
title: Свойство NumberOfProps (класс clientnetworkprotocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- NumberOfProps Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- NumberOfProps property
ms.assetid: 9c508bc5-c7a4-4db1-b3bf-c7098c66435a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3af0d8a773565cb776283e614dd7925624e9fd44
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88418878"
---
# <a name="numberofprops-property-clientnetworkprotocol-class"></a>Свойство NumberOfProps (класс ClientNetworkProtocol)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Возвращает количество свойств сетевого протокола клиента, заданного [методом SetOrderValue (класс класс clientnetworkprotocol)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.NumberOfProps [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, определяющее число свойств сетевого протокола клиента.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
