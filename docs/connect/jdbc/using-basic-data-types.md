---
title: Использование базовых типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d7044936-5b8c-4def-858c-28a11ef70a97
author: MightyPen
ms.author: genemi
ms.openlocfilehash: abbd2aa3c277ad36f419de849b02433f17d27403
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026513"
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
| char               | CHAR                                               | String                       |
| Дата               | DATE                                               | java.sql.Date                |
| DATETIME           | timestamp                                          | java.sql.Timestamp           |
| datetime2          | timestamp                                          | java.sql.Timestamp           |
| datetimeoffset (2) | microsoft.sql.Types.DATETIMEOFFSET                 | microsoft.sql.DateTimeOffset |
| Decimal            | DECIMAL                                            | java.math.BigDecimal         |
| FLOAT              | DOUBLE                                             | double                       |
| Изображение              | LONGVARBINARY                                      | byte[]                       |
| INT                | INTEGER                                            | INT                          |
| money              | DECIMAL                                            | java.math.BigDecimal         |
| nchar              | CHAR<br /><br /> NCHAR (Java SE 6.0)               | String                       |
| ntext              | LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0) | String                       |
| NUMERIC            | NUMERIC                                            | java.math.BigDecimal         |
| nvarchar           | VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)         | String                       |
| nvarchar(max)      | VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)         | String                       |
| real               | real                                               | FLOAT                        |
| smalldatetime      | timestamp                                          | java.sql.Timestamp           |
| smallint           | SMALLINT                                           | short                        |
| smallmoney         | DECIMAL                                            | java.math.BigDecimal         |
| text               | LONGVARCHAR                                        | String                       |
| time               | TIME (1)                                           | java.sql.Time (1)            |
| TIMESTAMP          | BINARY                                             | byte[]                       |
| tinyint            | TINYINT                                            | short                        |
| определяемый пользователем тип                | VARBINARY                                          | byte[]                       |
| UNIQUEIDENTIFIER   | CHAR                                               | String                       |
| varbinary          | VARBINARY                                          | byte[]                       |
| varbinary(max)     | VARBINARY                                          | byte[]                       |
| varchar            | VARCHAR                                            | String                       |
| varchar(max)       | VARCHAR                                            | String                       |
| Xml                | LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0) | String<br /><br /> SQLXML    |
| sqlvariant         | SQLVARIANT                                         | Объект                       |
| geometry           | VARBINARY                                          | byte[]                       |
| geography          | VARBINARY                                          | byte[]                       |
  
(1) Чтобы использовать java.sql.Time с типом времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], нужно задать для свойства подключения **sendTimeAsDatetime** значение "false" (ложь).  
  
(2) Значения **datetimeoffset** можно получить программным образом с помощью [класса DateTimeOffset](../../connect/jdbc/reference/datetimeoffset-class.md).  
  
В следующих разделах приводятся примеры использования драйвера JDBC и базовых типов данных. Более подробный пример использования базовых типов данных в приложении Java см. в разделе [Образец базовых типов данных](../../connect/jdbc/basic-data-types-sample.md).  
  
## <a name="retrieving-data-as-a-string"></a>Извлечение данных в виде строки

Если вам нужно получить из источника данные, соответствующие каким-либо базовым типам данных JDBC, и просмотреть их в виде строки, или если строго типизированные данные не требуются, вы можете воспользоваться методом [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) класса [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), как показано далее:  
  
