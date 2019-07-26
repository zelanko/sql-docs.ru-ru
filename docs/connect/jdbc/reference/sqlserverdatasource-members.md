---
title: Элементы SQLServerDataSource | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7e749bc5-d765-4864-be2b-7822d4c20c09
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 800f87c82987396743ec4c0c278444c4ba61d49b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67971410"
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
|[getApplicationIntent](../../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)|Возвращает значение свойства соединения **ApplicationIntent** .|  
|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|Возвращает имя приложения.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)|Пытается установить подключение к источнику данных, представляемому этим объектом [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|Возвращает имя базы данных.|  
|[getDisableStatementPooling](../../../connect/jdbc/reference/getdisablestatementpooling-method-sqlserverdatasource.md)|Возвращает значение свойства соединения **disableStatementPooling** . Этот параметр определяет, включено ли объединение инструкций в пул для данного соединения.|  
|[getEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource.md)|Возвращает значение свойства соединения **енаблепрепареонфирстпрепаредстатементкалл** .|  
|[getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md)|Возвращает значение типа **Boolean**, определяющее, включено ли свойство encrypt.|  
|[getDescription](../../../connect/jdbc/reference/getdescription-method-sqlserverdatasource.md)|Возвращает описание источника данных.|  
|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|Возвращает имя сервера отработки отказа, используемого в конфигурации зеркального отображения базы данных.|  
|[getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md)|Возвращает имя узла, используемого при проверке SSL-сертификата SQL Server.|  
|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|Возвращает имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|Возвращает значение типа **boolean**, определяющее, включено ли свойство lastUpdateCount.|  
|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|Возвращает значение типа **int**, указывающее время в миллисекундах, в течение которого база данных будет ожидать, прежде чем сообщит об истечении времени ожидания блокировки.|  
|[getLoginTimeout](../../../connect/jdbc/reference/getlogintimeout-method-sqlserverdatasource.md)|Возвращает время в секундах, в течение которого данный объект [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) ожидает при попытке установить подключение.|  
|[getLogWriter](../../../connect/jdbc/reference/getlogwriter-method-sqlserverdatasource.md)|Возвращает символьный выходной поток, используемый для регистрации всех сообщений ведения журнала и трассировки.|  
|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|Возвращает значение свойства соединения **MultiSubnetFailover** .|  
|[getPacketSize](../../../connect/jdbc/reference/getpacketsize-method-sqlserverdatasource.md)|Возвращает текущий размер сетевого пакета в байтах, используемый для обмена данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|Возвращает текущий номер порта, используемый для обмена данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[getReference](../../../connect/jdbc/reference/getreference-method-sqlserverdatasource.md)|Возвращает ссылку на этот объект [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverdatasource.md)|Возвращает режим буферизации ответов для этого объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
|[getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|Возвращает тип курсора по умолчанию, используемый для всех результирующих наборов, созданных с помощью этого объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|Возвращает значение типа **Boolean**, определяющее, разрешена ли отправка параметров на сервер в формате Юникода.|  
|[getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|Возвращает значение свойства соединения **сендтимеасдатетиме** .|  
|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|Возвращает имя компьютера, на котором работает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[getServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/getserverpreparedstatementdiscardthreshold-method-sqlserverdatasource.md)|Возвращает значение свойства соединения **серверпрепаредстатементдискардсрешолд** .|  
|[getStatementPoolingCacheSize](../../../connect/jdbc/reference/getstatementpoolingcachesize-method-sqlserverdatasource.md)|Возвращает размер подготовленного кэша инструкций для этого соединения.|  
|[жеттрустманажеркласс](../../../connect/jdbc/reference/gettrustmanagerclass-method-sqlserverdatasource.md)|Возвращает строковое значение свойства соединения TrustManagerClass.|  
|[жеттрустманажерконструкторарг](../../../connect/jdbc/reference/gettrustmanagerconstructorarg-method-sqlserverdatasource.md)|Возвращает строковое значение свойства соединения Трустманажерконструкторарг.|  
|[getTrustServerCertificate](../../../connect/jdbc/reference/gettrustservercertificate-method-sqlserverdatasource.md)|Возвращает значение типа **Boolean**, определяющее, включено ли свойство trustServerCertificate.|  
|[getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md)|Возвращает путь к файлу сертификата trustStore (включая имя файла).|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|Возвращает URL-адрес, используемый для соединения с источником данных.|  
|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|Возвращает имя пользователя, используемое для соединения с источником данных.|  
|[getUseSQLServerBaseDate](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|Возвращает значение свойства соединения useSQLServerBaseDate.|  
|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|Возвращает имя клиентского компьютера, используемого для соединения с источником данных.|  
|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|Возвращает значение типа **Boolean**, определяющее, включено ли преобразование состояний SQL в состояния, совместимые с XOPEN.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)|Указывает, является ли этот объект источника данных оболочкой указанного интерфейса.|  
|[setApplicationIntent](../../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)|Задает значение свойства соединения **ApplicationIntent** .|  
|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|Задает имя приложения.|  
|[setAuthenticationScheme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|Указывает, какой тип встроенной безопасности должен использоваться приложением.|  
|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|Задает имя базы данных для соединения.|  
|[setDescription](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|Задает описание источника данных.|  
|[setDisableStatementPooling](../../../connect/jdbc/reference/setdisablestatementpooling-method-sqlserverdatasource.md)|Задает для группирования инструкций значение true или false.|  
|[setEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/setenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource.md)|Указывает новое значение свойства соединения **енаблепрепареонфирстпрепаредстатементкалл** .|  
|[setEncrypt](../../../connect/jdbc/reference/setencrypt-method-sqlserverdatasource.md)|Задает значение типа **Boolean**, определяющее, включено ли свойство encrypt.|  
|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|Задает имя сервера отработки отказа, используемого в конфигурации зеркального отображения базы данных.|  
|[setHostNameInCertificate](../../../connect/jdbc/reference/sethostnameincertificate-method-sqlserverdatasource.md)|Задает имя узла, используемого для проверки SSL-сертификата SQL Server.|  
|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|Задает имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|Задает значение типа **Boolean**, определяющее, включено ли свойство integratedSecurity.|  
|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|Задает значение типа **Boolean**, определяющее, включено ли свойство lastUpdateCount.|  
|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|Задает значение типа **int**, определяющее время в миллисекундах, по истечении которого база данных сообщит об истечении времени ожидания блокировки.|  
|[setLoginTimeout](../../../connect/jdbc/reference/setlogintimeout-method-sqlserverdatasource.md)|Задает время в секундах, которое ждет объект [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) при попытке установить подключение.|  
|[setLogWriter](../../../connect/jdbc/reference/setlogwriter-method-sqlserverdatasource.md)|Задает символьный выходной поток, который используется для вывода всех сообщений ведения журнала и трассировки.|  
|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|Задает значение свойства соединения **MultiSubnetFailover** .|  
|[setPacketSize](../../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md)|Задает текущий размер сетевого пакета в байтах, используемый для обмена данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|Задает пароль, используемый для подключения к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|Задает номер порта, используемый для обмена данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)|Задает режим буферизации ответа для подключений, созданных с использованием этого объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|Задает тип курсора по умолчанию, используемый для всех результирующих наборов, созданных с помощью этого объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).|  
|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|Задает значение типа **Boolean**, определяющее, разрешена ли отправка параметров на сервер в формате Юникода.|  
|[setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)|Задает порядок отправки значений java.sql.Time на сервер.|  
|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|Задает имя компьютера, на котором работает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[setServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource.md)|Задает новое значение свойства соединения **серверпрепаредстатементдискардсрешолд** .|  
|[setStatementPoolingCacheSize](../../../connect/jdbc/reference/setstatementpoolingcachesize-method-sqlserverdatasource.md)|Задает размер подготовленного кэша инструкций для этого соединения.|  
|[сеттрустманажеркласс](../../../connect/jdbc/reference/settrustmanagerclass-method-sqlserverdatasource.md)|Задает строковое значение свойства соединения TrustManagerClass.|  
|[сеттрустманажерконструкторарг](../../../connect/jdbc/reference/settrustmanagerconstructorarg-method-sqlserverdatasource.md)|Задает строковое значение свойства соединения Трустманажерконструкторарг.|  
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
  
  
