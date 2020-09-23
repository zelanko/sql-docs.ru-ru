---
title: Использование базовых типов данных JDBC
description: Драйвер Microsoft JDBC Driver for SQL Server использует базовые типы данных JDBC для преобразования типов данных SQL Server в формат, который может быть понятен Java.
ms.custom: ''
ms.date: 08/24/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d7044936-5b8c-4def-858c-28a11ef70a97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3c26c3c065ddf415d966c8fd3613e284c3c7a2b6
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806999"
---
# <a name="using-basic-data-types"></a>Использование базовых типов данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] использует базовые типы данных JDBC для преобразования типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в формат языка программирования Java и обратно. Драйвер JDBC обеспечивает поддержку API JDBC 4.0, в том числе типа данных **SQLXML** и типов данных Юникода для национальных символов: **NCHAR**, **NVARCHAR**, **LONGNVARCHAR** и **NCLOB**.  
  
## <a name="data-type-mappings"></a>Сопоставление типов данных

В следующей таблице перечислены все сопоставления по умолчанию между базовыми типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], типами данных JDBC и типами данных языка программирования Java:  
  
| Типы SQL Server   | Типы JDBC (java.sql.Types)                        | Типы языка Java          |
| ------------------ | -------------------------------------------------- | ---------------------------- |
| BIGINT             | bigint                                             | long                         |
| binary             | BINARY                                             | byte[]                       |
| bit                | BIT                                                | Логическое                      |
| char               | CHAR                                               | Строка                       |
| Дата               | DATE                                               | java.sql.Date                |
| datetime<sup>3</sup>          | timestamp                               | java.sql.Timestamp           |
| datetime2          | timestamp                                          | java.sql.Timestamp           |
| datetimeoffset<sup>2</sup> | microsoft.sql.Types.DATETIMEOFFSET         | microsoft.sql.DateTimeOffset |
| Decimal            | DECIMAL                                            | java.math.BigDecimal         |
| FLOAT              | DOUBLE                                             | double                       |
| Изображение              | LONGVARBINARY                                      | byte[]                       |
| INT                | INTEGER                                            | INT                          |
| money              | DECIMAL                                            | java.math.BigDecimal         |
| nchar              | CHAR<br /><br /> NCHAR (Java SE 6.0)               | Строка                       |
| ntext              | LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0) | Строка                       |
| NUMERIC            | NUMERIC                                            | java.math.BigDecimal         |
| nvarchar           | VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)         | Строка                       |
| nvarchar(max)      | VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)         | Строка                       |
| real               | real                                               | FLOAT                        |
| smalldatetime      | timestamp                                          | java.sql.Timestamp           |
| smallint           | SMALLINT                                           | short                        |
| smallmoney         | DECIMAL                                            | java.math.BigDecimal         |
| text               | LONGVARCHAR                                        | Строка                       |
| time               | TIME<sup>1</sup>                                   | java.sql.Time<sup>1</sup>            |
| TIMESTAMP          | BINARY                                             | byte[]                       |
| tinyint            | TINYINT                                            | short                        |
| определяемый пользователем тип                | VARBINARY                                          | byte[]                       |
| UNIQUEIDENTIFIER   | CHAR                                               | Строка                       |
| varbinary          | VARBINARY                                          | byte[]                       |
| varbinary(max)     | VARBINARY                                          | byte[]                       |
| varchar            | VARCHAR                                            | Строка                       |
| varchar(max)       | VARCHAR                                            | Строка                       |
| Xml                | LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0) | Строка<br /><br /> SQLXML    |
| sqlvariant         | SQLVARIANT                                         | Объект                       |
| geometry           | VARBINARY                                          | byte[]                       |
| geography          | VARBINARY                                          | byte[]                       |
  
<sup>1</sup> Чтобы использовать java.sql.Time с типом времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], нужно задать для свойства подключения **sendTimeAsDatetime** значение "false".  
  
<sup>2</sup> Значения **datetimeoffset** можно получить программным образом с помощью класса [DateTimeOffset](reference/datetimeoffset-class.md).  
  
<sup>3</sup> Обратите внимание, что значения java.sql.Timestamp больше нельзя использовать для сравнения значений из столбца datetime, начиная с SQL Server 2016. Это ограничение обусловлено изменением на стороне сервера, которое иначе преобразует datetime в datetime2, в результате чего получаются не равнозначные значения. Чтобы решить эту проблему, можно либо изменить столбцы datetime на datetime2(3), использовать строку вместо java.sql.Timestamp или изменить уровень совместимости базы данных на 120 или ниже.
  
В следующих разделах приводятся примеры использования драйвера JDBC и базовых типов данных. Более подробный пример использования базовых типов данных в приложении Java см. в разделе [Образец базовых типов данных](basic-data-types-sample.md).  
  
## <a name="retrieving-data-as-a-string"></a>Извлечение данных в виде строки

