---
title: "Типы данных PHP по умолчанию | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: b66c301d-3d20-45b8-a112-225d8f01c0bd
caps.latest.revision: "40"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ff008fdf5cd27300da5912c5347f8c7089bdf53
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="default-php-data-types"></a>типы данных PHP по умолчанию;
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

При извлечении данных с сервера [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] преобразует данные в тип данных PHP по умолчанию, если пользователь не указал тип данных PHP.  
  
При возврате данных с помощью драйвера PDO_SQLSRV типом данных является int или string.  
  
В оставшейся части этой статьи рассматриваются типы данных по умолчанию при работе с драйвером SQLSRV.  
  
Следующая таблица содержит тип данных SQL Server (тип данных, извлекаемых с сервера), тип данных PHP по умолчанию (тип данных, в который преобразуются данные) и кодировку по умолчанию для потоков и строк. Дополнительные сведения об указании типов данных при извлечении данных с сервера см. в статье [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
|Тип SQL Server|Тип PHP по умолчанию|Кодировка по умолчанию|  
|-------------------|--------------------|--------------------|  
|bigint|Строковые значения|8-битовых символов<sup>1</sup>|  
|binary|Поток<sup>2</sup>|Двоичная<sup>3</sup>|  
|bit|Целочисленный|8-битовых символов<sup>1</sup>|  
|char|Строковые значения|8-битовых символов<sup>1</sup>|  
|date<sup>4</sup>|DateTime|Неприменимо|  
|DateTime<sup>4</sup>|DateTime|Неприменимо|  
|datetime2<sup>4</sup>|DateTime|Неприменимо|  
|datetimeoffset<sup>4</sup>|DateTime|Неприменимо|  
|decimal|Строковые значения|8-битовых символов<sup>1</sup>|  
|float|Число с плавающей запятой|8-битовых символов<sup>1</sup>|  
|geography|Поток|Двоичная<sup>3</sup>|  
|geometry|Поток|Двоичная<sup>3</sup>|  
|изображение<sup>5</sup>|Поток<sup>2</sup>|Двоичная<sup>3</sup>|  
|int|Целочисленный|8-битовых символов<sup>1</sup>|  
|money|Строковые значения|8-битовых символов<sup>1</sup>|  
|nchar|Строковые значения|8-битовых символов<sup>1</sup>|  
|numeric|Строковые значения|8-битовых символов<sup>1</sup>|  
|nvarchar|Строковые значения|8-битовых символов<sup>1</sup>|  
|nvarchar(MAX)|Поток<sup>2</sup>|8-битовых символов<sup>1</sup>|  
|ntext<sup>6</sup>|Поток<sup>2</sup>|8-битовых символов<sup>1</sup>|  
|real|Число с плавающей запятой|8-битовых символов<sup>1</sup>|  
|smalldatetime|DateTime|8-битовых символов<sup>1</sup>|  
|smallint|Целочисленный|8-битовых символов<sup>1</sup>|  
|smallmoney|Строковые значения|8-битовых символов<sup>1</sup>|  
|sql_variant<sup>7</sup>|Строковые значения|8-битовых символов<sup>1</sup>|  
|текст<sup>8</sup>|Поток<sup>2</sup>|8-битовых символов<sup>1</sup>|  
|time<sup>4</sup>|DateTime|Неприменимо|  
|timestamp|Строковые значения|8-битовых символов<sup>1</sup>|  
|tinyint|Целочисленный|8-битовых символов<sup>1</sup>|  
|определяемый пользователем тип|Поток<sup>2</sup>|Двоичная<sup>3</sup>|  
|uniqueidentifier|Строка<sup>9</sup>|8-битовых символов<sup>1</sup>|  
|varbinary|Поток<sup>2</sup>|Двоичная<sup>3</sup>|  
|varbinary(MAX)|Поток<sup>2</sup>|Двоичная<sup>3</sup>|  
|varchar|Строковые значения|8-битовых символов<sup>1</sup>|  
|varchar(MAX)|Поток<sup>2</sup>|8-битовых символов<sup>1</sup>|
|xml|Поток<sup>2</sup>|8-битовых символов<sup>1</sup>|  
  

1.  Данные возвращаются в виде 8-битовых символов, как указано в кодовой странице языкового стандарта Windows, установленного в системе. Для всех многобайтовых символов или символов, не соответствующих этой кодовой странице, подставляется однобайтовый символ вопросительного знака (?).  
  
2.  Если для извлечения данных, имеющих тип потока PHP по умолчанию, используется [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md) или [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) , данные возвращаются в виде строки с кодировкой потока. Например, если данные двоичного типа SQL Server извлекаются с помощью **sqlsrv_fetch_array**, типом возвращаемого значения по умолчанию будет двоичная строка.  
  
3.  Данные возвращаются в виде потока необработанных байтов с сервера без применения кодировки или преобразования.  

4.  Данные типов даты и времени можно извлекать в виде строк. Дополнительные сведения см. в статье [Практическое руководство. Получение типа даты и времени в виде строк с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md).  

5.  Это устаревший тип, соответствующий типу varbinary(max).

6. Это устаревший тип, соответствующий типу nvarchar(max).

7.  в параметрах двунаправленный или выходных данных sql_variant не поддерживается.

8.  Это устаревший тип, соответствующий типу varchar(max).  
  
9.  Идентификаторы UNIQUEIDENTIFIER — это идентификаторы GUID, представленные следующим регулярным выражением:  
  
    [0-9a-fA-F]{8}-[0-9a-fA-F]{4}-[0-9a-fA-f]{4}-[0-9a-fA-f]{4}-[0-9a-fA-F]{12}  
 
 
## <a name="other-new-sql-server-2008-data-types-and-features"></a>Другие новые типы данных и функции SQL Server 2008  
Типы данных, впервые появившиеся в SQL Server 2008 и существующие за пределами столбцов (например, возвращающих табличные значения параметров) не поддерживаются в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Следующая таблица содержит сводку о поддержке новых функций SQL Server 2008 в PHP.  
  
|Компонент|Поддержка PHP|  
|-----------|---------------|  
|Возвращающий табличное значение параметр|Нет|  
|Разреженные столбцы|Частичный|  
|Сжатие NULL-битов|Да|  
|Определяемые пользователем типы данных больших значений CLR (UDT)|Да|  
|Имя субъекта-службы|Нет|  
|MERGE|Да|  
|FILESTREAM|Частичный|  
  
Частичная поддержка типа означает, что вы не можете программно запросить тип столбца.  
  
## <a name="see-also"></a>См. также:  
[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Converting Data Types](../../connect/php/converting-data-types.md)  
[Типы PHP](http://go.microsoft.com/fwlink/?LinkId=109071)  
[Типы данных (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=109068)  
[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
  
