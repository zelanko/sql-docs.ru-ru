---
title: Свойство Properties (класс clientnetworkprotocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Properties Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Properties property
ms.assetid: 7e0a4e38-4555-4750-8fd3-4425b29e6aa1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fcaf075988d28d24f2daedefbdaa1c7f9e451f46
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889014"
---
# <a name="properties-property-clientnetworkprotocol-class"></a>Свойство Properties (класс ClientNetworkProtocol)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Возвращает свойства, связанные с текущим сетевым протоколом клиента, заданным в параметре [Настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Properties [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Массив объектов класса [ClientNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) , представляющих свойства, поддерживаемые текущим сетевым протоколом клиента, на который ссылается свойство **OrderValue** .  
  
## <a name="remarks"></a>Комментарии  
  
## <a name="see-also"></a>См. также  
 [Настройка сетевых протоколов клиента и сетевых библиотек](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
