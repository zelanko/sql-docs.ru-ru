---
title: Члены MSReportServer_ConfigurationSetting | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- MSReportServer_ConfigurationSetting Members
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], MSReportServer_ConfigurationSetting class
- MSReportServer_ConfigurationSetting class
ms.assetid: 5e21a53a-a2f8-4b35-a8d9-5483519e3857
caps.latest.revision: 46
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 32a253a22466d154c5e7e0fc3bb355c20c0f0847
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096349"
---
# <a name="msreportserverconfigurationsetting-members"></a>Элементы MSReportServer_ConfigurationSetting
  Класс MSReportServer_ConfigurationSetting содержит указанные ниже свойства и методы.  
  
## <a name="public-properties"></a>Открытые свойства  
  
|||  
|-|-|  
|[ConnectionPoolSize](configurationsetting-property-connectionpoolsize.md)|Возвращает размер пула соединений, используемого сервером отчетов для связи с экземпляром компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , где размещается база данных сервера отчетов. Только для чтения.|  
|[DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md)|Задает учетную запись входа, которую сервер отчетов использует для соединения с экземпляром компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором находится база данных сервера отчетов. Только для чтения.|  
|[DatabaseLogonTimeout](configurationsetting-property-databaselogontimeout.md)|Указывает число секунд ожидания перед тем, как попытка входа в базу данных сервера отчетов признается неуспешной. Только для чтения.|  
|[DatabaseLogonType](configurationsetting-property-databaselogontype.md)|Указывает, использует ли сервер отчетов для доступа к базе данных сервера отчетов учетную запись службы Windows, учетную запись пользователя Windows или имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Только для чтения.|  
|[DatabaseName](configurationsetting-property-databasename.md)|Задает имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в котором размещается база данных сервера отчетов.|  
|[DatabaseQueryTimeout](configurationsetting-property-databasequerytimeout.md)|Задает число секунд, проходящих до истечения времени ожидания команды или ее завершения с ошибкой. Сервер отчетов определяет время для процесса по базе данных сервера отчетов, а не по источнику данных для отчета.|  
|[DatabaseServerName](configurationsetting-property-databaseservername.md)|Задает имя сервера, на котором установлена база данных сервера отчетов.|  
|[Свойство InstallationID](configurationsetting-property-installationid.md)|Возвращает уникальный идентификатор для определенного экземпляра сервера отчетов.|  
|[InstanceName](configurationsetting-property-instancename.md)|Указывает имя экземпляра сервера отчетов на заданном компьютере.|  
|[IsInitialized](configurationsetting-property-isinitialized.md)|Указывает, инициализирован ли экземпляр сервера отчетов. Только для чтения.|  
|[IsSharePointIntegrated](configurationsetting-property-issharepointintegrated.md)|Показывает, настроен ли сервер отчетов в режиме интеграции для SharePoint.|  
|[IsWebServiceEnabled](configurationsetting-property-iswebserviceenabled.md)|Указывает, включена ли веб-служба сервера отчетов. Только для чтения.|  
|[IsWindowsServiceEnabled](configurationsetting-property-iswindowsserviceenabled.md)|Указывает, включена ли служба Windows сервера отчетов. Только для чтения.|  
|[Свойство MachineAccountIdentity &#40;WMI&#41;](configurationsetting-property-machineaccountidentity.md)|Возвращает удостоверение учетной записи компьютера, на котором установлен сервер отчетов.|  
|[PathName](configurationsetting-property-pathname.md)|Задает путь установки для экземпляра сервера отчетов.|  
|[SecureConnectionLevel](configurationsetting-property-secureconnectionlevel.md)|Возвращает уровень безопасного соединения, заданный в файле RSReportServer.config.|  
|[SenderEmailAddress](configurationsetting-property-senderemailaddress.md)|Возвращает адрес, используемый для отправки электронной почты с сервера отчетов. Только для чтения.|  
|[SendUsingSMTPServer](configurationsetting-property-sendusingsmtpserver.md)|Указывает, имеет ли свойство SendUsing в конфигурации электронной почты значение TRUE.|  
|[SMTPServer](configurationsetting-property-smtpserver.md)|Возвращает свойство SMTP-сервера из файла RSReportServer.config. Только для чтения.|  
|[UnattendedExecutionAccount](configurationsetting-property-unattendedexecutionaccount.md)|Указывает учетную запись пользователя для входа, олицетворение которой выполняет сервер отчетов во время автоматического выполнения отчетов. Только для чтения.|  
|[Версия](configurationsetting-property-version.md)|Возвращает версию сервера отчетов.|  
|[Свойство VirtualDirectoryReportManager &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-property-virtualdirectoryreportmanager.md)|Возвращает виртуальный каталог для приложения диспетчера отчетов.|  
|[Свойство VirtualDirectoryReportServer &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-property-virtualdirectoryreportserver.md)|Возвращает виртуальный каталог для приложения веб-службы сервера отчетов.|  
|[WindowsServiceIdentityActual](configurationsetting-property-windowsserviceidentityactual.md)|Возвращает удостоверение, с которым фактически выполняется служба Windows сервера отчетов. Только для чтения.|  
|[WindowsServiceIdentityConfigured](windowsserviceidentityconfigured-property.md)|Возвращает удостоверение, для выполнения с которым была в последний раз настроена служба Windows сервера отчетов. Только для чтения.|  
  
## <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|[BackupEncryptionKey](configurationsetting-method-backupencryptionkey.md)|Создает резервную копию ключа шифрования для экземпляра. Ключ шифрования хранится в зашифрованном виде под защитой пароля.|  
|[Метод CreateSSLCertificateBinding &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-createsslcertificatebinding.md)|Создает привязку SSL-сертификата.|  
|[DeleteEncryptedInformation](configurationsetting-method-deleteencryptedinformation.md)|Удаляет зашифрованные данные из базы данных сервера отчетов.|  
|[DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md)|Удаляет ключи шифрования из базы данных сервера отчетов.|  
|[GenerateDatabaseCreationScript](configurationsetting-method-generatedatabasecreationscript.md)|Формирует скрипт SQL, который можно использовать для создания базы данных сервера отчетов.|  
|[GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md)|Формирует скрипт SQL, с помощью которого можно предоставить пользователю разрешения для базы данных сервера отчетов.|  
|[GenerateDatabaseUpgradeScript](configurationsetting-method-generatedatabaseupgradescript.md)|Формирует скрипт SQL, который можно использовать для обновления базы данных сервера отчетов.|  
|[Метод GetAdminSiteUrl &#40;WMI&#41;](configurationsetting-method-getadminsiteurl.md)|Возвращает абсолютный URL-адрес веб-сайта центра администрирования.|  
|[GetDatabaseVersionDisplayName](configurationsetting-method-getdatabaseversiondisplayname.md)|Возвращает отображаемое имя для указанной строки версии базы данных сервера отчетов.|  
|[InitializeReportServer](configurationsetting-method-initializereportserver.md)|Инициализирует заданный экземпляр сервера отчетов.|  
|[Метод ListInstalledSharePointVersions &#40;WMI&#41;](configurationsetting-method-listinstalledsharepointversions.md)|Возвращает набор токенов, представляющих версии [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]или [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] , установленного на том же компьютере, что и сервер отчетов.|  
|[Метод ListIPAddresses &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-listipaddresses.md)|Выводит список IP-адресов для компьютера.|  
|[ListReportServersInDatabase](configurationsetting-method-listreportserversindatabase.md)|Возвращает список установленных экземпляров сервера отчетов, присутствующих в базе данных сервера отчетов, независимо от того, имеют ли эти экземпляры доступ к защищенным сведениям.|  
|[Метод ListReservedURLs &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-listreservedurls.md)|Выводит список URL-адресов, зарезервированных для всех приложений на сервере отчетов.|  
|[Метод ListSSLCertificateBindings &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-listsslcertificatebindings.md)|Выводит список привязок SSL-сертификатов, существующих в HTTP.SYS, и привязок, ожидаемых в файле rsreportserver.config.|  
|[Метод ListSSLCertificates &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-listsslcertificates.md)|Выводит список SSL-сертификатов, установленных на компьютере.|  
|[ReencryptSecureInformation](configurationsetting-method-reencryptsecureinformation.md)|Создает новый ключ шифрования и повторно шифрует все защищаемые сведения в базе данных сервера отчетов с этим новым ключом.|  
|[Метод RemoveSSLCertificateBindings &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-removesslcertificatebinding.md)|Удаляет привязку SSL-сертификата.|  
|[RemoveUnattendedExecutionAccount](configurationsetting-method-removeunattendedexecutionaccount.md)|Удаляет учетную запись автоматического выполнения из конфигурации сервера отчетов.|  
|[Метод RemoveURL &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-removeurl.md)|Удаляет URL-адрес, зарезервированный для сервера отчетов.|  
|[Метод ReserveURL &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-reserveurl.md)|Добавляет резервирование URL-адресов для заданного приложения.|  
|[RestoreEncryptionKey](configurationsetting-method-restoreencryptionkey.md)|Повторно применяет заданный ключ шифрования к базе данных сервера отчетов.|  
|[SetDatabaseConnection](configurationsetting-method-setdatabaseconnection.md)|Задает подключение к определенной базе данных сервера отчетов.|  
|[SetDatabaseLogonTimeout](configurationsetting-method-setdatabaselogontimeout.md)|Указывает значение времени ожидания по умолчанию для попыток входа в базу данных сервера отчетов.|  
|[SetDatabaseQueryTimeout](configurationsetting-method-setdatabasequerytimeout.md)|Указывает значение времени ожидания по умолчанию для подключений к базе данных сервера отчетов.|  
|[SetEmailConfiguration](configurationsetting-method-setemailconfiguration.md)|Настраивает модуль доставки электронной почты, используемый сервером отчетов для отправки электронной почты.|  
|[SetSecureConnectionLevel](configurationsetting-method-setsecureconnectionlevel.md)|Задает уровень безопасных соединений для сервера отчетов.|  
|[SetServiceState](configurationsetting-method-setservicestate.md)|Включает и выключает службу Windows и веб-службу сервера отчетов.|  
|[SetUnattendedExecutionAccount](configurationsetting-method-setunattendedexecutionaccount.md)|Задает учетную запись, используемую для автоматического выполнения отчетов.|  
|[Метод SetVirtualDirectory &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md)|Задает виртуальный каталог для приложения.|  
|[SetWindowsServiceIdentity](configurationsetting-method-setwindowsserviceidentity.md)|Обеспечивает выполнение службы Windows сервера отчетов под именем указанного пользователя Windows и предоставляет этой учетной записи разрешения файловой системы, достаточные для работы сервера отчетов.|  
  
## <a name="see-also"></a>См. также  
 [Класс MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
  