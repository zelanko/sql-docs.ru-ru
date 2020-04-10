---
title: Члены SQLServerCallableStatement | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apitype: Assembly
ms.assetid: 5ebdc186-e50f-4d14-bbf4-95af5051e4a4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c964e08ab62e67764197cd9f1ebc64e6ad735dee
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920419"
---
# <a name="sqlservercallablestatement-members"></a>Члены SQLServerCallableStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены элементы, предоставляемые классом [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md).  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="inherited-fields"></a>Наследуемые поля  
 Нет.  
  
## <a name="methods"></a>Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Добавляет набор параметров к пакету команд для этого объекта CallableStatement.|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Отменяет инструкцию SQL, выполняемую в настоящее время объектом CallableStatement.|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Обнуляет текущий список команд SQL для данного объекта CallableStatement.|  
|[clearParameters](../../../connect/jdbc/reference/clearparameters-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Немедленно удаляет текущие значения параметров.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Очищает все предупреждения, выданные для данного объекта CallableStatement.|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Немедленно высвобождает ресурсы базы данных и JDBC этого объекта CallableStatement вместо ожидания их автоматического освобождения.|  
|[execute](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Выполняет в этом объекте CallableStatement инструкцию SQL любого типа.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Отправляет пакет команд базе данных для выполнения. В случае успешного выполнения всех команд возвращает массив из количества операций обновления, выполненных той или иной командой.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Выполняет SQL-запрос в этом объекте CallableStatement и возвращает созданный запросом объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Выполняет инструкцию SQL в этом объекте CallableStatement. Это должна быть инструкция SQL INSERT, UPDATE, MERGE или DELETE либо инструкция SQL, не возвращающая значения, например инструкция DDL.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md), создавший данный объект CallableStatement.|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)|Получает значение указанного столбца в виде объекта [DateTimeOffset Class](../../../connect/jdbc/reference/datetimeoffset-class.md).|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает направление выборки строк из таблиц базы данных, заданное по умолчанию для результирующих наборов, созданных на основе этого объекта CallableStatement.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает число строк результирующего набора, равное размеру выборки по умолчанию для объектов результирующих наборов, созданных на основе этого объекта CallableStatement.|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает все автоматически сформированные ключи, созданные в результате выполнения этого объекта CallableStatement.|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает максимальное число байтов, которое может возвращаться для значений символьных и двоичных столбцов в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданном этим объектом CallableStatement.|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает максимальное количество строк, которое может содержаться в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданном этим объектом CallableStatement.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Извлекает объект [класса SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md), содержащий сведения о столбцах объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), который возвращается при выполнении этого объекта CallableStatement.|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Переходит к следующему результату этого объекта SQLServerStatement.|  
|[getParameterMetaData](../../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Извлекает количество, типы и свойства параметров этого объекта CallableStatement.|  
|[getArray](../../../connect/jdbc/reference/getarray-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде объекта Array.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде потока символов **ASCII**.|  
|[getBigDecimal](../../../connect/jdbc/reference/getbigdecimal-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде значения java.math.BigDecimal.|  
|[getBinaryStream](../../../connect/jdbc/reference/getbinarystream-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде двоичного непрерывного потока байтов.|  
|[getBlob](../../../connect/jdbc/reference/getblob-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра большого двоичного объекта JDBC в виде BLOB-объекта на языке программирования Java.|  
|[getboolean](../../../connect/jdbc/reference/getboolean-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде значения **Boolean**.|  
|[getByte](../../../connect/jdbc/reference/getbyte-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде значения **byte**.|  
|[getBytes](../../../connect/jdbc/reference/getbytes-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде массива байтов.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде объекта java.io.Reader.|  
|[getClob](../../../connect/jdbc/reference/getclob-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра большого двоичного объекта JDBC в виде объекта Clob на языке программирования Java.|  
|[getDate](../../../connect/jdbc/reference/getdate-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде объекта java.sql.Date на языке программирования Java.|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)|Получает значение указанного столбца в виде объекта [класса DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md).|  
|[getDouble](../../../connect/jdbc/reference/getdouble-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде **double** на языке программирования Java.|  
|[getFloat](../../../connect/jdbc/reference/getfloat-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде значения **float** на языке программирования Java.|  
|[getInt](../../../connect/jdbc/reference/getint-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде значения **int** на языке программирования Java.|  
|[getLong](../../../connect/jdbc/reference/getlong-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде значения типа **long** на языке программирования Java.|  
|[getNCharacterStream](../../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде объекта Reader.|  
|[getNClob](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра JDBC **NCLOB** в виде объекта **NClob** на языке программирования Java.|  
|[getNString](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра **NCHAR**, **NVARCHAR** или **LONGNVARCHAR** в виде значения String на языке программирования Java.|  
|[getObject](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде объекта на языке программирования Java.|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает время в секундах, в течение которого [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет ожидать выполнения этого объекта CallableStatement.|  
|[getRef](../../../connect/jdbc/reference/getref-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде объекта Ref на языке программирования Java.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает режим буферизации ответов для этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает текущий результат как объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает параллелизм результирующего набора для объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданных этим объектом CallableStatement.|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает возможность ожидания результирующего набора для объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданных этим объектом CallableStatement.|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает тип результирующего набора для объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданных этим объектом CallableStatement.|  
|[getShort](../../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде значения **short** на языке программирования Java.|  
|[getString](../../../connect/jdbc/reference/getstring-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде значения **String** на языке программирования Java.|  
|[getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде объекта java.sql.SQLXML.|  
|[getTime](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде объекта java.sql.Time на языке программирования Java.|  
|[getTimestamp](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде объекта java.sql.Timestamp на языке программирования Java.|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает текущий результат в виде счетчика обновлений.|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlservercallablestatement.md)|Извлекает значение указанного параметра в виде объекта URL на языке программирования Java.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает первое предупреждение, указанное в отчетах для вызовов этого объекта CallableStatement.|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Указывает, был ли закрыт этот объект Statement.|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает значение, показывающее, можно ли добавить инструкцию в предоставляемый пользователем пул инструкций.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)|Указывает, является ли этот объект инструкции оболочкой указанного интерфейса.|  
|[registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)|Регистрирует параметр OUT.|  
|[setArray](../../../connect/jdbc/reference/setarray-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Задает номер назначенного параметра для указанного объекта Array.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-sqlservercallablestatement.md)|Устанавливает для указанного параметра заданное значение входного потока.|  
|[setBigDecimal](../../../connect/jdbc/reference/setbigdecimal-method-sqlservercallablestatement.md)|Задает номер назначенного параметра для указанного объекта BigDecimal.|  
|[setBinaryStream](../../../connect/jdbc/reference/setbinarystream-sqlservercallablestatement.md)|Устанавливает для указанного параметра указанное значение входного потока.|  
|[setBlob](../../../connect/jdbc/reference/setblob-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Задает указанный параметр для заданного BLOB-объекта.|  
|[setboolean](../../../connect/jdbc/reference/setboolean-method-sqlservercallablestatement.md)|Задает указанному параметру заданное значение **Boolean**.|  
|[setByte](../../../connect/jdbc/reference/setbyte-method-sqlservercallablestatement.md)|Задает указанному параметру заданное значение **byte**.|  
|[setBytes](../../../connect/jdbc/reference/setbytes-method-sqlservercallablestatement.md)|Присваивает указанному параметру заданный массив значений **byte**.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservercallablestatement.md)|Задает указанный параметр для заданного объекта Reader.|  
|[setClob](../../../connect/jdbc/reference/setclob-method-sqlservercallablestatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Присваивает указанному параметру значение заданного объекта.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Присваивает имени курсора SQL значение заданной строки. Это значение будет использоваться при дальнейших вызовах метода execute.|  
|[SetDate](../../../connect/jdbc/reference/setdate-method-sqlservercallablestatement.md)|Присваивает указанному параметру заданное значение даты.|  
|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md)|Задает для указанного столбца значение [класса DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md).|  
|[setDouble](../../../connect/jdbc/reference/setdouble-method-sqlservercallablestatement.md)|Задает указанному параметру заданное значение **double**.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задается режим обработки escape-последовательностей.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Определяет указание для драйвера JDBC относительно направления, в котором будут обрабатываться строки результирующего набора.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Определяет указание для драйвера JDBC относительно числа строк, которые должны быть извлечены из базы данных при необходимости в дополнительных строках.|  
|[setFloat](../../../connect/jdbc/reference/setfloat-method-sqlservercallablestatement.md)|Задает назначенному параметру указанное значение **float**.|  
|[setInt](../../../connect/jdbc/reference/setint-method-sqlservercallablestatement.md)|Задает назначенному параметру указанное значение **int**.|  
|[setLong](../../../connect/jdbc/reference/setlong-method-sqlservercallablestatement.md)|Задает назначенному параметру указанное значение **long**.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Устанавливает заданное количество байтов в качестве ограничения на максимальное число байтов для столбца [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), в котором хранятся символьные или двоичные значения.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Устанавливает равное заданному числу ограничение для максимального количества строк, которое может содержаться в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[setNCharacterStream](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)|Задает указанному параметру заданный объект Reader.|  
|[setNClob](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)|Присваивает указанному параметру значение заданного объекта.|  
|[setNString](../../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md)|Задает назначенному параметру значение указанного объекта String.|  
|[setNull](../../../connect/jdbc/reference/setnull-method-sqlservercallablestatement.md)|Устанавливает значение NULL для параметра, определяемого по заданному типу.|  
|[setObject](../../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)|Устанавливает значение указанного параметра с помощью заданного объекта.|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Запрашивает поддержку пулов или запрет пулов в инструкции. По умолчанию создаваемый объект SQLServerCallableStatement поддерживает включение в пул.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задает указанное количество секунд, в течение которых драйвер будет ожидать выполнения объекта CallableStatement.|  
|[setRef](../../../connect/jdbc/reference/setref-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Задает назначенному параметру значение указанного объекта Ref.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задает режиму буферизации ответов для этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) значение **String full** или **adaptive** без учета регистра.|  
|[setShort](../../../connect/jdbc/reference/setshort-method-sqlservercallablestatement.md)|Задает указанному параметру заданное значение **short**.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md)|Задает назначенному параметру заданное значение Java **String**.|  
|[setSQLXML](../../../connect/jdbc/reference/setsqlxml-method-sqlservercallablestatement.md)|Задает указанному параметру значение заданного объекта **SQLXML**.|  
|[setTime](../../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)|Устанавливает для указанного параметра указанное значение времени.|  
|[setTimestamp](../../../connect/jdbc/reference/settimestamp-method-sqlservercallablestatement.md)|Присваивает указанному параметру заданное значение отметки времени.|  
|[setUnicodeStream](../../../connect/jdbc/reference/setunicodestream-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Присваивает указанный номер параметра заданному входному потоку, который будет содержать указанное число байтов.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlservercallablestatement.md)|Устанавливает для указанного параметра указанное значение URL-адреса.|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)|Возвращает объект, реализующий указанный интерфейс для доступа к методам, относящимся к драйверу [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].|  
|[wasNull](../../../connect/jdbc/reference/wasnull-method-sqlservercallablestatement.md)|Получает значение, определяющее, имел ли последний считанный параметр OUT значение SQL NULL.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPreparedStatement|addBatch, clearBatch, clearParameters, close, execute, executeBatch, executeQuery, executeUpdate, getMetaData, getParameterMetaData, setArray, setAsciiStream, setBigDecimal, setBinaryStream, setBlob, setboolean, setByte, setBytes, setCharacterStream, setClob, setDate, setDouble, setFloat, setInt, setLong, setNull, setObject, setRef, setShort, setString, setTime, setTimestamp, setUnicodeStream, setURL|  
|com.microsoft.sqlserver.jdbc.SQLServerStatement|cancel, clearWarnings, execute, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, isPoolable, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setPoolable, setQueryTimeout|  
|class java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait,|  
|java.sql.PreparedStatement|addBatch, clearParameters, execute, executeQuery, executeUpdate, getMetaData, getParameterMetaData, getSQLXML, setArray, setAsciiStream, setBigDecimal, setBinaryStream, setBlob, setboolean, setByte, setBytes, setCharacterStream, setClob, setDate, setDate, setDouble, setFloat, setInt, setLong, setNull, setObject, setRef, setShort, setString, setSQLXML, setTime, setTimestamp, setUnicodeStream, setURL|  
|java.sql.Statement|addBatch, cancel, clearBatch, clearWarnings, close, execute, executeBatch, executeQuery, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setQueryTimeout|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
