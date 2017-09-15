---
title: "sqlsrv_get_config | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
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
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a5712c6f98da82b422e76a7cb6c8d07adac86b5e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
  
## <a name="remarks"></a>Замечания  
Если **false** config **sqlsrv_get_config**, необходимо вызвать [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) , чтобы определить, произошла ли ошибка или значение **false** параметра определено параметром *$setting* .  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)  
[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)  
  

