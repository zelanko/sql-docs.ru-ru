---
title: "Элементы SQLServerConnectionPoolDataSource | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dac0337e-8088-488c-a25a-801a2190f6ca
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: da18ece75049aa2681379f265e9812159017d722
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverconnectionpooldatasource-members"></a>Элементы SQLServerConnectionPoolDataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
  
|Имя|Description|  
|----------|-----------------|  
|[(SQLServerConnectionPoolDataSource)](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-constructor.md)|Инициализирует новый экземпляр [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md) класса.|  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
 Нет.  
  
## <a name="methods"></a>Методы  
  
|Имя|Description|  
|----------|-----------------|  
|[getApplicationIntent](../../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает значение **applicationIntent** свойство соединения.|  
|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает имя приложения.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) пытается установить соединение с источником данных, который представляет этот объект источника данных.|  
|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает имя базы данных.|  
|[getDescription](../../../connect/jdbc/reference/getdescription-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает описание источника данных.|  
|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает имя сервера отработки отказа, который используется в конфигурации зеркального отображения базы данных.|  
|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] имя экземпляра.|  
|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает **логическое** значение, указывающее, включено ли свойство lastUpdateCount.|  
|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает **int** значение, указывающее число миллисекунд, базы данных будет ожидать до появления сообщения о времени ожидания блокировки.|  
|[getLoginTimeout](../../../connect/jdbc/reference/getlogintimeout-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает количество секунд, этот объект источника данных будет ожидать при попытке установить соединение.|  
|[getLogWriter](../../../connect/jdbc/reference/getlogwriter-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает символьный выходной поток, используемый для всех сообщений ведения журнала и трассировки.|  
|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает значение **multiSubnetFailover** свойство соединения.|  
|[getPooledConnection](../../../connect/jdbc/reference/getpooledconnection-method-sqlserverconnectionpooldatasource.md)|Устанавливает физическое соединение с базой данных, которое будет использоваться в пулах соединений.|  
|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает текущий номер порта, используемый для взаимодействия с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[getReference](../../../connect/jdbc/reference/getreference-method-sqlserverconnectionpooldatasource.md)|Возвращает ссылку на этот объект источника данных.|  
|[метод getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает тип курсора по умолчанию, который используется для всех результирующих наборов, созданных с помощью этого объекта источника данных.|  
|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает **логическое** значение, указывающее, включена ли отправка параметров на сервер в Юникоде.|  
|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает имя компьютера, на котором выполняется [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает URL-адрес, используемый для подключения к источнику данных.|  
|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает имя пользователя, который используется для подключения к источнику данных.|  
|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает имя клиента, имя компьютера, который используется для подключения к источнику данных.|  
|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) возвращает **логическое** значение, указывающее, включено ли преобразование состояний SQL в состояния, соответствующие стандарту xopen.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverconnectionpooldatasource.md)|Указывает, является ли этот объект оболочкой указанного интерфейса.|  
|[setApplicationIntent](../../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает значение **applicationIntent** свойство соединения.|  
|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает имя приложения.|  
|[setAuthenticationSceme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) указывает тип встроенной безопасности приложения для использования.|  
|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает имя базы данных для подключения к.|  
|[Описание](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает описание источника данных.|  
|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает имя сервера отработки отказа, который используется в конфигурации зеркального отображения базы данных.|  
|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) наборы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] имя экземпляра.|  
|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) наборы **логическое** значение, указывающее, включено ли свойство integratedSecurity.|  
|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) наборы **логическое** значение, указывающее, включено ли свойство lastUpdateCount.|  
|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) наборы **int** значение, указывающее, сколько миллисекунд ждать, пока база данных сообщает об истечении времени ожидания блокировки.|  
|[setLoginTimeout](../../../connect/jdbc/reference/setlogintimeout-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает количество секунд, этот объект источника данных будет ожидать при попытке установить соединение.|  
|[setLogWriter](../../../connect/jdbc/reference/setlogwriter-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Задает символьный выходной поток, используемый для всех сообщений ведения журнала и трассировки.|  
|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает значение **multiSubnetFailover** свойство соединения.|  
|[Задание пароля](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает пароль, который будет использоваться для подключения к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает номер порта, используемый для связи с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает тип курсора по умолчанию, который используется для всех результирующих наборов, созданных с помощью этого объекта источника данных.|  
|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) наборы **логическое** значение, указывающее, включена ли отправка параметров на сервер в Юникоде.|  
|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает имя компьютера, на котором выполняется [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает URL-адрес, используемый для подключения к источнику данных.|  
|[Инструкция setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает имя пользователя, который используется для подключения к источнику данных.|  
|[setWorkstationID](../../../connect/jdbc/reference/setworkstationid-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) задает имя компьютера, который используется для подключения к источнику данных клиента.|  
|[setXopenStates](../../../connect/jdbc/reference/setxopenstates-method-sqlserverdatasource.md)|(Наследуется от [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) наборы **логическое** значение, указывающее, включено ли преобразование состояний SQL в состояния, соответствующие стандарту xopen.|  
|[Извлечение из оболочки](../../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md)|Возвращает объект, реализующий указанный интерфейс для доступа к [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-определенных методов.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerDataSource|getApplicationName, getConnection, getDatabaseName, getDescription, getFailoverPartner, getInstanceName, getLastUpdateCount, getLockTimeout, getLoginTimeout, getLogWriter, getPortNumber, getSelectMethod, getSendStringParametersAsUnicode, getServerName, getURL, getUser, getWorkstationID, getXopenStates, setApplicationName, setDatabaseName, setDescription, setFailoverPartner, setInstanceName, setIntegratedSecurity, setLastUpdateCount, setLockTimeout, setLoginTimeout, setLogWriter, setPassword, setPortNumber, setSelectMethod, setSendStringParametersAsUnicode, setServerName, setURL, setUser, setWorkstationID, setXopenStates|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
|javax.sql.ConnectionPoolDataSource|getLoginTimeout, getLogWriter, setLoginTimeout, setLogWriter, getPooledConnection|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  

