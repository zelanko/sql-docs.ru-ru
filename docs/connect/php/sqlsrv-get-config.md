---
title: sqlsrv_get_config | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- sqlsrv_get_config
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_get_config
- sqlsrv_get_config
ms.assetid: ce2befc2-af98-45bb-8d41-60f1674dccfc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ffdebecc3121e8707b3e58cd1302fe02f9897106
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MTE
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlsrvgetconfig"></a>sqlsrv_get_config
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Возвращает текущее значение указанного параметра конфигурации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_get_config( string $setting )  
```  
  
#### <a name="parameters"></a>Параметры  
*$setting*: параметр конфигурации, для которого возвращается значение. Список настраиваемых параметров см. в статье [sqlsrv_configure](../../connect/php/sqlsrv-configure.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение параметра, определяемое параметром *$setting* . Если указано недопустимое значение, возвращается значение **false** , а в коллекцию ошибок добавляется ошибка.  
  
## <a name="remarks"></a>Remarks  
Если **false** config **sqlsrv_get_config**, необходимо вызвать [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) , чтобы определить, произошла ли ошибка или значение **false** параметра определено параметром *$setting* .  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)  

[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)  
  
