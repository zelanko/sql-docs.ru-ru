---
title: "Элементы SQLServerConnection | Документы Microsoft"
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
ms.assetid: 3115a533-756b-4c78-aee9-4ba7253c85e0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 181df7c774bdf48b87bfb139d4fcaa272ba25a87
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
---
# <a name="sqlserverconnection-members"></a>Элементы SQLServerConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
  
|Название|Описание|  
|----------|-----------------|  
|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|Используется для указания уровня изоляции транзакций моментальных снимков.|  
  
## <a name="inherited-fields"></a>Наследуемые поля  
  
|Класс, из которого наследуется:|Описание|  
|---------------------------|-----------------|  
|java.sql.Connection|TRANSACTION_NONE, TRANSACTION_READ_COMMITTED, TRANSACTION_READ_UNCOMMITTED, TRANSACTION_REPEATABLE_READ, TRANSACTION_SERIALIZABLE|  
  
## <a name="methods"></a>Методы  
  
|Название|Описание|  
|----------|-----------------|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverconnection.md)|Удаляет все предупреждения для этого [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverconnection.md)|Высвобождает базу данных для этой [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта и ресурсы JDBC вместо ожидания их автоматического освобождения.|  
|[closeUnreferencedPreparedStatementHandles](../../../connect/jdbc/reference/closeunreferencedpreparedstatementhandles-method-sqlserverconnection.md)|Заставляет отмены-подготовки запросов для любой необработанных отклоненных подготовленных инструкций для выполнения.| 
|[Фиксация](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md)|Фиксирует все изменения, внесенные с момента предыдущей операции фиксации или отката постоянными и снимает базе данных все блокировки, удерживаемые в настоящее время это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md)|Создает **java.sql.Blob** объекта без данных.|  
|[createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md)|Создает **java.sql.Clob** объекта без данных.|  
|[createNClob](../../../connect/jdbc/reference/createnclob-method-sqlserverconnection.md)|Создает **java.sql.NClob** объекта без данных.|  
|[createStatement](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)|Создает [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объект для отправки инструкций SQL в базу данных.|  
|[createSQLXML](../../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)|Создает **java.sql.SQLXML** объекта без данных.|  
|[getAutoCommit](../../../connect/jdbc/reference/getautocommit-method-sqlserverconnection.md)|Извлекает текущий режим автоматической фиксации для данного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[getCatalog](../../../connect/jdbc/reference/getcatalog-method-sqlserverconnection.md)|Возвращает текущее имя каталога для данного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[Метод getClientConnectionID &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|Возвращает идентификатор соединения для последней попытки соединения, вне зависимости от того, была ли она успешной.|  
|[getClientInfo](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)|Извлекает дополнительные сведения о свойствах данных клиентов, поддерживаемых драйвером JDBC.|  
|[getDisableStatementPooling](../../../connect/jdbc/reference/getdisablestatementpooling-method-sqlserverconnection.md)|Возвращает значение **disableStatementPooling** свойство соединения. Этот параметр определяет, включен пул инструкции или не для этого подключения.|
|[getDiscardedServerPreparedStatementCount](../../../connect/jdbc/reference/getdiscardedserverpreparedstatementcount-method-sqlserverconnection.md)|Возвращает количество ожидающих подготовленной инструкции аннулирующие действия.|
|[getEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection.md)|Возвращает значение **enablePrepareOnFirstPreparedStatementCall** свойство соединения.|
|[getHoldability](../../../connect/jdbc/reference/getholdability-method-sqlserverconnection.md)|Извлекает значение текущего удержания [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты, созданные с помощью этого [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md)|Извлекает [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) объект, содержащий метаданные базы данных, к которому [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) представляет подключение.|  
|[getServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/getserverpreparedstatementdiscardthreshold-method-sqlserverconnection.md)|Возвращает значение **serverPreparedStatementDiscardThreshold** свойство соединения.|  
|[getStatementHandleCacheEntryCount](../../../connect/jdbc/reference/getstatementhandlecacheentrycount-method-sqlserverconnection.md)|Возвращает текущее количество дескрипторов пула подготовленной инструкции.|  
|[getStatementPoolingCacheSize](../../../connect/jdbc/reference/getstatementpoolingcachesize-method-sqlserverconnection.md)|Возвращает размер кэша подготовленной инструкции для этого подключения.|  
|[getTransactionIsolation](../../../connect/jdbc/reference/gettransactionisolation-method-sqlserverconnection.md)|Извлекает текущий уровень изоляции транзакции для данного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[getTypeMap](../../../connect/jdbc/reference/gettypemap-method-sqlserverconnection.md)|Возвращает объект карты, связанный с этим [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md)|Возвращает первое предупреждение, указанное в отчетах вызовов в этом [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverconnection.md)|Указывает, является ли это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объект был закрыт.|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverconnection.md)|Указывает, является ли это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объект находится в режиме только для чтения.|  
|[isStatementPoolingEnabled](../../../connect/jdbc/reference/isstatementpoolingenabled-method-sqlserverconnection.md)|Возвращает пул инструкции включен или не для этого подключения.|  
|[isValid](../../../connect/jdbc/reference/isvalid-method-sqlserverconnection.md)|Указывает, является ли это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта не была закрыта и все еще действителен.|  
|[nativeSQL](../../../connect/jdbc/reference/nativesql-method-sqlserverconnection.md)|Преобразовывает заданную инструкцию SQL в соответствии с грамматикой SQL сервера базы данных.|  
|[prepareCall](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)|Создает [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) объект для вызова хранимых процедур базы данных.|  
|[prepareStatement](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)|Создает [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) объект для отправки параметризованных инструкций SQL в базу данных.|  
|[releaseSavepoint](../../../connect/jdbc/reference/releasesavepoint-method-sqlserverconnection.md)|Удаляет указанный [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) объектов из текущей транзакции.|  
|[Откат](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)|Отменяет все изменения, сделанные в текущей транзакции и освобождает базе данных все блокировки, удерживаемые в настоящее время это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[setAutoCommit](../../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md)|Задает режим автоматической фиксации для данного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) состояние данного объекта.|  
|[setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md)|Задает указанное имя каталога для выбора подпространства этого [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) базы данных объекта в котором будет производиться работа.|  
|[setClientInfo](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)|Задает значение для свойств сведений о клиенте.|  
|[setDisableStatementPooling](../../../connect/jdbc/reference/setdisablestatementpooling-method-sqlserverconnection.md)|Задает значение true или false пулы инструкций.|  
|[setEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/setenableprepareonfirstpreparedstatementcall-method-sqlserverconnection.md)|Указывает новое значение **enablePrepareOnFirstPreparedStatementCall** свойство соединения.|  
|[setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)|Изменяет возможность сохранения из [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты, созданные с помощью этого [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) объект в заданное значение.|  
|[setReadOnly](../../../connect/jdbc/reference/setreadonly-method-sqlserverconnection.md)|Помещает это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объект в режиме только для чтения, как подсказку для драйвера JDBC включить оптимизацию базы данных.|  
|[setSavepoint](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)|Создает в текущей транзакции неименованную точку сохранения и возвращает новый [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) , представляющий его.|  
|[setServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/setserverpreparedstatementdiscardthreshold-method-sqlserverconnection.md)|Задает новое значение **serverPreparedStatementDiscardThreshold** свойство соединения.|  
|[setStatementPoolingCacheSize](../../../connect/jdbc/reference/setstatementpoolingcachesize-method-sqlserverconnection.md)|Задает размер кэша подготовленной инструкции для этого подключения.|  
|[setTransactionIsolation](../../../connect/jdbc/reference/settransactionisolation-method-sqlserverconnection.md)|Пытается изменить уровень изоляции транзакции для данного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) заданный объект.|  
|[setTypeMap](../../../connect/jdbc/reference/settypemap-method-sqlserverconnection.md)|Устанавливает указанный объект TypeMap в качестве сопоставления типов для данного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.lang.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также  
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