Если вам нужно получить из источника данные, соответствующие каким-либо базовым типам данных JDBC, и просмотреть их в виде строки, или если строго типизированные данные не требуются, вы можете воспользоваться методом [getString](reference/getstring-method-sqlserverresultset.md) класса [SQLServerResultSet](reference/sqlserverresultset-class.md), как показано далее:  
  
[!code[JDBC#UsingBasicDataTypes1](codesnippet/Java/using-basic-data-types_1.java)]  
  
## <a name="retrieving-data-by-data-type"></a>Извлечение данных по типу данных

Если вам нужно получить из источника данные известного типа, воспользуйтесь одним из методов get\<Type> класса SQLServerResultSet, также известных как *методы получения*. С методами get\<Type> можно использовать имя столбца или его индекс:  
  
[!code[JDBC#UsingBasicDataTypes2](codesnippet/Java/using-basic-data-types_2.java)]  
  
> [!NOTE]  
> Применение getUnicodeStream и getBigDecimal в сочетании с методами масштабирования считается устаревшим и не поддерживается драйвером JDBC.

## <a name="updating-data-by-data-type"></a>Обновление данных по типу данных

Если вам нужно обновить значение поля в источнике данных, воспользуйтесь одним из методов update\<Type> класса SQLServerResultSet. В следующем примере для обновления данных в источнике используется метод [updateInt](reference/updateint-method-sqlserverresultset.md) совместно с методом [updateRow](reference/updaterow-method-sqlserverresultset.md):  
  
[!code[JDBC#UsingBasicDataTypes3](codesnippet/Java/using-basic-data-types_3.java)]  
  
> [!NOTE]  
> Драйвер JDBC не может обновить столбец SQL Server, если имя столбца длиннее, чем 127 символов. При попытке обновить столбец, имя которого длиннее 127 символов, возникнет исключение.  
  
## <a name="updating-data-by-parameterized-query"></a>Обновление по параметризированному запросу

Если вам нужно обновить данные в источнике с помощью параметризированного запроса, вы можете задать тип данных для параметров одним из методов set\<Type> класса [SQLServerPreparedStatement](reference/sqlserverpreparedstatement-class.md), также известных как *методы задания*. В следующем примере метод [prepareStatement](reference/preparestatement-method-sqlserverconnection.md) используется для предварительной компиляции параметризированного запроса, затем метод [setString](reference/setstring-method-sqlserverpreparedstatement.md) задает строковое значение параметра, после чего вызывается метод [executeUpdate](reference/executeupdate-method.md).  
  
[!code[JDBC#UsingBasicDataTypes4](codesnippet/Java/using-basic-data-types_4.java)]  
  
Дополнительные сведения о параметризованных запросах см. в [этой статье](using-an-sql-statement-with-parameters.md).  

## <a name="passing-parameters-to-a-stored-procedure"></a>Передача параметров хранимой процедуре

Если вам нужно передать параметры типа хранимой процедуре, вы можете задать параметры по имени или индексу с помощью методов set\<Type> класса [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). В следующем примере метод [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) используется для вызова хранимой процедуры, затем с помощью метода [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md) задается параметр для вызова, после чего вызывается метод [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md).  
  
[!code[JDBC#UsingBasicDataTypes5](codesnippet/Java/using-basic-data-types_5.java)]  
  
> [!NOTE]  
> В данном примере возвращается результирующий набор с результатами запуска хранимой процедуры.

Дополнительные сведения об использовании драйвера JDBC с хранимыми процедурами и входными параметрами см. в [этой статье](using-a-stored-procedure-with-input-parameters.md).  

## <a name="retrieving-parameters-from-a-stored-procedure"></a>Извлечение параметров из хранимой процедуры

Если вам нужно получить параметры обратно из хранимой процедуры, то нужно сначала зарегистрировать параметр OUT по имени или индексу при помощи метода [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) класса SQLServerCallableStatement, а затем после вызова хранимой процедуры назначить возвращаемый параметр OUT надлежащей переменной. В следующем примере сначала используется метод prepareCall для настройки вызова хранимой процедуры, затем — метод registerOutParameter для настройки параметра OUT, затем — метод [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md) для задания параметра вызова, после чего вызывается метод executeQuery. Значение, возвращаемое параметром OUT хранимой процедуры, извлекается с помощью метода [getShort](../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md).  
  
[!code[JDBC#UsingBasicDataTypes6](../../connect/jdbc/codesnippet/Java/using-basic-data-types_6.java)]  
  
> [!NOTE]  
> В дополнение к возвращаемому параметру OUT также можно вернуть результирующий набор с результатами запуска хранимой процедуры.  
  
Дополнительные сведения об использовании драйвера JDBC с хранимыми процедурами и выходными параметрами см. в [этой статье](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md).  

## <a name="see-also"></a>См. также раздел

[Основные сведения о типах данных JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
