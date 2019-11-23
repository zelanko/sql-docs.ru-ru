---
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 030e35fca5fc6a2dbc31a16fc1bc1cb0e5c9fea5
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73660210"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a>Свойство ProtocolOrder (класс ClientNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает порядковый номер текущего указанного сетевого протокола клиента, заданного методом [SetOrderValue (класс ClientNetworkProtocol)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 A [класса ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , определяющее порядковый номер текущего указанного сетевого протокола клиента, заданного методом **OrderValue** . Если сетевой протокол клиента отключен, это значение будет равно нулю.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также статью  
 [Настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx)   
 [Настройка клиентских сетевых протоколов и сетевых библиотек](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
