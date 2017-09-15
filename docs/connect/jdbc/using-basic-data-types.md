---
title: "Использование базовых типов данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7044936-5b8c-4def-858c-28a11ef70a97
caps.latest.revision: 73
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e7333b711d828981a93c51b98b7e84fb62a7749b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-basic-data-types"></a>Использование базовых типов данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Использует расширенные типы данных JDBC для преобразования [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типов данных в формат, распознаваемый языком программирования Java и наоборот. Драйвер JDBC обеспечивает поддержку API JDBC 4.0, который включает **SQLXML** тип данных и национальные (Юникод) типы данных, такие как **NCHAR**, **NVARCHAR**, **LONGNVARCHAR**, и **NCLOB**.  
  
## <a name="data-type-mappings"></a>Сопоставление типов данных  
 В следующей таблице перечислены сопоставления по умолчанию между базовыми [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], JDBC и типами данных языка программирования Java:  
  
|Типы SQL Server|Типы JDBC (java.sql.Types)|Типы языка Java|  
|----------------------|-----------------------------------|-------------------------|  
|bigint|bigint|long|  
|binary|BINARY|byte[]|  
|bit|BIT|boolean|  
|char|CHAR|Строковые значения|  
|date|DATE|java.sql.Date|  
|datetime|timestamp|java.sql.Timestamp|  
|datetime2|timestamp|java.sql.Timestamp|  
|datetimeoffset (2)|microsoft.sql.Types.DATETIMEOFFSET|microsoft.sql.DateTimeOffset|  
|decimal|DECIMAL|java.math.BigDecimal|  
|float|DOUBLE|double|  
|image|LONGVARBINARY|byte[]|  
|int|INTEGER|int|  
|money|DECIMAL|java.math.BigDecimal|  
|nchar|CHAR<br /><br /> NCHAR (Java SE 6.0)|Строковые значения|  
|ntext|LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0)|Строковые значения|  
|numeric|NUMERIC|java.math.BigDecimal|  
|nvarchar|VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)|Строковые значения|  
|nvarchar(max)|VARCHAR<br /><br /> NVARCHAR (Java SE 6.0)|Строковые значения|  
|real|REAL|float|  
|smalldatetime|timestamp|java.sql.Timestamp|  
|smallint|SMALLINT|short|  
|smallmoney|DECIMAL|java.math.BigDecimal|  
|text|LONGVARCHAR|Строковые значения|  
|time|TIME (1)|java.sql.Time (1)|  
|timestamp|BINARY|byte[]|  
|tinyint|TINYINT|short|  
|определяемый пользователем тип|VARBINARY|byte[]|  
|uniqueidentifier|CHAR|Строковые значения|  
|varbinary|VARBINARY|byte[]|  
|varbinary(max)|VARBINARY|byte[]|  
|varchar|VARCHAR|Строковые значения|  
|varchar(max)|VARCHAR|Строковые значения|  
|xml|LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0)|Строковые значения<br /><br /> SQLXML|  
  
 (1) чтобы использовать java.sql.Time с временем [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типа, необходимо задать **sendTimeAsDatetime** свойства соединения значение false.  
  
 (2) доступны программным образом значения **datetimeoffset** с [класс DateTimeOffset](../../connect/jdbc/reference/datetimeoffset-class.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Тип данных sqlvariant в настоящее время не поддерживается драйвером JDBC. Если использовался запрос на извлечение данных из таблицы, содержащей столбец типа данных sqlvariant, то возникнет исключение.  
  
 В следующих разделах приводятся примеры использования драйвера JDBC и базовых типов данных. Более подробный пример использования базовых типов данных в приложении Java см. в разделе [базовые типы данных, образцы](../../connect/jdbc/basic-data-types-sample.md).  
  
## <a name="retrieving-data-as-a-string"></a>Извлечение данных в виде строки  
 Если для извлечения данных из источника данных, сопоставленного с любыми типами данных JDBC для просмотра в виде строки, или если строго типизированных данных не требуется, можно использовать [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) класса, как описано ниже:  
  
 [!code[JDBC#UsingBasicDataTypes1](../../connect/jdbc/codesnippet/Java/using-basic-data-types_1.java)]  
  
## <a name="retrieving-data-by-data-type"></a>Извлечение данных по типу данных  
 Если известен тип данных, который извлекается нужно извлечь данные из источника данных, выполните одно из get\<типа > методы класса SQLServerResultSet класса, также известный как *методов считывания*. Можно использовать имя столбца или индекс столбца с get\<типа > методы, как описано ниже:  
  
 [!code[JDBC#UsingBasicDataTypes2](../../connect/jdbc/codesnippet/Java/using-basic-data-types_2.java)]  
  
> [!NOTE]  
>  GetUnicodeStream и getBigDecimal с методами шкалы устарели и не поддерживаются драйвером JDBC.  
  
## <a name="updating-data-by-data-type"></a>Обновление данных по типу данных  
 Если нужно обновить значение поля в источнике данных, воспользуйтесь одним из обновление\<типа > методы класса SQLServerResultSet. В следующем примере [updateInt](../../connect/jdbc/reference/updateint-method-sqlserverresultset.md) метод используется в сочетании с [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) обновление данных в источнике данных:  
  
 [!code[JDBC#UsingBasicDataTypes3](../../connect/jdbc/codesnippet/Java/using-basic-data-types_3.java)]  
  
> [!NOTE]  
>  Драйвер JDBC не может обновить столбец SQL Server, если имя столбца длиннее, чем 127 символов. При попытке обновить столбец, имя которого длиннее 127 символов, возникнет исключение.  
  
## <a name="updating-data-by-parameterized-query"></a>Обновление по параметризированному запросу  
 Если необходимо обновить данные в источнике данных с помощью параметризованного запроса можно задать тип данных параметров с помощью одного набора\<типа > методы [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) класса, также известные как *методов задания*. В следующем примере [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md) метод используется для предварительной компиляции параметризированного запроса, а затем [setString](../../connect/jdbc/reference/setstring-method-sqlserverpreparedstatement.md) метод используется для задания величины строки параметра перед [executeUpdate](../../connect/jdbc/reference/executeupdate-method.md) вызывается метод.  
  
 [!code[JDBC#UsingBasicDataTypes4](../../connect/jdbc/codesnippet/Java/using-basic-data-types_4.java)]  
  
 Дополнительные сведения о параметризованных запросах см. в разделе [с помощью инструкции SQL с параметрами](../../connect/jdbc/using-an-sql-statement-with-parameters.md).  
  
## <a name="passing-parameters-to-a-stored-procedure"></a>Передача параметров хранимой процедуре  
 Если нужно передать введенные параметры хранимой процедуры, можно задать параметры по индексу или по имени с помощью одного набора\<типа > методы [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) класса. В следующем примере [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) метод используется для настройки вызова хранимой процедуры, а затем [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md) метод используется для настройки параметра вызова, после чего [ executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) вызывается метод.  
  
 [!code[JDBC#UsingBasicDataTypes5](../../connect/jdbc/codesnippet/Java/using-basic-data-types_5.java)]  
  
> [!NOTE]  
>  В данном примере возвращается результирующий набор с результатами запуска хранимой процедуры.  
  
 Дополнительные сведения об использовании драйвера JDBC с хранимыми процедурами и входными параметрами см. в разделе [с помощью хранимой процедуры с входными параметрами](../../connect/jdbc/using-a-stored-procedure-with-input-parameters.md).  
  
## <a name="retrieving-parameters-from-a-stored-procedure"></a>Извлечение параметров из хранимой процедуры  
 Если нужно извлечь параметры обратно из хранимой процедуры, необходимо сначала зарегистрировать параметр out по имени или по индексу с помощью [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) метод класса SQLServerCallableStatement, а затем присвоить возвращаемый параметр out надлежащей переменной после инициации вызова хранимой процедуры. В следующем примере используется метод prepareCall для настройки вызова хранимой процедуры, метод registerOutParameter используется для настройки параметра out, а затем [setString](../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md) метод используется для задания параметров для Вызовите до вызова метода executeQuery. Значение, возвращаемое параметром out хранимой процедуры, извлекается с помощью [getShort](../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md) метод.  
  
 [!code[JDBC#UsingBasicDataTypes6](../../connect/jdbc/codesnippet/Java/using-basic-data-types_6.java)]  
  
> [!NOTE]  
>  В дополнение к возвращаемому параметру OUT также можно вернуть результирующий набор с результатами запуска хранимой процедуры.  
  
 Дополнительные сведения об использовании драйвера JDBC с хранимыми процедурами и выходными параметрами см. в разделе [с помощью хранимой процедуры с выходными параметрами](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md).  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
