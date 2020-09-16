---
description: Члены SQLServerPreparedStatement
title: Члены SQLServerPreparedStatement | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2363902f-d4c6-4cd4-a5fc-86079eb9e418
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b5025d8a7387777de1d95861fa6b2d09f436b68
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458276"
---
# <a name="sqlserverpreparedstatement-members"></a>Члены SQLServerPreparedStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены элементы, предоставляемые классом [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="methods"></a>Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)|Добавляет набор параметров к пакету команд для этого объекта инструкции.|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Отменяет инструкцию SQL, выполняемую в настоящее время объектом инструкции.|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md)|Обнуляет текущий список команд SQL для данного объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[clearParameters](../../../connect/jdbc/reference/clearparameters-method-sqlserverpreparedstatement.md)|Немедленно удаляет текущие значения параметров.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Очищает все предупреждения, выданные для данного объекта инструкции.|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverpreparedstatement.md)|Немедленно освобождает ресурсы базы данных и JDBC этого объекта инструкции вместо того, чтобы ожидать их автоматического освобождения.|  
|[execute](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)|Выполняет инструкцию SQL в этом объекте инструкции, который может принадлежать к любому типу инструкции SQL.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverpreparedstatement.md)|Отправляет пакет команд базе данных для выполнения. В случае успешного выполнения всех команд возвращает массив из количества операций обновления, выполненных той или иной командой.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)|Выполняет запрос SQL в этом объекте инструкции и возвращает объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданный этим запросом.|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)|Выполняет инструкцию SQL в этом объекте инструкции. Это должна быть инструкция SQL INSERT, UPDATE, MERGE или DELETE либо инструкция SQL, не возвращающая значения, например инструкция DDL.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md), создавший данный объект инструкции.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает направление выборки строк из таблиц базы данных, заданное по умолчанию для результирующих наборов, созданных на основе этого объекта инструкции.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает число строк результирующего набора, равное размеру выборки по умолчанию для объектов результирующих наборов, созданных на основе этого объекта инструкции.|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает все автоматически сформированные ключи, созданные в результате выполнения этого объекта инструкции.|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает максимальное число байтов, которое может возвращаться для значений символьных и двоичных столбцов в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданном этим объектом инструкции.|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает максимальное количество строк, которое может содержаться в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданном этим объектом инструкции.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverpreparedstatement.md)|Извлекает объект [класса SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md), содержащий сведения о столбцах объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), который возвращается при выполнении этого объекта инструкции.|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Переходит к следующему результату этого объекта Statement.|  
|[getParameterMetaData](../../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md)|Извлекает количество, типы и свойства параметров этого объекта инструкции.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает режим буферизации ответов для этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает время в секундах, в течение которого [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет ожидать выполнения этого объекта инструкции.|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает текущий результат как объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает параллелизм результирующего набора для объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданных этим объектом инструкции.|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает возможность сохранения результирующих наборов для объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданных этим объектом инструкции.|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает тип результирующего набора для объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданных этим объектом инструкции.|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает текущий результат в виде счетчика обновлений.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает первое предупреждение, указанное в отчетах для вызовов этого объекта инструкции.|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Указывает, был ли закрыт этот объект Statement.|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает значение, показывающее, можно ли добавить инструкцию в предоставляемый пользователем пул инструкций.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)|Указывает, является ли этот объект инструкции оболочкой указанного интерфейса.|  
|[setArray](../../../connect/jdbc/reference/setarray-method-sqlserverpreparedstatement.md)|Задает номер назначенного параметра для указанного объекта Array.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlserverpreparedstatement.md)|Задает номер назначенного параметра для указанного объекта InputStream.|  
|[setBigDecimal](../../../connect/jdbc/reference/setbigdecimal-method-sqlserverpreparedstatement.md)|Задает номер назначенного параметра для указанного объекта BigDecimal.|  
|[setBinaryStream](../../../connect/jdbc/reference/setbinarystream-method-sqlserverpreparedstatement.md)|Устанавливает для указанного параметра указанное значение входного потока.|  
|[setBlob](../../../connect/jdbc/reference/setblob-method-sqlserverpreparedstatement.md)|Задает назначенному параметру значение указанного BLOB-объекта.|  
|[setboolean](../../../connect/jdbc/reference/setboolean-method-sqlserverpreparedstatement.md)|Задает назначенному параметру указанное **логическое** значение.|  
|[setByte](../../../connect/jdbc/reference/setbyte-method-sqlserverpreparedstatement.md)|Задает назначенному параметру указанное значение **байта**.|  
|[setBytes](../../../connect/jdbc/reference/setbytes-method-sqlserverpreparedstatement.md)|Задает указанный параметр для указанного массива байтов.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)|Задает указанному параметру заданный объект Reader.|  
|[setClob](../../../connect/jdbc/reference/setclob-method-sqlserverpreparedstatement.md)|Задает назначенному параметру значение указанного CLOB-объекта.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Для имени курсора SQL задается значение типа String, которое будет использоваться последующими методами выполнения.|  
|[SetDate](../../../connect/jdbc/reference/setdate-method-sqlserverpreparedstatement.md)|Устанавливает для указанного параметра указанное значение даты.|  
|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md)|Задает для указанного столбца значение [класса DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md).|  
|[setDouble](../../../connect/jdbc/reference/setdouble-method-sqlserverpreparedstatement.md)|Задает назначенному параметру указанное значение **double**.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задается режим обработки escape-последовательностей.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Определяет указание для драйвера JDBC относительно направления, в котором будут обрабатываться строки результирующего набора.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Определяет указание для драйвера JDBC относительно числа строк, которые должны быть извлечены из базы данных при необходимости в дополнительных строках.|  
|[setFloat](../../../connect/jdbc/reference/setfloat-method-sqlserverpreparedstatement.md)|Задает назначенному параметру указанное значение **float**.|  
|[setInt](../../../connect/jdbc/reference/setint-method-sqlserverpreparedstatement.md)|Задает назначенному параметру указанное значение **int**.|  
|[setLong](../../../connect/jdbc/reference/setlong-method-sqlserverpreparedstatement.md)|Задает назначенному параметру указанное значение **long**.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Устанавливает ограничение количества байтов для максимального размера столбца [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), в котором хранятся символьные или двоичные значения.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Устанавливает равное заданному числу ограничение для максимального количества строк, которое может содержаться в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[setNCharacterStream](../../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md)|Задает указанному параметру заданный объект Reader.|  
|[setNClob](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру значение заданного объекта.|  
|[setNull](../../../connect/jdbc/reference/setnull-method-sqlserverpreparedstatement.md)|Устанавливает значение NULL для параметра, определяемого по заданному типу.|  
|[setNString](../../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md)|Задает назначенному параметру значение указанного объекта **String**.|  
|[setObject](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)|Устанавливает значение указанного параметра с помощью заданного объекта.|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Запрашивает поддержку пулов или запрет пулов в инструкции. По умолчанию создаваемый объект SQLServerPreparedStatement поддерживает включение в пул.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задает количество секунд, в течение которых драйвер будет ожидать выполнения объекта инструкции.|  
|[setRef](../../../connect/jdbc/reference/setref-method-sqlserverpreparedstatement.md)|Задает назначенному параметру значение указанного объекта Ref.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задает режиму буферизации ответов для этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) значение **String full** или **adaptive** без учета регистра.|  
|[setShort](../../../connect/jdbc/reference/setshort-method-sqlserverpreparedstatement.md)|Задает указанному параметру заданное значение **short**.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlserverpreparedstatement.md)|Задает назначенному параметру указанное значение **String**.|  
|[setSQLXML](../../../connect/jdbc/reference/setsqlxml-method-sqlserverpreparedstatement.md)|Задает указанному параметру значение заданного объекта **SQLXML**.|  
|[setTime](../../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)|Устанавливает для указанного параметра указанное значение времени.|  
|[setTimestamp](../../../connect/jdbc/reference/settimestamp-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру заданное значение отметки времени.|  
|[setUnicodeStream](../../../connect/jdbc/reference/setunicodestream-method-sqlserverpreparedstatement.md)|Присваивает указанный номер параметра заданному входному потоку, который будет содержать указанное число байтов.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverpreparedstatement.md)|Устанавливает для указанного параметра указанное значение URL-адреса.|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)|Возвращает объект, реализующий указанный интерфейс для доступа к методам, относящимся к драйверу [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerStatement|cancel, clearWarnings, execute, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, isPoolable, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setPoolable, setQueryTimeout|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Statement|cancel, clearWarnings, execute, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setQueryTimeout|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
