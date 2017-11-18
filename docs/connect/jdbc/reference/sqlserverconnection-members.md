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
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 917a5561dd3de7f9f45434aef88bd2eb98661473
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverconnection-members"></a>Элементы SQLServerConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
  
|Имя|Description|  
|----------|-----------------|  
|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|Используется для указания уровня изоляции транзакций моментальных снимков.|  
  
## <a name="inherited-fields"></a>Наследуемые поля  
  
|Класс, из которого наследуется:|Description|  
|---------------------------|-----------------|  
|java.sql.Connection|TRANSACTION_NONE, TRANSACTION_READ_COMMITTED, TRANSACTION_READ_UNCOMMITTED, TRANSACTION_REPEATABLE_READ, TRANSACTION_SERIALIZABLE|  
  
## <a name="methods"></a>Методы  
  
|Имя|Description|  
|----------|-----------------|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverconnection.md)|Удаляет все предупреждения для этого [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[Закрыть](../../../connect/jdbc/reference/close-method-sqlserverconnection.md)|Высвобождает базу данных для этой [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта и ресурсы JDBC вместо ожидания их автоматического освобождения.|  
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
|[getHoldability](../../../connect/jdbc/reference/getholdability-method-sqlserverconnection.md)|Извлекает значение текущего удержания [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты, созданные с помощью этого [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md)|Извлекает [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) объект, содержащий метаданные базы данных, к которому [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) представляет подключение.|  
|[getTransactionIsolation](../../../connect/jdbc/reference/gettransactionisolation-method-sqlserverconnection.md)|Извлекает текущий уровень изоляции транзакции для данного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[getTypeMap](../../../connect/jdbc/reference/gettypemap-method-sqlserverconnection.md)|Возвращает объект карты, связанный с этим [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md)|Возвращает первое предупреждение, указанное в отчетах вызовов в этом [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverconnection.md)|Указывает, является ли это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объект был закрыт.|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverconnection.md)|Указывает, является ли это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объект находится в режиме только для чтения.|  
|[isValid](../../../connect/jdbc/reference/isvalid-method-sqlserverconnection.md)|Указывает, является ли это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта не была закрыта и все еще действителен.|  
|[nativeSQL](../../../connect/jdbc/reference/nativesql-method-sqlserverconnection.md)|Преобразовывает заданную инструкцию SQL в соответствии с грамматикой SQL сервера базы данных.|  
|[prepareCall](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)|Создает [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) объект для вызова хранимых процедур базы данных.|  
|[prepareStatement](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)|Создает [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) объект для отправки параметризованных инструкций SQL в базу данных.|  
|[releaseSavepoint](../../../connect/jdbc/reference/releasesavepoint-method-sqlserverconnection.md)|Удаляет указанный [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) объектов из текущей транзакции.|  
|[откат](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)|Отменяет все изменения, сделанные в текущей транзакции и освобождает базе данных все блокировки, удерживаемые в настоящее время это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[setAutoCommit](../../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md)|Задает режим автоматической фиксации для данного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) состояние данного объекта.|  
|[setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md)|Задает указанное имя каталога для выбора подпространства этого [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) базы данных объекта в котором будет производиться работа.|  
|[setClientInfo](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)|Задает значение для свойств сведений о клиенте.|  
|[setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)|Изменяет возможность сохранения из [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты, созданные с помощью этого [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) объект в заданное значение.|  
|[setReadOnly](../../../connect/jdbc/reference/setreadonly-method-sqlserverconnection.md)|Помещает это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объект в режиме только для чтения, как подсказку для драйвера JDBC включить оптимизацию базы данных.|  
|[setSavepoint](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)|Создает в текущей транзакции неименованную точку сохранения и возвращает новый [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) , представляющий его.|  
|[setTransactionIsolation](../../../connect/jdbc/reference/settransactionisolation-method-sqlserverconnection.md)|Пытается изменить уровень изоляции транзакции для данного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) заданный объект.|  
|[setTypeMap](../../../connect/jdbc/reference/settypemap-method-sqlserverconnection.md)|Устанавливает указанный объект TypeMap в качестве сопоставления типов для данного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.lang.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

