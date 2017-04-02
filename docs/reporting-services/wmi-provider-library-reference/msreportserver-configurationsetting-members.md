---
title: "Элементы MSReportServer_ConfigurationSetting | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "MSReportServer_ConfigurationSetting Members"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "поставщик WMI [службы Reporting Services], класс MSReportServer_ConfigurationSetting"
  - "MSReportServer_ConfigurationSetting, класс"
ms.assetid: 5e21a53a-a2f8-4b35-a8d9-5483519e3857
caps.latest.revision: 46
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 46
---
# Элементы MSReportServer_ConfigurationSetting
  Класс MSReportServer_ConfigurationSetting содержит указанные ниже свойства и методы.  
  
## Открытые свойства  
  
|||  
|-|-|  
|[ConnectionPoolSize](../../reporting-services/wmi-provider-library-reference/connectionpoolsize-property-wmi-msreportserver-configurationsetting.md)|Возвращает размер пула соединений, используемого сервером отчетов для связи с экземпляром компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , где размещается база данных сервера отчетов. Только для чтения.|  
|[DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/databaselogonaccount-property-wmi-msreportserver-configurationsetting.md)|Задает учетную запись входа, которую сервер отчетов использует для соединения с экземпляром компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором находится база данных сервера отчетов. Только для чтения.|  
|[DatabaseLogonTimeout](../../reporting-services/wmi-provider-library-reference/databaselogontimeout-property-wmi-msreportserver-configurationsetting.md)|Указывает число секунд ожидания перед тем, как попытка входа в базу данных сервера отчетов признается неуспешной. Только для чтения.|  
|[DatabaseLogonType](../../reporting-services/wmi-provider-library-reference/databaselogontype-property-wmi-msreportserver-configurationsetting.md)|Указывает, использует ли сервер отчетов для доступа к базе данных сервера отчетов учетную запись службы Windows, учетную запись пользователя Windows или имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Только для чтения.|  
|[DatabaseName](../../reporting-services/wmi-provider-library-reference/databasename-property-wmi-msreportserver-configurationsetting.md)|Задает имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в котором размещается база данных сервера отчетов.|  
|[DatabaseQueryTimeout](../../reporting-services/wmi-provider-library-reference/databasequerytimeout-property-wmi-msreportserver-configurationsetting.md)|Задает число секунд, проходящих до истечения времени ожидания команды или ее завершения с ошибкой. Сервер отчетов определяет время для процесса по базе данных сервера отчетов, а не по источнику данных для отчета.|  
|[DatabaseServerName](../../reporting-services/wmi-provider-library-reference/databaseservername-property-wmi-msreportserver-configurationsetting.md)|Задает имя сервера, на котором установлена база данных сервера отчетов.|  
|[Свойство InstallationID](../../reporting-services/wmi-provider-library-reference/installationid-property-wmi-msreportserver-configurationsetting.md)|Возвращает уникальный идентификатор для определенного экземпляра сервера отчетов.|  
|[InstanceName](../../reporting-services/wmi-provider-library-reference/instancename-property-wmi-msreportserver-configurationsetting.md)|Указывает имя экземпляра сервера отчетов на заданном компьютере.|  
|[IsInitialized](../../reporting-services/wmi-provider-library-reference/isinitialized-property-wmi-msreportserver-configurationsetting.md)|Указывает, инициализирован ли экземпляр сервера отчетов. Только для чтения.|  
|[IsSharePointIntegrated](../../reporting-services/wmi-provider-library-reference/issharepointintegrated-property-wmi.md)|Показывает, настроен ли сервер отчетов в режиме интеграции для SharePoint.|  
|[IsWebServiceEnabled](../../reporting-services/wmi-provider-library-reference/iswebserviceenabled-property-wmi-msreportserver-configurationsetting.md)|Указывает, включена ли веб-служба сервера отчетов. Только для чтения.|  
|[IsWindowsServiceEnabled](../../reporting-services/wmi-provider-library-reference/iswindowsserviceenabled-property-wmi-msreportserver-configurationsetting.md)|Указывает, включена ли служба Windows сервера отчетов. Только для чтения.|  
|[Свойство MachineAccountIdentity (WMI)](../../reporting-services/wmi-provider-library-reference/machineaccountidentity-property-wmi.md)|Возвращает удостоверение учетной записи компьютера, на котором установлен сервер отчетов.|  
|[PathName](../../reporting-services/wmi-provider-library-reference/pathname-property-wmi-msreportserver-configurationsetting.md)|Задает путь установки для экземпляра сервера отчетов.|  
|[SecureConnectionLevel](../../reporting-services/wmi-provider-library-reference/secureconnectionlevel-property-wmi-msreportserver-configurationsetting.md)|Возвращает уровень безопасного соединения, заданный в файле RSReportServer.config.|  
|[SenderEmailAddress](../../reporting-services/wmi-provider-library-reference/senderemailaddress-property-wmi-msreportserver-configurationsetting.md)|Возвращает адрес, используемый для отправки электронной почты с сервера отчетов. Только для чтения.|  
|[SendUsingSMTPServer](../../reporting-services/wmi-provider-library-reference/sendusingsmtpserver-property-wmi-msreportserver-configurationsetting.md)|Указывает, имеет ли свойство SendUsing в конфигурации электронной почты значение TRUE.|  
|[SMTPServer](../../reporting-services/wmi-provider-library-reference/smtpserver-property-wmi-msreportserver-configurationsetting.md)|Возвращает свойство SMTP-сервера из файла RSReportServer.config. Только для чтения.|  
|[UnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/unattendedexecutionaccount-property-wmi-msreportserver-configurationsetting.md)|Указывает учетную запись пользователя для входа, олицетворение которой выполняет сервер отчетов во время автоматического выполнения отчетов. Только для чтения.|  
|[Версия](../../reporting-services/wmi-provider-library-reference/version-property-wmi-msreportserver-configurationsetting.md)|Возвращает версию сервера отчетов.|  
|[Свойство VirtualDirectoryReportManager (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/virtualdirectoryreportmanager-property-wmi-msreportserver-configurationsetting.md)|Возвращает виртуальный каталог для приложения диспетчера отчетов.|  
|[Свойство VirtualDirectoryReportServer (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/virtualdirectoryreportserver-property-wmi-msreportserver-configurationsetting.md)|Возвращает виртуальный каталог для приложения веб-службы сервера отчетов.|  
|[WindowsServiceIdentityActual](../../reporting-services/wmi-provider-library-reference/windowsserviceidentityactual-property-wmi-msreportserver-configurationsetting.md)|Возвращает удостоверение, с которым фактически выполняется служба Windows сервера отчетов. Только для чтения.|  
|[WindowsServiceIdentityConfigured](../../reporting-services/wmi-provider-library-reference/windowsserviceidentityconfigured-property.md)|Возвращает удостоверение, для выполнения с которым была в последний раз настроена служба Windows сервера отчетов. Только для чтения.|  
  
## Открытые методы  
  
|||  
|-|-|  
|[BackupEncryptionKey](../../reporting-services/wmi-provider-library-reference/backupencryptionkey-method-wmi-msreportserver-configurationsetting.md)|Создает резервную копию ключа шифрования для экземпляра. Ключ шифрования хранится в зашифрованном виде под защитой пароля.|  
|[CreateSSLCertificateBinding Method (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/createsslcertificatebinding-method-wmi-msreportserver-configurationsetting.md)|Создает привязку SSL-сертификата.|  
|[DeleteEncryptedInformation](../../reporting-services/wmi-provider-library-reference/deleteencryptedinformation-method-wmi-msreportserver-configurationsetting.md)|Удаляет зашифрованные данные из базы данных сервера отчетов.|  
|[DeleteEncryptionKey](../../reporting-services/wmi-provider-library-reference/deleteencryptionkey-method-wmi-msreportserver-configurationsetting.md)|Удаляет ключи шифрования из базы данных сервера отчетов.|  
|[GenerateDatabaseCreationScript](../../reporting-services/wmi-provider-library-reference/generatedatabasecreationscript-method-wmi-msreportserver-configurationsetting.md)|Формирует скрипт SQL, который можно использовать для создания базы данных сервера отчетов.|  
|[GenerateDatabaseRightsScript](../../reporting-services/wmi-provider-library-reference/generatedatabaserightsscript-method-wmi-msreportserver-configurationsetting.md)|Формирует скрипт SQL, с помощью которого можно предоставить пользователю разрешения для базы данных сервера отчетов.|  
|[GenerateDatabaseUpgradeScript](../../reporting-services/wmi-provider-library-reference/generatedatabaseupgradescript-method-wmi-msreportserver-configurationsetting.md)|Формирует скрипт SQL, который можно использовать для обновления базы данных сервера отчетов.|  
|[Метод GetAdminSiteUrl (WMI)](../../reporting-services/wmi-provider-library-reference/getadminsiteurl-method-wmi.md)|Возвращает абсолютный URL-адрес веб-сайта центра администрирования.|  
|[GetDatabaseVersionDisplayName](../../reporting-services/wmi-provider-library-reference/getdatabaseversiondisplayname-method-wmi.md)|Возвращает отображаемое имя для указанной строки версии базы данных сервера отчетов.|  
|[InitializeReportServer](../../reporting-services/wmi-provider-library-reference/initializereportserver-method-wmi-msreportserver-configurationsetting.md)|Инициализирует заданный экземпляр сервера отчетов.|  
|[Метод ListInstalledSharePointVersions (WMI)](../../reporting-services/wmi-provider-library-reference/listinstalledsharepointversions-method-wmi.md)|Возвращает набор токенов, представляющих версии [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]или [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] , установленного на том же компьютере, что и сервер отчетов.|  
|[Метод ListIPAddresses (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/listipaddresses-method-wmi-msreportserver-configurationsetting.md)|Выводит список IP-адресов для компьютера.|  
|[ListReportServersInDatabase](../../reporting-services/wmi-provider-library-reference/listreportserversindatabase-method-wmi-msreportserver-configurationsetting.md)|Возвращает список установленных экземпляров сервера отчетов, присутствующих в базе данных сервера отчетов, независимо от того, имеют ли эти экземпляры доступ к защищенным сведениям.|  
|[Метод ListReservedURLs (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/listreservedurls-method-wmi-msreportserver-configurationsetting.md)|Выводит список URL-адресов, зарезервированных для всех приложений на сервере отчетов.|  
|[Метод ListSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/listsslcertificatebindings-method-wmi-msreportserver-configurationsetting.md)|Выводит список привязок SSL-сертификатов, существующих в HTTP.SYS, и привязок, ожидаемых в файле rsreportserver.config.|  
|[Метод ListSSLCertificates (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/listsslcertificates-method-wmi-msreportserver-configurationsetting.md)|Выводит список SSL-сертификатов, установленных на компьютере.|  
|[ReencryptSecureInformation](../../reporting-services/wmi-provider-library-reference/reencryptsecureinformation-method-wmi-msreportserver-configurationsetting.md)|Создает новый ключ шифрования и повторно шифрует все защищаемые сведения в базе данных сервера отчетов с этим новым ключом.|  
|[Метод RemoveSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/removesslcertificatebindings-method-wmi-msreportserver-configurationsetting.md)|Удаляет привязку SSL-сертификата.|  
|[RemoveUnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/removeunattendedexecutionaccount-method-wmi-msreportserver-configurationsetting.md)|Удаляет учетную запись автоматического выполнения из конфигурации сервера отчетов.|  
|[Метод RemoveURL (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/removeurl-method-wmi-msreportserver-configurationsetting.md)|Удаляет URL-адрес, зарезервированный для сервера отчетов.|  
|[Метод ReserveURL (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/reserveurl-method-wmi-msreportserver-configurationsetting.md)|Добавляет резервирование URL-адресов для заданного приложения.|  
|[RestoreEncryptionKey](../../reporting-services/wmi-provider-library-reference/restoreencryptionkey-method-wmi-msreportserver-configurationsetting.md)|Повторно применяет заданный ключ шифрования к базе данных сервера отчетов.|  
|[SetDatabaseConnection](../../reporting-services/wmi-provider-library-reference/setdatabaseconnection-method-wmi-msreportserver-configurationsetting.md)|Задает подключение к определенной базе данных сервера отчетов.|  
|[SetDatabaseLogonTimeout](../../reporting-services/wmi-provider-library-reference/setdatabaselogontimeout-method-wmi-msreportserver-configurationsetting.md)|Указывает значение времени ожидания по умолчанию для попыток входа в базу данных сервера отчетов.|  
|[SetDatabaseQueryTimeout](../../reporting-services/wmi-provider-library-reference/setdatabasequerytimeout-method-wmi-msreportserver-configurationsetting.md)|Указывает значение времени ожидания по умолчанию для подключений к базе данных сервера отчетов.|  
|[SetEmailConfiguration](../../reporting-services/wmi-provider-library-reference/setemailconfiguration-method-wmi-msreportserver-configurationsetting.md)|Настраивает модуль доставки электронной почты, используемый сервером отчетов для отправки электронной почты.|  
|[SetSecureConnectionLevel](../../reporting-services/wmi-provider-library-reference/setsecureconnectionlevel-method-wmi-msreportserver-configurationsetting.md)|Задает уровень безопасных соединений для сервера отчетов.|  
|[SetServiceState](../../reporting-services/wmi-provider-library-reference/setservicestate-method-wmi-msreportserver-configurationsetting.md)|Включает и выключает службу Windows и веб-службу сервера отчетов.|  
|[SetUnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/setunattendedexecutionaccount-method-wmi-msreportserver-configurationsetting.md)|Задает учетную запись, используемую для автоматического выполнения отчетов.|  
|[Метод SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/setvirtualdirectory-method-wmi-msreportserver-configurationsetting.md)|Задает виртуальный каталог для приложения.|  
|[SetWindowsServiceIdentity](../../reporting-services/wmi-provider-library-reference/setwindowsserviceidentity-method-wmi-msreportserver-configurationsetting.md)|Обеспечивает выполнение службы Windows сервера отчетов под именем указанного пользователя Windows и предоставляет этой учетной записи разрешения файловой системы, достаточные для работы сервера отчетов.|  
  
## См. также  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  