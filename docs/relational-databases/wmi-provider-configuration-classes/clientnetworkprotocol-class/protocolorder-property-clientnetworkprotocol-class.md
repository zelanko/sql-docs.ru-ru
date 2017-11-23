---
title: "Свойство ProtocolOrder (класс ClientNetworkProtocol) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ProtocolOrder Property (ClientNetworkProtocol Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 74910097784812b920233198a81fede673d60443
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a>Свойство ProtocolOrder (класс ClientNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Возвращает порядковый номер текущего указанного клиентского сетевого протокола в соответствии с [Setordervalue (класс ClientNetworkProtocol)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 A [класса ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , определяющее порядковый номер текущего указанного сетевого протокола клиента, заданного методом **OrderValue** . Если сетевой протокол клиента отключен, это значение будет равно нулю.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Настройка клиентских протоколов](http://technet.microsoft.com/library/ms181035.aspx)   
 [Настройка клиентских сетевых протоколов и сетевых библиотек](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
