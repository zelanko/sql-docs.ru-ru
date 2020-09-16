---
description: Элементы SQLServerDataSource
title: Элементы SQLServerDataSource | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7e749bc5-d765-4864-be2b-7822d4c20c09
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4f425bfe9f4a27595270c2a060027e6a4358c6c2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450666"
---
# <a name="sqlserverdatasource-members"></a>Элементы SQLServerDataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые классом [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
## <a name="constructors"></a>Конструкторы  
  
|Имя|Описание|  
|----------|-----------------|  
|[SQLServerDataSource ()](../../../connect/jdbc/reference/sqlserverdatasource-constructor.md)|Инициализирует новый экземпляр класса [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
 Нет.  
  
## <a name="methods"></a>Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[getApplicationIntent](../../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)|Возвращает значение свойства подключения **applicationIntent**.|  
|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|Возвращает имя приложения.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)|Пытается установить подключение к источнику данных, представляемому этим объектом [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|Возвращает имя базы данных.|  
|[getDisableStatementPooling](../../../connect/jdbc/reference/getdisablestatementpooling-method-sqlserverdatasource.md)|Возвращает значение свойства **disableStatementPooling** для подключения. Этот параметр определяет, включено ли объединение инструкций в пул для этого подключения.|  
|[getEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource.md)|Возвращает значение свойства подключения **enablePrepareOnFirstPreparedStatementCall**.|  
|[getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md)|Возвращает значение типа **Boolean**, определяющее, включено ли свойство encrypt.|  
|[getDescription](../../../connect/jdbc/reference/getdescription-method-sqlserverdatasource.md)|Возвращает описание источника данных.|  
|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|Возвращает имя сервера отработки отказа, используемого в конфигурации зеркального отображения базы данных.|  
|[getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md)|Возвращает имя узла, используемого при проверке TLS-сертификата SQL Server, который ранее назывался SSL-сертификатом.|  
|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|Возвращает имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|Возвращает значение типа **boolean**, определяющее, включено ли свойство lastUpdateCount.|  
|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|Возвращает значение типа **int**, указывающее время в миллисекундах, в течение которого база данных будет ожидать, прежде чем сообщит об истечении времени ожидания блокировки.|  
|[getLoginTimeout](../../../connect/jdbc/reference/getlogintimeout-method-sqlserverdatasource.md)|Возвращает время в секундах, в течение которого данный объект [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) ожидает при попытке установить подключение.|  
|[getLogWriter](../../../connect/jdbc/reference/getlogwriter-method-sqlserverdatasource.md)|Возвращает символьный выходной поток, используемый для регистрации всех сообщений ведения журнала и трассировки.|  
|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|Возвращает значение свойства подключения **multiSubnetFailover**.|  
|[getPacketSize](../../../connect/jdbc/reference/getpacketsize-method-sqlserverdatasource.md)|Возвращает текущий размер сетевого пакета в байтах, используемый для обмена данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|Возвращает текущий номер порта, используемый для обмена данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[getReference](../../../connect/jdbc/reference/getreference-method-sqlserverdatasource.md)|Возвращает ссылку на этот объект [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverdatasource.md)|Возвращает режим буферизации ответов для этого объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
|[getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|Возвращает тип курсора по умолчанию, используемый для всех результирующих наборов, созданных с помощью этого объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|Возвращает значение типа **Boolean**, определяющее, разрешена ли отправка параметров на сервер в формате Юникода.|  
|[getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|Возвращает значение свойства подключения **sendTimeAsDatetime**.|  
|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|Возвращает имя компьютера, на котором работает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[getServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/getserverpreparedstatementdiscardthreshold-method-sqlserverdatasource.md)|Возвращает значение свойства подключения **serverPreparedStatementDiscardThreshold**.|  
|[getStatementPoolingCacheSize](../../../connect/jdbc/reference/getstatementpoolingcachesize-method-sqlserverdatasource.md)|Возвращает размер кэша подготовленных инструкций для этого подключения.|  
|[getTrustManagerClass](../../../connect/jdbc/reference/gettrustmanagerclass-method-sqlserverdatasource.md)|Возвращает строковое значение свойства подключения "TrustManagerClass".|  
|[getTrustManagerConstructorArg](../../../connect/jdbc/reference/gettrustmanagerconstructorarg-method-sqlserverdatasource.md)|Возвращает строковое значение свойства подключения "TrustManagerConstructorArg".|  
|[getTrustServerCertificate](../../../connect/jdbc/reference/gettrustservercertificate-method-sqlserverdatasource.md)|Возвращает значение типа **Boolean**, определяющее, включено ли свойство trustServerCertificate.|  
|[getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md)|Возвращает путь к файлу сертификата trustStore (включая имя файла).|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|Возвращает URL-адрес, используемый для соединения с источником данных.|  
|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|Возвращает имя пользователя, используемое для соединения с источником данных.|  
|[getUseSQLServerBaseDate](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|Возвращает значение свойства соединения useSQLServerBaseDate.|  
|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|Возвращает имя клиентского компьютера, используемого для соединения с источником данных.|  
|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|Возвращает значение типа **Boolean**, определяющее, включено ли преобразование состояний SQL в состояния, совместимые с XOPEN.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)|Указывает, является ли этот объект источника данных оболочкой указанного интерфейса.|  
|[setApplicationIntent](../../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)|Устанавливает значение свойства подключения **applicationIntent**.|  
|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|Задает имя приложения.|  
|[setAuthenticationScheme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|Указывает, какой тип встроенной безопасности должен использоваться приложением.|  
|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|Задает имя базы данных для соединения.|  
|[setDescription](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|Задает описание источника данных.|  
|[setDisableStatementPooling](../../../connect/jdbc/reference/setdisablestatementpooling-method-sqlserverdatasource.md)|Задает значение true или false для параметра создания пула инструкций.|  
|[setEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/setenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource.md)|Задает новое значение свойства подключения **enablePrepareOnFirstPreparedStatementCall**.|  
|[setEncrypt](../../../connect/jdbc/reference/setencrypt-method-sqlserverdatasource.md)|Задает значение типа **Boolean**, определяющее, включено ли свойство encrypt.|  
|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|Задает имя сервера отработки отказа, используемого в конфигурации зеркального отображения базы данных.|  
|[setHostNameInCertificate](../../../connect/jdbc/reference/sethostnameincertificate-method-sqlserverdatasource.md)|Задает имя узла, используемого для проверки TLS-сертификата SQL Server, который ранее назывался SSL-сертификатом.|  
|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|Задает имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|Задает значение типа **Boolean**, определяющее, включено ли свойство integratedSecurity.|  
|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|Задает значение типа **Boolean**, определяющее, включено ли свойство lastUpdateCount.|  
|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|Задает значение типа **int**, определяющее время в миллисекундах, по истечении которого база данных сообщит об истечении времени ожидания блокировки.|  
|[setLoginTimeout](../../../connect/jdbc/reference/setlogintimeout-method-sqlserverdatasource.md)|Задает время в секундах, которое ждет объект [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) при попытке установить подключение.|  
|[setLogWriter](../../../connect/jdbc/reference/setlogwriter-method-sqlserverdatasource.md)|Задает символьный выходной поток, который используется для вывода всех сообщений ведения журнала и трассировки.|  
|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|Устанавливает значение свойства подключения **multiSubnetFailover**.|  
|[setPacketSize](../../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md)|Задает текущий размер сетевого пакета в байтах, используемый для обмена данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|Задает пароль, используемый для подключения к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|Задает номер порта, используемый для обмена данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)|Задает режим буферизации ответа для подключений, созданных с использованием этого объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|Задает тип курсора по умолчанию, используемый для всех результирующих наборов, созданных с помощью этого объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|Задает значение типа **Boolean**, определяющее, разрешена ли отправка параметров на сервер в формате Юникода.|  
|[setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)|Задает порядок отправки значений java.sql.Time на сервер.|  
|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|Задает имя компьютера, на котором работает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[setServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource.md)|Задает новое значение для свойства подключения **serverPreparedStatementDiscardThreshold**.|  
|[setStatementPoolingCacheSize](../../../connect/jdbc/reference/setstatementpoolingcachesize-method-sqlserverdatasource.md)|Задает размер кэша подготовленных инструкций для этого подключения.|  
|[setTrustManagerClass](../../../connect/jdbc/reference/settrustmanagerclass-method-sqlserverdatasource.md)|Устанавливает строковое значение свойства подключения "TrustManagerClass".|  
|[setTrustManagerConstructorArg](../../../connect/jdbc/reference/settrustmanagerconstructorarg-method-sqlserverdatasource.md)|Устанавливает строковое значение свойства подключения "TrustManagerConstructorArg".|  
|[setTrustServerCertificate](../../../connect/jdbc/reference/settrustservercertificate-method-sqlserverdatasource.md)|Задает значение типа **Boolean**, определяющее, включено ли свойство trustServerCertificate.|  
|[setTrustStore](../../../connect/jdbc/reference/settruststore-method-sqlserverdatasource.md)|Задает путь к файлу сертификата trustStore (включая имя файла).|  
|[setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md)|Задает пароль, используемый для проверки целостности данных trustStore.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)|Задает URL-адрес, используемый для соединения с источником данных.|  
|[setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)|Задает имя пользователя, используемое для соединения с источником данных.|  
|[setWorkstationID](../../../connect/jdbc/reference/setworkstationid-method-sqlserverdatasource.md)|Задает имя клиентского компьютера, используемого для соединения с источником данных.|  
|[setXopenStates](../../../connect/jdbc/reference/setxopenstates-method-sqlserverdatasource.md)|Задает значение типа **Boolean**, определяющее, включено ли преобразование состояний SQL в состояния, совместимые с XOPEN.|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)|Возвращает объект, реализующий указанный интерфейс для доступа к методам, относящимся к драйверу [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
