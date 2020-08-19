---
description: Метод RemoveCertificate (класс ServerSettings)
title: Метод RemoveCertificate (класс serversettings)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- RemoveCertificate Method (ServerSettings Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 9ffdbc39-93f5-48fb-859a-86a3ad545827
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8de2c4e631ac0455fa16d2f4ce70f3e980c467df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427256"
---
# <a name="removecertificate-method-serversettings-class"></a>Метод RemoveCertificate (класс ServerSettings)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Удаляет текущий сертификат безопасности из экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.RemoveCertificate()  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса ServerSettings](../../../relational-databases/wmi-provider-configuration-classes/serversettings-class/serversettings-class.md) , представляющий параметры сервера в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение u**Int32** , равное 0, если служба была успешно изменена, 1, если запрос не поддерживается, и любое другое число для указания ошибки.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Конфигурирование сетевых протоколов сервера и сетевых библиотек](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
