---
title: По умолчанию для типов данных SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: 65c7c211-96d3-4e65-a1de-1fe8d21348e7
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c3aea23b8a3fcf3632b164846a3addaba7a501e6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="default-sql-server-data-types"></a>Типы данных SQL Server по умолчанию
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

При отправке данных на сервер [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] преобразует данные из своего типа данных PHP в тип данных SQL Server, если пользователь не задал тип данных SQL Server. Следующая таблица содержит тип данных PHP (тип данных, отправляемых на сервер) и тип данных SQL Server по умолчанию тип (тип данных, в который преобразуются данные). Дополнительные сведения об указании типов данных при отправке данных на сервер см. в статье [Практическое руководство. Указание типов данных SQL Server при использовании драйвера SQLSRV](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md).  
  
|Тип данных PHP|Тип SQL Server по умолчанию в драйвере SQLSRV|Тип SQL Server по умолчанию в драйвере PDO_SQLSRV|  
|-----------------|------------------------------------------------|-----------------------------------------------------|  
|NULL|varchar(1)|не поддерживается|  
|Boolean|bit|bit|  
|Целочисленный|int|int|  
|Число с плавающей запятой|float(24)|не поддерживается|  
|Строка (длина менее 8000 байт)|varchar (<string length>)|varchar (<string length>)|  
|Строка (длина более 8000 байт)|varchar(max)|varchar(max)|  
|Ресурс|Не поддерживается.|Не поддерживается.|  
|Поток (кодировка: не двоичная)|varchar(max)|varchar(max)|  
|Поток (кодировка: двоичная)|varbinary|varbinary|  
|Array|Не поддерживается.|Не поддерживается.|  
|Объект|Не поддерживается.|Не поддерживается.|  
|DateTime (1)|datetime|Не поддерживается.|  
  
## <a name="see-also"></a>См. также  
[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Преобразование типов данных](../../connect/php/converting-data-types.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)

[Типы PHP](http://php.net/manual/language.types.php)

[Типы данных (Transact-SQL)](https://docs.microsoft.com/en-us/sql/t-sql/data-types/data-types-transact-sql)  
  
