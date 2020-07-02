---
title: Метод SetDisable (класс servernetworkprotocolipaddress)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDisable Method (ServerNetworkProtocolIPAddress Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDisable method
ms.assetid: 7a7cc8cc-9fb8-4bf5-b483-2150d633ee10
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3014658abcfe20056353643e0ddd9e82afec4fb8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768195"
---
# <a name="setdisable-method-servernetworkprotocolipaddress-class"></a>Метод SetDisable (класс ServerNetworkProtocolIPAddress)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Отключает IP-адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetDisable()  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса ServerNetworkProtocolIPAdress](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) , который представляет IP-адрес сетевого протокола для экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Конфигурирование сетевых протоколов сервера и сетевых библиотек](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
