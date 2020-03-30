---
title: sqlsrv_configure | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_configure
apitype: NA
helpviewer_keywords:
- sqlsrv_configure
- API Reference, sqlsrv_configure
ms.assetid: 9393f975-a4ef-4c50-b4dd-14892fc55cc9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b98533dcc1589e07bc8ae37562bf6734077a78f1
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67935802"
---
# <a name="sqlsrv_configure"></a>sqlsrv_configure
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Изменяет параметры обработки ошибок и ведения журнала.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_configure( string $setting, mixed $value )  
```  
  
#### <a name="parameters"></a>Параметры  
*$setting*: имя настраиваемого параметра. Список параметров приведен в таблице ниже.  
  
*$value*: значение, применяемое к настройке, указанной в параметре *$setting* . Возможные значения этого параметра зависят от указанной настройки. В следующей таблице перечислены возможные сочетания.  
  
|Параметр|Возможные значения параметра $value (целочисленный эквивалент в круглых скобках)|Значение по умолчанию|  
|-----------|------------------------------------------------------------------------------|-----------------|  
|ClientBufferMaxKBSize<sup>1</sup>|Неотрицательное число вплоть до предела памяти PHP.<br /><br />Число должно быть больше нуля.|10240 КБ|  
|LogSeverity<sup>2</sup>|SQLSRV_LOG_SEVERITY_ALL (-1)<br /><br />SQLSRV_LOG_SEVERITY_ERROR (1)<br /><br />SQLSRV_LOG_SEVERITY_NOTICE (4)<br /><br />SQLSRV_LOG_SEVERITY_WARNING (2)|SQLSRV_LOG_SEVERITY_ERROR (1)|  
|LogSubsystems<sup>2</sup>|SQLSRV_LOG_SYSTEM_ALL (-1)<br /><br />SQLSRV_LOG_SYSTEM_CONN (2)<br /><br />SQLSRV_LOG_SYSTEM_INIT (1)<br /><br />SQLSRV_LOG_SYSTEM_OFF (0)<br /><br />SQLSRV_LOG_SYSTEM_STMT (4)<br /><br />SQLSRV_LOG_SYSTEM_UTIL (8)|SQLSRV_LOG_SYSTEM_OFF (0)|  
|WarningsReturnAsErrors<sup>3</sup>|(1) — **true** или (0) — **false**|**true** (1)|  
  
## <a name="return-value"></a>Возвращаемое значение  
Если **sqlsrv_configure** вызывается с неподдерживаемым параметром или значением, функция возвращает значение **false**. В противном случае функция возвращает значение **true**.  
  
## <a name="remarks"></a>Remarks  
(1) Дополнительные сведения о клиентских запросах см. в статье [Типы курсоров (драйвер SQLSRV)](../../connect/php/cursor-types-sqlsrv-driver.md).  
  
(2) Дополнительные сведения о ведении журнала см. в статье [Ведение журнала](../../connect/php/logging-activity.md).  
  
(3) Дополнительные сведения о настройке обработки ошибок и предупреждений см. в статье [Практическое руководство. Настройка обработки ошибок и предупреждений с помощью драйвера SQLSRV](../../connect/php/how-to-configure-error-and-warning-handling-using-the-sqlsrv-driver.md).  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Руководство по программированию драйверов Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md) 
  