[!code[JDBC#UsingBasicDataTypes1](../../connect/jdbc/codesnippet/Java/using-basic-data-types_1.java)]  
  
## <a name="retrieving-data-by-data-type"></a>Извлечение данных по типу данных

Если вам нужно получить из источника данные известного типа, воспользуйтесь одним из методов get\<Тип> класса SQLServerResultSet, также известных как *методы получения*. С методами get\<Тип> можно использовать имя столбца или его индекс:  
  
[!code[JDBC#UsingBasicDataTypes2](../../connect/jdbc/codesnippet/Java/using-basic-data-types_2.java)]  
  
> [!NOTE]  
> Применение getUnicodeStream и getBigDecimal в сочетании с методами масштабирования считается устаревшим и не поддерживается драйвером JDBC.

## <a name="updating-data-by-data-type"></a>Обновление данных по типу данных

Если вам нужно обновить значение поля в источнике данных, воспользуйтесь одним из методов update\<тип> класса SQLServerResultSet. В следующем примере для обновления данных в источнике используется метод [updateInt](../../connect/jdbc/reference/updateint-method-sqlserverresultset.md) совместно с методом [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md):  
  
[!code[JDBC#UsingBasicDataTypes3](../../connect/jdbc/codesnippet/Java/using-basic-data-types_3.java)]  
  
> [!NOTE]  
> Драйвер JDBC не может обновить столбец SQL Server, если имя столбца длиннее, чем 127 символов. При попытке обновить столбец, имя которого длиннее 127 символов, возникнет исключение.  
  
## <a name="updating-data-by-parameterized-query"></a>Обновление по параметризированному запросу

Если вам нужно обновить данные в источнике с помощью параметризированного запроса, вы можете задать тип данных для параметров одним из методов set\<Тип> класса [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), также известных как *методы задания*. В следующем примере метод [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md) используется для предварительной компиляции параметризированного запроса, затем метод [setString](../../connect/jdbc/reference/setstring-method-sqlserverpreparedstatement.md) задает строковое значение параметра, после чего вызывается метод [executeUpdate](../../connect/jdbc/reference/executeupdate-method.md).  
  
[!code[JDBC#UsingBasicDataTypes4](../../connect/jdbc/codesnippet/Java/using-basic-data-types_4.java)]  
  
Дополнительные сведения о параметризованных запросах см. в [этой статье](../../connect/jdbc/using-an-sql-statement-with-parameters.md).  

## <a name="passing-parameters-to-a-stored-procedure"></a>Передача параметров хранимой процедуре

Если вам нужно передать параметры типа хранимой процедуре, вы можете задать параметры по имени или индексу с помощью методов set\<Тип> класса [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). В следующем примере метод [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) используется для вызова хранимой процедуры, затем с помощью метода [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md) задается параметр для вызова, после чего вызывается метод [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md).  
  
[!code[JDBC#UsingBasicDataTypes5](../../connect/jdbc/codesnippet/Java/using-basic-data-types_5.java)]  
  
> [!NOTE]  
> В данном примере возвращается результирующий набор с результатами запуска хранимой процедуры.

Дополнительные сведения об использовании драйвера JDBC с хранимыми процедурами и входными параметрами см. в [этой статье](../../connect/jdbc/using-a-stored-procedure-with-input-parameters.md).  

## <a name="retrieving-parameters-from-a-stored-procedure"></a>Извлечение параметров из хранимой процедуры

Если вам нужно получить параметры обратно из хранимой процедуры, то нужно сначала зарегистрировать параметр OUT по имени или индексу при помощи метода [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) класса SQLServerCallableStatement, а затем после вызова хранимой процедуры назначить возвращаемый параметр OUT надлежащей переменной. В следующем примере сначала используется метод prepareCall для настройки вызова хранимой процедуры, затем — метод registerOutParameter для настройки параметра OUT, затем — метод [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md) для задания параметра вызова, после чего вызывается метод executeQuery. Значение, возвращаемое параметром OUT хранимой процедуры, извлекается с помощью метода [getShort](../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md).  
  
[!code[JDBC#UsingBasicDataTypes6](../../connect/jdbc/codesnippet/Java/using-basic-data-types_6.java)]  
  
> [!NOTE]  
> В дополнение к возвращаемому параметру OUT также можно вернуть результирующий набор с результатами запуска хранимой процедуры.  
  
Дополнительные сведения об использовании драйвера JDBC с хранимыми процедурами и выходными параметрами см. в [этой статье](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md).  

## <a name="see-also"></a>См. также раздел

[Основные сведения о типах данных JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
