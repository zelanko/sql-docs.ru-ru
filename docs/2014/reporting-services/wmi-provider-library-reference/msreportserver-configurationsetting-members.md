---
title: Члены MSReportServer_ConfigurationSetting | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
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
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4a83bdbce04c9be8813dafa0505d82339666bfb0
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59967020"
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
|[Свойство MachineAccountIdentity (WMI)](configurationsetting-property-machineaccountidentity.md)|Возвращает удостоверение учетной записи компьютера, на котором установлен сервер отчетов.|  
|[PathName](configurationsetting-property-pathname.md)|Задает путь установки для экземпляра сервера отчетов.|  
|[SecureConnectionLevel](configurationsetting-property-secureconnectionlevel.md)|Возвращает уровень безопасного соединения, заданный в файле RSReportServer.config.|  
|[SenderEmailAddress](configurationsetting-property-senderemailaddress.md)|Возвращает адрес, используемый для отправки электронной почты с сервера отчетов. Только для чтения.|  
|[SendUsingSMTPServer](configurationsetting-property-sendusingsmtpserver.md)|Указывает, имеет ли свойство SendUsing в конфигурации электронной почты значение TRUE.|  
|[SMTPServer](configurationsetting-property-smtpserver.md)|Возвращает свойство SMTP-сервера из файла RSReportServer.config. Только для чтения.|  
|[UnattendedExecutionAccount](configurationsetting-property-unattendedexecutionaccount.md)|Указывает учетную запись пользователя для входа, олицетворение которой выполняет сервер отчетов во время автоматического выполнения отчетов. Только для чтения.|  
|[Версия](configurationsetting-property-version.md)|Возвращает версию сервера отчетов.|  
|[Свойство VirtualDirectoryReportManager (WMI MSReportServer_ConfigurationSetting)](configurationsetting-property-virtualdirectoryreportmanager.md)|Возвращает виртуальный каталог для приложения диспетчера отчетов.|  
|[Свойство VirtualDirectoryReportServer (WMI MSReportServer_ConfigurationSetting)](configurationsetting-property-virtualdirectoryreportserver.md)|Возвращает виртуальный каталог для приложения веб-службы сервера отчетов.|  
|[WindowsServiceIdentityActual](configurationsetting-property-windowsserviceidentityactual.md)|Возвращает удостоверение, с которым фактически выполняется служба Windows сервера отчетов. Только для чтения.|  
|[WindowsServiceIdentityConfigured](windowsserviceidentityconfigured-property.md)|Возвращает удостоверение, для выполнения с которым была в последний раз настроена служба Windows сервера отчетов. Только для чтения.|  
  
## <a name="public-methods"></a>Открытые методы  
  
