---
title: Члены SQLServerPreparedStatement | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2363902f-d4c6-4cd4-a5fc-86079eb9e418
caps.latest.revision: 38
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 275115e8d23c48a564528de57fee14ae19513e00
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32852939"
---
# <a name="sqlserverpreparedstatement-members"></a>Члены SQLServerPreparedStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="methods"></a>Методы  
  
|Название|Описание|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)|Добавляет набор параметров в пакет команд для этого объекта инструкции.|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Отменяет инструкцию SQL, выполняемую в настоящее время данным объектом инструкции.|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md)|Обнуляет текущий список команд SQL для этого [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[clearParameters](../../../connect/jdbc/reference/clearparameters-method-sqlserverpreparedstatement.md)|Немедленно удаляет текущие значения параметров.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Удаляет все предупреждения, выданные для данного объекта инструкции.|  
|[Закрыть](../../../connect/jdbc/reference/close-method-sqlserverpreparedstatement.md)|Освобождает базы данных и ресурсы JDBC этого объекта инструкция немедленно, не дожидаясь их автоматического освобождения.|  
|[execute](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)|Выполняет инструкцию SQL в этом объекте инструкции может быть любой тип инструкции SQL.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverpreparedstatement.md)|Отправляет пакет команд базе данных для выполнения. В случае успешного выполнения всех команд возвращает массив из количества операций обновления, выполненных той или иной командой.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)|Выполняет SQL-запрос в этот объект инструкции и возвращает [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, созданного запросом.|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)|Выполняет инструкцию SQL в этом объекте оператор, который должен быть SQL INSERT, UPDATE, MERGE или DELETE инструкции. или инструкция SQL, которая не возвращает ничего, например инструкция DDL.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объект, который был создан этот объект инструкции.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает направление выборки строк из таблиц базы данных, значение по умолчанию для результирующих наборов, созданных на основе этого объекта инструкции.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает число строк результирующего набора, равное размеру выборки по умолчанию для результирующих наборов объектов, созданных на основе этого объекта инструкции.|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает все автоматически сформированные ключи, созданные в результате выполнения этого объекта инструкции.|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает максимальное число байтов, которые могут возвращаться для значений символьных и двоичных столбцов в [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, созданном этим объектом инструкции.|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает максимальное число строк, [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) может содержаться в объекте, созданном этим объектом инструкции.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverpreparedstatement.md)|Извлекает [класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) , содержащий сведения о столбцах [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект, который будет возвращаться при выполнении данного объекта инструкции.|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Переходит к следующему результату этого объекта инструкции.|  
|[getParameterMetaData](../../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md)|Извлекает количество, типы и свойства параметров для этого объекта инструкции.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает режим буферизации для этого ответов [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает количество секунд [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет ожидать выполнения этого объекта инструкции.|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает текущий результат в виде [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Получает результирующий набор с параллелизмом для [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектов, созданных этим объектом инструкции.|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Получает результирующий набор удержания для [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектов, созданных этим объектом инструкции.|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Получает тип для результирующего набора [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектов, созданных этим объектом инструкции.|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md),) возвращает текущий результат в виде счетчика обновлений.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Извлекает первое предупреждение, сообщаемые вызовы на этот объект инструкции.|  
|[IsClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Указывает, был ли закрыт этот объект инструкции.|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Возвращает значение, показывающее, можно ли добавить инструкцию в предоставляемый пользователем пул инструкций.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)|Указывает, является ли этот объект инструкции оболочкой указанного интерфейса.|  
|[setArray](../../../connect/jdbc/reference/setarray-method-sqlserverpreparedstatement.md)|Задает номер указанного параметра для заданного объекта массива.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlserverpreparedstatement.md)|Задает номер указанного параметра для заданного объекта InputStream.|  
|[setBigDecimal](../../../connect/jdbc/reference/setbigdecimal-method-sqlserverpreparedstatement.md)|Задает номер указанного параметра для заданного объекта BigDecimal.|  
|[setBinaryStream](../../../connect/jdbc/reference/setbinarystream-method-sqlserverpreparedstatement.md)|Устанавливает для указанного параметра указанное значение входного потока.|  
|[setBlob](../../../connect/jdbc/reference/setblob-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанный большой двоичный объект.|  
|[setboolean](../../../connect/jdbc/reference/setboolean-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанное **логическое** значение.|  
|[setByte](../../../connect/jdbc/reference/setbyte-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанное **байтов** значение.|  
|[SetBytes](../../../connect/jdbc/reference/setbytes-method-sqlserverpreparedstatement.md)|Задает указанный параметр для указанного массива байтов.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанный объект модуля чтения.|  
|[setClob](../../../connect/jdbc/reference/setclob-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру для заданного объекта Clob.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Для имени курсора SQL задается значение типа String, которое будет использоваться последующими методами выполнения.|  
|[setDate](../../../connect/jdbc/reference/setdate-method-sqlserverpreparedstatement.md)|Устанавливает для указанного параметра указанное значение даты.|  
|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md)|Задает значение указанного столбца [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) значение.|  
|[setDouble](../../../connect/jdbc/reference/setdouble-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанное **двойные** значение.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задается режим обработки escape-последовательностей.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Определяет указание для драйвера JDBC относительно направления, в котором будут обрабатываться строки результирующего набора.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Определяет указание для драйвера JDBC относительно числа строк, которые должны быть извлечены из базы данных при необходимости в дополнительных строках.|  
|[setFloat](../../../connect/jdbc/reference/setfloat-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанное **float** значение.|  
|[setInt](../../../connect/jdbc/reference/setint-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанное **int** значение.|  
|[setLong](../../../connect/jdbc/reference/setlong-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанное **длинные** значение.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задает ограничение на максимальное число байтов в [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) столбца хранятся символьные или двоичные значения заданного числа байтов.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задает ограничение на максимальное число строк, чтобы любое [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектов могут содержать до указанного числа.|  
|[setNCharacterStream](../../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанный объект модуля чтения.|  
|[setNClob](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру значение заданного объекта.|  
|[setNull](../../../connect/jdbc/reference/setnull-method-sqlserverpreparedstatement.md)|Устанавливает значение NULL для параметра, определяемого по заданному типу.|  
|[setNString](../../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md)|Присваивает указанному параметру указанное **строка** объекта.|  
|[setObject](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)|Устанавливает значение указанного параметра с помощью заданного объекта.|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Запрашивает поддержку пулов или запрет пулов в инструкции. По умолчанию объект SQLServerPreparedStatement поддерживают.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задает количество секунд ожидания драйвер для объекта инструкции для запуска указанного количества секунд.|  
|[setRef](../../../connect/jdbc/reference/setref-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанный объект Ref.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|(Наследуется от [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Задает режим буферизации для этого ответов [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта без учета регистра **полная строка** или **адаптивной**.|  
|[setShort](../../../connect/jdbc/reference/setshort-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанное **короткие** значение.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанное **строка** значение.|  
|[setSQLXML](../../../connect/jdbc/reference/setsqlxml-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру указанное **SQLXML** объекта.|  
|[setTime](../../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)|Устанавливает для указанного параметра указанное значение времени.|  
|[setTimestamp](../../../connect/jdbc/reference/settimestamp-method-sqlserverpreparedstatement.md)|Присваивает указанному параметру заданное значение отметки времени.|  
|[setUnicodeStream](../../../connect/jdbc/reference/setunicodestream-method-sqlserverpreparedstatement.md)|Присваивает указанный номер параметра заданному входному потоку, который будет содержать указанное число байтов.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverpreparedstatement.md)|Устанавливает для указанного параметра указанное значение URL-адреса.|  
|[Извлечение из оболочки](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)|Возвращает объект, реализующий указанный интерфейс для доступа к [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-определенных методов.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerStatement|cancel, clearWarnings, execute, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, isPoolable, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setPoolable, setQueryTimeout|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Statement|cancel, clearWarnings, execute, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setQueryTimeout|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также  
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
