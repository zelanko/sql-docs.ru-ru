---
description: Свойство Properties (класс ClientNetworkProtocol)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ba9dfe13c38f4f29dd06c313c16896f34857a746
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91890357"
---
# <a name="properties-property-clientnetworkprotocol-class"></a>Свойство Properties (класс ClientNetworkProtocol)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Возвращает свойства, связанные с текущим сетевым протоколом клиента, заданным в параметре [Настройка клиентских протоколов](../../../database-engine/configure-windows/configure-client-protocols.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Properties [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Массив объектов класса [ClientNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) , представляющих свойства, поддерживаемые текущим сетевым протоколом клиента, на который ссылается свойство **OrderValue** .  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Настройка сетевых протоколов клиента и сетевых библиотек](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