|||  
|-|-|  
|[BackupEncryptionKey](configurationsetting-method-backupencryptionkey.md)|Создает резервную копию ключа шифрования для экземпляра. Ключ шифрования хранится в зашифрованном виде под защитой пароля.|  
|[CreateSSLCertificateBinding Method (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-createsslcertificatebinding.md)|Создает привязку SSL-сертификата.|  
|[DeleteEncryptedInformation](configurationsetting-method-deleteencryptedinformation.md)|Удаляет зашифрованные данные из базы данных сервера отчетов.|  
|[DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md)|Удаляет ключи шифрования из базы данных сервера отчетов.|  
|[GenerateDatabaseCreationScript](configurationsetting-method-generatedatabasecreationscript.md)|Формирует скрипт SQL, который можно использовать для создания базы данных сервера отчетов.|  
|[GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md)|Формирует скрипт SQL, с помощью которого можно предоставить пользователю разрешения для базы данных сервера отчетов.|  
|[GenerateDatabaseUpgradeScript](configurationsetting-method-generatedatabaseupgradescript.md)|Формирует скрипт SQL, который можно использовать для обновления базы данных сервера отчетов.|  
|[Метод GetAdminSiteUrl (WMI)](configurationsetting-method-getadminsiteurl.md)|Возвращает абсолютный URL-адрес веб-сайта центра администрирования.|  
|[GetDatabaseVersionDisplayName](configurationsetting-method-getdatabaseversiondisplayname.md)|Возвращает отображаемое имя для указанной строки версии базы данных сервера отчетов.|  
|[InitializeReportServer](configurationsetting-method-initializereportserver.md)|Инициализирует заданный экземпляр сервера отчетов.|  
|[Метод ListInstalledSharePointVersions (WMI)](configurationsetting-method-listinstalledsharepointversions.md)|Возвращает набор токенов, представляющих версии [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]или [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] , установленного на том же компьютере, что и сервер отчетов.|  
|[Метод ListIPAddresses (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-listipaddresses.md)|Выводит список IP-адресов для компьютера.|  
|[ListReportServersInDatabase](configurationsetting-method-listreportserversindatabase.md)|Возвращает список установленных экземпляров сервера отчетов, присутствующих в базе данных сервера отчетов, независимо от того, имеют ли эти экземпляры доступ к защищенным сведениям.|  
|[Метод ListReservedURLs (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-listreservedurls.md)|Выводит список URL-адресов, зарезервированных для всех приложений на сервере отчетов.|  
|[Метод ListSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-listsslcertificatebindings.md)|Выводит список привязок SSL-сертификатов, существующих в HTTP.SYS, и привязок, ожидаемых в файле rsreportserver.config.|  
|[Метод ListSSLCertificates (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-listsslcertificates.md)|Выводит список SSL-сертификатов, установленных на компьютере.|  
|[ReencryptSecureInformation](configurationsetting-method-reencryptsecureinformation.md)|Создает новый ключ шифрования и повторно шифрует все защищаемые сведения в базе данных сервера отчетов с этим новым ключом.|  
|[Метод RemoveSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-removesslcertificatebinding.md)|Удаляет привязку SSL-сертификата.|  
|[RemoveUnattendedExecutionAccount](configurationsetting-method-removeunattendedexecutionaccount.md)|Удаляет учетную запись автоматического выполнения из конфигурации сервера отчетов.|  
|[Метод RemoveURL (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-removeurl.md)|Удаляет URL-адрес, зарезервированный для сервера отчетов.|  
|[Метод ReserveURL (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-reserveurl.md)|Добавляет резервирование URL-адресов для заданного приложения.|  
|[RestoreEncryptionKey](configurationsetting-method-restoreencryptionkey.md)|Повторно применяет заданный ключ шифрования к базе данных сервера отчетов.|  
|[SetDatabaseConnection](configurationsetting-method-setdatabaseconnection.md)|Задает подключение к определенной базе данных сервера отчетов.|  
|[SetDatabaseLogonTimeout](configurationsetting-method-setdatabaselogontimeout.md)|Указывает значение времени ожидания по умолчанию для попыток входа в базу данных сервера отчетов.|  
|[SetDatabaseQueryTimeout](configurationsetting-method-setdatabasequerytimeout.md)|Указывает значение времени ожидания по умолчанию для подключений к базе данных сервера отчетов.|  
|[SetEmailConfiguration](configurationsetting-method-setemailconfiguration.md)|Настраивает модуль доставки электронной почты, используемый сервером отчетов для отправки электронной почты.|  
|[SetSecureConnectionLevel](configurationsetting-method-setsecureconnectionlevel.md)|Задает уровень безопасных соединений для сервера отчетов.|  
|[SetServiceState](configurationsetting-method-setservicestate.md)|Включает и выключает службу Windows и веб-службу сервера отчетов.|  
|[SetUnattendedExecutionAccount](configurationsetting-method-setunattendedexecutionaccount.md)|Задает учетную запись, используемую для автоматического выполнения отчетов.|  
|[Метод SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setvirtualdirectory.md)|Задает виртуальный каталог для приложения.|  
|[SetWindowsServiceIdentity](configurationsetting-method-setwindowsserviceidentity.md)|Обеспечивает выполнение службы Windows сервера отчетов под именем указанного пользователя Windows и предоставляет этой учетной записи разрешения файловой системы, достаточные для работы сервера отчетов.|  
  
## <a name="see-also"></a>См. также  
 [MSReportServer_ConfigurationSetting Class](msreportserver-configurationsetting-class.md)  
  
  
