---
title: "Элементы SQLServerDataSource | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e749bc5-d765-4864-be2b-7822d4c20c09
caps.latest.revision: "43"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6feb87ad1bb5054b800a001a30af6b94679e977a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverdatasource-members"></a>Элементы SQLServerDataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
  
|Имя|Description|  
|----------|-----------------|  
|[(SQLServerDataSource)](../../../connect/jdbc/reference/sqlserverdatasource-constructor.md)|Инициализирует новый экземпляр [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) класса.|  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
 Нет.  
  
## <a name="methods"></a>Методы  
  
|Имя|Description|  
|----------|-----------------|  
|[getApplicationIntent](../../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)|Возвращает значение **applicationIntent** свойство соединения.|  
|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|Возвращает имя приложения.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)|Пытается установить соединение с данными источника, который [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) представляет.|  
|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|Возвращает имя базы данных.|  
|[getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md)|Возвращает **логическое** значение, указывающее, включено ли свойство encrypt.|  
|[getDescription](../../../connect/jdbc/reference/getdescription-method-sqlserverdatasource.md)|Возвращает описание источника данных.|  
|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|Возвращает имя сервера отработки отказа, используемого в конфигурации зеркального отображения базы данных.|  
|[getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md)|Возвращает имя узла, используемого при проверке SSL-сертификата SQL Server.|  
|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|Возвращает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] имя экземпляра.|  
|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|Возвращает **логическое** значение, указывающее, включено ли свойство lastUpdateCount.|  
|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|Возвращает **int** значение, указывающее, ожидает базу данных перед созданием отчета об истечении времени ожидания блокировки в миллисекундах.|  
|[getLoginTimeout](../../../connect/jdbc/reference/getlogintimeout-method-sqlserverdatasource.md)|Возвращает количество секунд, это [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) объект ожидает при попытке установить соединение.|  
|[getLogWriter](../../../connect/jdbc/reference/getlogwriter-method-sqlserverdatasource.md)|Возвращает символьный выходной поток, используемый для регистрации всех сообщений ведения журнала и трассировки.|  
|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|Возвращает значение **multiSubnetFailover** свойство соединения.|  
|[getPacketSize](../../../connect/jdbc/reference/getpacketsize-method-sqlserverdatasource.md)|Возвращает текущий размер сетевого пакета, используемый для связи с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], указанного в байтах.|  
|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|Возвращает текущий номер порта, используемый для связи с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[getReference](../../../connect/jdbc/reference/getreference-method-sqlserverdatasource.md)|Возвращает ссылку на это [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) объекта.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverdatasource.md)|Возвращает режим буферизации для этого ответов [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) объекта.|  
|[метод getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|Возвращает тип курсора по умолчанию, используемый для всех результирующих наборов, созданных с помощью этого [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) объекта.|  
|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|Возвращает **логическое** значение, указывающее, включена ли отправка параметров на сервер в Юникоде.|  
|[getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|Возвращает значение **SendTimeAsDatetime** свойство соединения.|  
|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|Возвращает имя компьютера под управлением [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[getTrustServerCertificate](../../../connect/jdbc/reference/gettrustservercertificate-method-sqlserverdatasource.md)|Возвращает **логическое** значение, указывающее, включено ли свойство trustServerCertificate.|  
|[getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md)|Возвращает путь к файлу сертификата trustStore (включая имя файла).|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|Возвращает URL-адрес, используемый для соединения с источником данных.|  
|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|Возвращает имя пользователя, используемое для соединения с источником данных.|  
|[getUseSQLServerBaseDate](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|Возвращает значение свойства соединения useSQLServerBaseDate.|  
|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|Возвращает имя клиентского компьютера, используемого для соединения с источником данных.|  
|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|Возвращает **логическое** значение, указывающее, включено ли преобразование состояний SQL в состояния, соответствующие стандарту xopen.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)|Указывает, является ли этот объект источника данных оболочкой указанного интерфейса.|  
|[setApplicationIntent](../../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)|Задает значение **applicationIntent** свойство соединения.|  
|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|Задает имя приложения.|  
|[метода setAuthenticationScheme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|Указывает, какой тип встроенной безопасности должен использоваться приложением.|  
|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|Задает имя базы данных для соединения.|  
|[Описание](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|Задает описание источника данных.|  
|[setEncrypt](../../../connect/jdbc/reference/setencrypt-method-sqlserverdatasource.md)|Наборы **логическое** значение, указывающее, включено ли свойство encrypt.|  
|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|Задает имя сервера отработки отказа, используемого в конфигурации зеркального отображения базы данных.|  
|[setHostNameInCertificate](../../../connect/jdbc/reference/sethostnameincertificate-method-sqlserverdatasource.md)|Задает имя узла, используемого для проверки SSL-сертификата SQL Server.|  
|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|Наборы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] имя экземпляра.|  
|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|Наборы **логическое** значение, указывающее, включено ли свойство integratedSecurity.|  
|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|Наборы **логическое** значение, указывающее, включено ли свойство lastUpdateCount.|  
|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|Наборы **int** значение, указывающее количество миллисекунд ждать, пока база данных сообщает об истечении времени ожидания блокировки.|  
|[setLoginTimeout](../../../connect/jdbc/reference/setlogintimeout-method-sqlserverdatasource.md)|Задает количество секунд, которое это [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) объект ожидает при попытке установить соединение.|  
|[setLogWriter](../../../connect/jdbc/reference/setlogwriter-method-sqlserverdatasource.md)|Задает символьный выходной поток, который используется для вывода всех сообщений ведения журнала и трассировки.|  
|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|Задает значение **multiSubnetFailover** свойство соединения.|  
|[setPacketSize](../../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md)|Задает текущий размер сетевого пакета, используемый для связи с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], указанного в байтах.|  
|[Задание пароля](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|Задает пароль, используемый для подключения к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|Задает номер порта, используемый для взаимодействия с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)|Задает режим буферизации ответов для подключений, созданных с помощью этого [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) объекта.|  
|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|Задает тип курсора по умолчанию, используемый для всех результирующих наборов, созданных с помощью этого [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) объекта.|  
|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|Наборы **логическое** значение, указывающее, включена ли отправка параметров на сервер в Юникоде.|  
|[setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)|Задает порядок отправки значений java.sql.Time на сервер.|  
|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|Задает имя компьютера под управлением [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[setTrustServerCertificate](../../../connect/jdbc/reference/settrustservercertificate-method-sqlserverdatasource.md)|Наборы **логическое** значение, указывающее, включено ли свойство trustServerCertificate.|  
|[setTrustStore](../../../connect/jdbc/reference/settruststore-method-sqlserverdatasource.md)|Задает путь к файлу сертификата trustStore (включая имя файла).|  
|[setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md)|Задает пароль, используемый для проверки целостности данных trustStore.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)|Задает URL-адрес, используемый для соединения с источником данных.|  
|[Инструкция setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)|Задает имя пользователя, используемое для соединения с источником данных.|  
|[setWorkstationID](../../../connect/jdbc/reference/setworkstationid-method-sqlserverdatasource.md)|Задает имя клиентского компьютера, используемого для соединения с источником данных.|  
|[setXopenStates](../../../connect/jdbc/reference/setxopenstates-method-sqlserverdatasource.md)|Наборы **логическое** значение, указывающее, включено ли преобразование состояний SQL в состояния, соответствующие стандарту xopen.|  
|[Извлечение из оболочки](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)|Возвращает объект, реализующий указанный интерфейс для доступа к [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-определенных методов.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
