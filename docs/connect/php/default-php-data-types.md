---
title: Типы данных PHP по умолчанию | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: b66c301d-3d20-45b8-a112-225d8f01c0bd
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 432b09a03f9f0d7704ed50de92db64417b624ba8
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307703"
---
# <a name="default-php-data-types"></a>типы данных PHP по умолчанию;
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

При извлечении данных с сервера [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] преобразует данные в тип данных PHP по умолчанию, если пользователь не указал тип данных PHP.  
  
При возврате данных с помощью драйвера PDO_SQLSRV типом данных является int или string.  
  
В оставшейся части этой статьи рассматриваются типы данных по умолчанию при работе с драйвером SQLSRV.  
  
Следующая таблица содержит тип данных SQL Server (тип данных, извлекаемых с сервера), тип данных PHP по умолчанию (тип данных, в который преобразуются данные) и кодировку по умолчанию для потоков и строк. Дополнительные сведения об указании типов данных при извлечении данных с сервера см. в статье [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
|Тип SQL Server|Тип PHP по умолчанию|Кодировка по умолчанию|  
|-------------------|--------------------|--------------------|  
|BIGINT|String|8-битовых символов<sup>1</sup>|  
|BINARY|Поток<sup>2</sup>|Двоичная<sup>3</sup>|  
|bit|Целочисленный|8-битовых символов<sup>1</sup>|  
|char;|String|8-битовых символов<sup>1</sup>|  
|date<sup>4</sup>|DATETIME|Неприменимо|  
|DateTime<sup>4</sup>|DATETIME|Неприменимо|  
|datetime2<sup>4</sup>|DATETIME|Неприменимо|  
|datetimeoffset<sup>4</sup>|DATETIME|Неприменимо|  
|Decimal|String|8-битовых символов<sup>1</sup>|  
|FLOAT|float|8-битовых символов<sup>1</sup>|  
|geography|Поток|Двоичная<sup>3</sup>|  
|geometry|Поток|Двоичная<sup>3</sup>|  
|изображение<sup>5</sup>|Поток<sup>2</sup>|Двоичная<sup>3</sup>|  
|ssNoversion|Целочисленный|8-битовых символов<sup>1</sup>|  
|money|String|8-битовых символов<sup>1</sup>|  
|NCHAR|String|8-битовых символов<sup>1</sup>|  
|NUMERIC|String|8-битовых символов<sup>1</sup>|  
|NVARCHAR|String|8-битовых символов<sup>1</sup>|  
|nvarchar(MAX)|Поток<sup>2</sup>|8-битовых символов<sup>1</sup>|  
|ntext<sup>6</sup>|Поток<sup>2</sup>|8-битовых символов<sup>1</sup>|  
|REAL|float|8-битовых символов<sup>1</sup>|  
|smalldatetime|DATETIME|8-битовых символов<sup>1</sup>|  
|SMALLINT|Целочисленный|8-битовых символов<sup>1</sup>|  
|SMALLMONEY|String|8-битовых символов<sup>1</sup>|  
|sql_variant<sup>7</sup>|String|8-битовых символов<sup>1</sup>|  
|text<sup>8</sup>|Поток<sup>2</sup>|8-битовых символов<sup>1</sup>|  
|time<sup>4</sup>|DATETIME|Неприменимо|  
|TIMESTAMP|String|8-битовых символов<sup>1</sup>|  
|TINYINT|Целочисленный|8-битовых символов<sup>1</sup>|  
|определяемый пользователем тип|Поток<sup>2</sup>|Двоичная<sup>3</sup>|  
|UNIQUEIDENTIFIER|Строка<sup>9</sup>|8-битовых символов<sup>1</sup>|  
|varbinary|Поток<sup>2</sup>|Двоичная<sup>3</sup>|  
|varbinary(MAX)|Поток<sup>2</sup>|Двоичная<sup>3</sup>|  
|varchar|String|8-битовых символов<sup>1</sup>|  
|varchar(MAX)|Поток<sup>2</sup>|8-битовых символов<sup>1</sup>|
|xml|Поток<sup>2</sup>|8-битовых символов<sup>1</sup>|  
  

1.  Данные возвращаются в виде 8-битовых символов, как указано в кодовой странице языкового стандарта Windows, установленного в системе. Любой многобайтовых символов или символов, не соответствующих этой кодовой странице, подставляется символ однобайтовый вопросительный знак (?).  
  
2.  Если [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md) или [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) — используется для получения данных, имеющих тип потока PHP по умолчанию, данные возвращаются в виде строки с кодировкой потока. Например, если двоичный файл SQL Server типа извлекаются с помощью **sqlsrv_fetch_array**, тип — это двоичная строка возвращаемого значения по умолчанию.  
  
3.  Данные возвращаются в виде потока необработанных байтов с сервера без применения кодировки или преобразования.  

4.  Данные типов даты и времени можно извлекать в виде строк. Дополнительные сведения см. в статье [Практическое руководство. Получение типа даты и времени в виде строк с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md).  

5.  Это устаревший тип, соответствующий типу varbinary(max).

6. Это устаревший тип, соответствующий типу nvarchar(max).

7.  в параметрах двунаправленный или выходных данных sql_variant не поддерживается.

8.  Это устаревший тип, соответствующий типу varchar(max).  
  
9.  Идентификаторы UNIQUEIDENTIFIER — это идентификаторы GUID, представленные следующим регулярным выражением:  
  
    [0-9a-fA-F] {8}-[0-9a-fA-F]{4}-[0-9a-fA-f]{4}-[0-9a-fA-f]{4}-[0-9a-fA-F]{12}  
 
 
## <a name="other-new-sql-server-2008-data-types-and-features"></a>Другие новые типы данных и функции SQL Server 2008  
Типы данных, впервые появившиеся в SQL Server 2008 и существующие за пределами столбцов (например, возвращающих табличные значения параметров) не поддерживаются в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. В следующей таблице перечислены поддержке новых функций SQL Server 2008 в PHP.  
  
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
  
## <a name="see-also"></a>См. также  
[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Converting Data Types](../../connect/php/converting-data-types.md)

[Типы PHP](http://php.net/manual/en/language.types.php)

[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
  
