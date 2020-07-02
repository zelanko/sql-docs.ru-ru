---
title: Свойство Enabled (класс servernetworkprotocolipaddress)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Enabled Property (ServerNetworkProtocolIpAddress Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Enabled property
ms.assetid: 870fd4d0-6c77-462a-b480-d42eb044b2e7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a6a033243b552495734a9a3cc9aad69e0518d2c2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786061"
---
# <a name="enabled-property-servernetworkprotocolipaddress-class"></a>Свойство Enabled (класс ServerNetworkProtocolIPAddress)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Возвращает свойство логического типа, указывающее, включен ли IP-адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.Enabled [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 A [класса ServerNetworkProtocolIPAdress](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) , который представляет IP-адрес сетевого протокола для экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Логическое значение, указывающее, включен ли IP-адрес: **true** , если включен; в противном случае — **false** .  
  
## <a name="see-also"></a>См. также  
 [Конфигурирование сетевых протоколов сервера и сетевых библиотек](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
