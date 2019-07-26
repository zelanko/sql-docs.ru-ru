---
title: Элементы SQLServerConnection | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3115a533-756b-4c78-aee9-4ba7253c85e0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a3e3ba3d7da52f10b9bd51934b25f44a38a16be0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67971721"
---
# <a name="sqlserverconnection-members"></a>Элементы SQLServerConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены элементы, предоставляемые классом [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
  
|Имя|Описание|  
|----------|-----------------|  
|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|Используется для указания уровня изоляции транзакций моментальных снимков.|  
  
## <a name="inherited-fields"></a>Наследуемые поля  
  
|Класс, из которого наследуется:|Описание|  
|---------------------------|-----------------|  
|java.sql.Connection|TRANSACTION_NONE, TRANSACTION_READ_COMMITTED, TRANSACTION_READ_UNCOMMITTED, TRANSACTION_REPEATABLE_READ, TRANSACTION_SERIALIZABLE|  
  
## <a name="methods"></a>Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverconnection.md)|Удаляет все предупреждения, включенные в отчет для этого объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverconnection.md)|Немедленно освобождает базу данных для этого объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) и ресурсы JDBC вместо ожидания их автоматического освобождения.|  
|[клосеунреференцедпрепаредстатеменсандлес](../../../connect/jdbc/reference/closeunreferencedpreparedstatementhandles-method-sqlserverconnection.md)|Вызывает принудительное выполнение запросов отмены подготовки для всех необработанных отброшенных подготовленных инструкций.| 
|[commit](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md)|Фиксирует все изменения, выполненные после предыдущей операции фиксации или отката, и снимает в базе данных все блокировки, удерживаемые в настоящее время данным объектом [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md)|Создает объект **Java. SQL. BLOB** без каких-либо данных.|  
|[createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md)|Создает объект **Java. SQL. CLOB** без данных.|  
|[createNClob](../../../connect/jdbc/reference/createnclob-method-sqlserverconnection.md)|Создает объект **Java. SQL. NClob** без каких-либо данных.|  
|[createStatement](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)|Создает объект [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) для отправки инструкций SQL в базу данных.|  
|[createSQLXML](../../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)|Создает объект **Java. SQL. SQLXML** без каких-либо данных.|  
|[getAutoCommit](../../../connect/jdbc/reference/getautocommit-method-sqlserverconnection.md)|Извлекает текущий режим автоматической фиксации для данного объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[getCatalog](../../../connect/jdbc/reference/getcatalog-method-sqlserverconnection.md)|Извлекает имя текущего каталога для данного объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[Метод getClientConnectionID (SQLServerConnection)](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|Возвращает идентификатор соединения для последней попытки соединения, вне зависимости от того, была ли она успешной.|  
|[getClientInfo](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)|Извлекает дополнительные сведения о свойствах данных клиентов, поддерживаемых драйвером JDBC.|  
|[getDisableStatementPooling](../../../connect/jdbc/reference/getdisablestatementpooling-method-sqlserverconnection.md)|Возвращает значение свойства соединения **disableStatementPooling** . Этот параметр определяет, включено ли объединение инструкций в пул для данного соединения.|
|[getDiscardedServerPreparedStatementCount](../../../connect/jdbc/reference/getdiscardedserverpreparedstatementcount-method-sqlserverconnection.md)|Возвращает количество невыполненных в настоящее время незавершенных действий подготовки инструкции.|
|[getEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection.md)|Возвращает значение свойства соединения **енаблепрепареонфирстпрепаредстатементкалл** .|
|[getHoldability](../../../connect/jdbc/reference/getholdability-method-sqlserverconnection.md)|Извлекает текущую возможность ожидания объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданных с помощью объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md)|Извлекает объект [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md), который содержит метаданные базы данных, подключение к которой представляет данный объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[getServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/getserverpreparedstatementdiscardthreshold-method-sqlserverconnection.md)|Возвращает значение свойства соединения **серверпрепаредстатементдискардсрешолд** .|  
|[getStatementHandleCacheEntryCount](../../../connect/jdbc/reference/getstatementhandlecacheentrycount-method-sqlserverconnection.md)|Возвращает текущее число готовых дескрипторов инструкций в составе пула.|  
|[getStatementPoolingCacheSize](../../../connect/jdbc/reference/getstatementpoolingcachesize-method-sqlserverconnection.md)|Возвращает размер подготовленного кэша инструкций для этого соединения.|  
|[getTransactionIsolation](../../../connect/jdbc/reference/gettransactionisolation-method-sqlserverconnection.md)|Извлекает текущий уровень изоляции транзакции для данного объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[getTypeMap](../../../connect/jdbc/reference/gettypemap-method-sqlserverconnection.md)|Извлекает объект Map, связанный с данным объектом [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md)|Извлекает первое предупреждение, указанное в отчетах вызовов данного объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverconnection.md)|Указывает, был ли закрыт этот объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverconnection.md)|Указывает, находится ли этот объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) в режиме только для чтения.|  
|[isStatementPoolingEnabled](../../../connect/jdbc/reference/isstatementpoolingenabled-method-sqlserverconnection.md)|Возвращает значение, указывающее, включено ли объединение инструкций в пул для этого соединения.|  
|[isValid](../../../connect/jdbc/reference/isvalid-method-sqlserverconnection.md)|Указывает, верно ли, что этот объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) не закрыт и до сих пор действителен.|  
|[nativeSQL](../../../connect/jdbc/reference/nativesql-method-sqlserverconnection.md)|Преобразовывает заданную инструкцию SQL в соответствии с грамматикой SQL сервера базы данных.|  
|[prepareCall](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)|Создает объект [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) для вызова хранимых процедур базы данных.|  
|[prepareStatement](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)|Создает объект [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) для отправки в базу данных параметризованных инструкций SQL.|  
|[releaseSavepoint](../../../connect/jdbc/reference/releasesavepoint-method-sqlserverconnection.md)|Удаляет заданный объект [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) из текущей транзакции.|  
|[rollback](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)|Отменяет все изменения, сделанные в текущей транзакции, и снимает в базе данных все блокировки, удерживаемые данным объектом [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[setAutoCommit](../../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md)|Устанавливает режим автоматической фиксации для данного объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) в указанное состояние.|  
|[setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md)|Задает указанное имя каталога для выбора подпространства базы данных данного объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md), в котором будет производиться работа.|  
|[setClientInfo](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)|Задает значение для свойств сведений о клиенте.|  
|[setDisableStatementPooling](../../../connect/jdbc/reference/setdisablestatementpooling-method-sqlserverconnection.md)|Задает для группирования инструкций значение true или false.|  
|[setEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/setenableprepareonfirstpreparedstatementcall-method-sqlserverconnection.md)|Указывает новое значение свойства соединения **енаблепрепареонфирстпрепаредстатементкалл** .|  
|[setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)|Изменяет возможность ожидания объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), создаваемых с помощью данного объекта [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md), устанавливая для нее заданное значение.|  
|[setReadOnly](../../../connect/jdbc/reference/setreadonly-method-sqlserverconnection.md)|Переводит данный объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) в режим только для чтения, который является указанием драйверу JDBC включить оптимизацию базы данных.|  
|[setSavepoint](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)|Создает в текущей транзакции безымянную точку сохранения и возвращает новый объект [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md), который ее представляет.|  
|[setServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/setserverpreparedstatementdiscardthreshold-method-sqlserverconnection.md)|Задает новое значение свойства соединения **серверпрепаредстатементдискардсрешолд** .|  
|[setStatementPoolingCacheSize](../../../connect/jdbc/reference/setstatementpoolingcachesize-method-sqlserverconnection.md)|Задает размер подготовленного кэша инструкций для этого соединения.|  
|[setTransactionIsolation](../../../connect/jdbc/reference/settransactionisolation-method-sqlserverconnection.md)|Изменяет текущий уровень изоляции транзакций для данного объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) на заданный.|  
|[setTypeMap](../../../connect/jdbc/reference/settypemap-method-sqlserverconnection.md)|Устанавливает указанный объект TypeMap в качестве сопоставления типов для данного объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.lang.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
