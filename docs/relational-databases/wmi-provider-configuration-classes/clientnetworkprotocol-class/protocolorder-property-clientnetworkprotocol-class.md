---
description: Свойство ProtocolOrder (класс ClientNetworkProtocol)
title: Свойство ProtocolOrder (класс clientnetworkprotocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolOrder Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 51b686edb6ac9e93862c5f90f06bb7370fe47a9a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89523168"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a>Свойство ProtocolOrder (класс ClientNetworkProtocol)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Возвращает порядковый номер текущего указанного сетевого протокола клиента, заданного методом [SetOrderValue (класс ClientNetworkProtocol)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , определяющее порядковый номер текущего указанного сетевого протокола клиента, заданного методом **OrderValue** . Если сетевой протокол клиента отключен, это значение будет равно нулю.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)   
 [Настройка сетевых протоколов клиента и сетевых библиотек](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
