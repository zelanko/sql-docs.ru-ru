---
title: "Члены SQLServerCallableStatement | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apitype: Assembly
ms.assetid: 5ebdc186-e50f-4d14-bbf4-95af5051e4a4
caps.latest.revision: 50
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 430675118dcccfbeb93c33c936b674daee8403c9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlservercallablestatement-members"></a>Члены SQLServerCallableStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="inherited-fields"></a>Наследуемые поля  
 Нет.  
  
## <a name="methods"></a>Методы  
  
|Имя|Description|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Добавляет набор параметров в пакет команд для данного объекта CallableStatement.|  
|[Отмена](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Отменяет инструкцию SQL, выполняемую в данный момент этот объект CallableStatement.|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Очищает текущий список команд SQL для данного объекта CallableStatement.|  
|[clearParameters](../../../connect/jdbc/reference/clearparameters-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Немедленно удаляет текущие значения параметров.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Удаляет все предупреждения, выданные для данного объекта CallableStatement.|  
|[Закрыть](../../../connect/jdbc/reference/close-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Освобождает базы данных и ресурсы JDBC этого объекта CallableStatement немедленно, не дожидаясь их автоматического освобождения.|  
|[выполнение](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Выполняет инструкцию SQL в этом объекте CallableStatement может быть любой тип инструкции SQL.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Отправляет пакет команд базе данных для выполнения. В случае успешного выполнения всех команд возвращает массив из количества операций обновления, выполненных той или иной командой.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Выполняет SQL-запрос в этом объекте CallableStatement и возвращает [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, созданного запросом.|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Выполняет инструкцию SQL в этом объекте CallableStatement, который должен быть SQL INSERT, UPDATE, MERGE или DELETE инструкции. или инструкция SQL, которая не возвращает ничего, например инструкция DDL.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объект, который был создан этот объект CallableStatement.|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)|Получает значение указанного столбца в виде [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) объекта.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает направление выборки строк из таблиц базы данных, значение по умолчанию для результирующих наборов, созданных на основе этого объекта CallableStatement.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает число строк результирующего набора, равное размеру выборки по умолчанию для результирующих наборов объектов, созданных на основе этого объекта CallableStatement.|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает все автоматически сформированные ключи, созданные в результате выполнения этого объекта CallableStatement.|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает максимальное число байтов, которые могут возвращаться для значений символьных и двоичных столбцов в [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, созданном этим объектом CallableStatement.|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает максимальное число строк, [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) может содержаться в объекте, созданном этим объектом CallableStatement.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Извлекает [класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) , содержащий сведения о столбцах [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект, который будет возвращен при запуске данного объекта CallableStatement.|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Переходит к следующему результату этого объекта CallableStatement.|  
|[getParameterMetaData](../../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Извлекает количество, типы и свойства параметров для этого объекта CallableStatement.|  
|[getArray](../../../connect/jdbc/reference/getarray-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде объекта Array.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде потока из **ASCII** символов.|  
|[getBigDecimal](../../../connect/jdbc/reference/getbigdecimal-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде значения java.math.BigDecimal.|  
|[getBinaryStream](../../../connect/jdbc/reference/getbinarystream-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде двоичного непрерывного потока байтов.|  
|[getBlob](../../../connect/jdbc/reference/getblob-method-sqlservercallablestatement.md)|Получает значение указанного параметра JDBC Blob в виде большого двоичного объекта на языке программирования Java.|  
|[getboolean](../../../connect/jdbc/reference/getboolean-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде **логическое** значение.|  
|[getByte](../../../connect/jdbc/reference/getbyte-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде **байтов** значение.|  
|[метод getBytes](../../../connect/jdbc/reference/getbytes-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде массива байтов.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде объекта java.io.Reader.|  
|[getClob](../../../connect/jdbc/reference/getclob-method-sqlservercallablestatement.md)|Получает значение указанного параметра JDBC Blob в виде объекта Clob в языке программирования Java.|  
|[функция getDate](../../../connect/jdbc/reference/getdate-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде объекта java.sql.Date на языке программирования Java.|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)|Получает значение указанного столбца в виде[класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) объекта.|  
|[getDouble](../../../connect/jdbc/reference/getdouble-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде **двойные** языке программирования Java.|  
|[getFloat](../../../connect/jdbc/reference/getfloat-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде **float** языке программирования Java.|  
|[getInt](../../../connect/jdbc/reference/getint-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде **int** языке программирования Java.|  
|[getLong](../../../connect/jdbc/reference/getlong-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде **длинные** языке программирования Java.|  
|[getNCharacterStream](../../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде объекта модуля чтения.|  
|[getNClob](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)|Получает значение указанного JDBC **NCLOB** параметр как **NClob** объекта на языке программирования Java.|  
|[getNString](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)|Извлекает значение указанного **NCHAR**, **NVARCHAR** или **LONGNVARCHAR** параметра в виде строки на Java языка программирования.|  
|[функция getObject](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде объекта на языке программирования Java.|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает количество секунд [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет ожидать выполнения этого объекта CallableStatement.|  
|[getRef](../../../connect/jdbc/reference/getref-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде ссылки объекта на языке программирования Java.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает режим буферизации для этого ответов [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает текущий результат в виде [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Получает результирующий набор с параллелизмом для [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектов, созданных этим объектом CallableStatement.|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Получает результирующий набор удержания для [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектов, созданных этим объектом CallableStatement.|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Получает тип для результирующего набора [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектов, созданных этим объектом CallableStatement.|  
|[getShort](../../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде **короткие** языке программирования Java.|  
|[getString](../../../connect/jdbc/reference/getstring-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде **строка** языке программирования Java.|  
|[getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде объекта java.sql.SQLXML.|  
|[getTime](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде объекта java.sql.Time на языке программирования Java.|  
|[getTimestamp](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)|Возвращает значение указанного параметра в виде объекта java.sql.Timestamp на языке программирования Java.|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает текущий результат в виде счетчика обновлений.|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlservercallablestatement.md)|Получает значение указанного параметра в виде URL-адрес объекта на языке программирования Java.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает первое предупреждение, полученных от вызовов в этом объекте CallableStatement.|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Указывает, был ли закрыт этот объект инструкции.|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает значение, показывающее, можно ли добавить инструкцию в предоставляемый пользователем пул инструкций.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)|Указывает, является ли этот объект инструкции оболочкой указанного интерфейса.|  
|[registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)|Регистрирует параметр OUT.|  
|[setArray](../../../connect/jdbc/reference/setarray-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Задает номер указанного параметра для заданного объекта массива.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-sqlservercallablestatement.md)|Устанавливает для указанного параметра заданное значение входного потока.|  
|[setBigDecimal](../../../connect/jdbc/reference/setbigdecimal-method-sqlservercallablestatement.md)|Задает номер указанного параметра для заданного объекта BigDecimal.|  
|[setBinaryStream](../../../connect/jdbc/reference/setbinarystream-sqlservercallablestatement.md)|Устанавливает для указанного параметра указанное значение входного потока.|  
|[setBlob](../../../connect/jdbc/reference/setblob-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Присваивает указанному параметру для заданного объекта BLOB-объектов.|  
|[setboolean](../../../connect/jdbc/reference/setboolean-method-sqlservercallablestatement.md)|Устанавливает указанный параметр заданного **логическое** значение.|  
|[setByte](../../../connect/jdbc/reference/setbyte-method-sqlservercallablestatement.md)|Устанавливает указанный параметр заданного **байтов** значение.|  
|[setBytes](../../../connect/jdbc/reference/setbytes-method-sqlservercallablestatement.md)|Присваивает указанному параметру заданный массив **байтов** значения.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservercallablestatement.md)|Присваивает указанному параметру для заданного объекта модуля чтения.|  
|[setClob](../../../connect/jdbc/reference/setclob-method-sqlservercallablestatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Присваивает указанному параметру значение заданного объекта.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Присваивает имени курсора SQL значение заданной строки. Это значение будет использоваться при дальнейших вызовах метода execute.|  
|[setDate](../../../connect/jdbc/reference/setdate-method-sqlservercallablestatement.md)|Присваивает указанному параметру заданное значение даты.|  
|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md)|Задает значение указанного столбца [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) значение.|  
|[setDouble](../../../connect/jdbc/reference/setdouble-method-sqlservercallablestatement.md)|Устанавливает указанный параметр заданного **двойные** значение.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задается режим обработки escape-последовательностей.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Определяет указание для драйвера JDBC относительно направления, в котором будут обрабатываться строки результирующего набора.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Определяет указание для драйвера JDBC относительно числа строк, которые должны быть извлечены из базы данных при необходимости в дополнительных строках.|  
|[setFloat](../../../connect/jdbc/reference/setfloat-method-sqlservercallablestatement.md)|Присваивает указанному параметру указанное **float** значение.|  
|[setInt](../../../connect/jdbc/reference/setint-method-sqlservercallablestatement.md)|Присваивает указанному параметру указанное **int** значение.|  
|[setLong](../../../connect/jdbc/reference/setlong-method-sqlservercallablestatement.md)|Присваивает указанному параметру указанное **длинные** значение.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задает ограничение на максимальное число байтов в [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) столбца хранятся символьные или двоичные значения указанное число байтов.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задает ограничение на максимальное число строк, чтобы любое [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) может содержать объект указанному числу.|  
|[setNCharacterStream](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)|Присваивает указанному параметру указанный объект модуля чтения.|  
|[setNClob](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)|Присваивает указанному параметру значение заданного объекта.|  
|[setNString](../../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md)|Присваивает указанному параметру для указанного объекта String.|  
|[setNull](../../../connect/jdbc/reference/setnull-method-sqlservercallablestatement.md)|Устанавливает значение NULL для параметра, определяемого по заданному типу.|  
|[setObject](../../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)|Устанавливает значение указанного параметра с помощью заданного объекта.|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Запрашивает поддержку пулов или запрет пулов в инструкции. По умолчанию объект SQLServerCallableStatement поддерживают.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задает количество секунд, в которых драйвер будет ожидать выполнения указанного количества секунд объекта CallableStatement.|  
|[setRef](../../../connect/jdbc/reference/setref-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Присваивает указанному параметру указанный объект Ref.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задает режим буферизации для этого ответов [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта без учета регистра **полная строка** или **адаптивной**.|  
|[setShort](../../../connect/jdbc/reference/setshort-method-sqlservercallablestatement.md)|Присваивает указанному параметру указанное **короткие** значение.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md)|Присваивает указанному параметру указанный Java **строка** значение.|  
|[setSQLXML](../../../connect/jdbc/reference/setsqlxml-method-sqlservercallablestatement.md)|Присваивает указанному параметру указанное **SQLXML** объекта.|  
|[setTime](../../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)|Устанавливает для указанного параметра указанное значение времени.|  
|[setTimestamp](../../../connect/jdbc/reference/settimestamp-method-sqlservercallablestatement.md)|Присваивает указанному параметру заданное значение отметки времени.|  
|[setUnicodeStream](../../../connect/jdbc/reference/setunicodestream-method-sqlserverpreparedstatement.md)|(Наследуется от [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Присваивает указанный номер параметра заданному входному потоку, который будет содержать указанное число байтов.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlservercallablestatement.md)|Устанавливает для указанного параметра указанное значение URL-адреса.|  
|[Извлечение из оболочки](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)|Возвращает объект, реализующий указанный интерфейс для доступа к [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-определенных методов.|  
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
  
  

