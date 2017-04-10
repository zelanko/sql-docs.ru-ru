---
title: "Методы MSReportServer_ConfigurationSetting | Microsoft Docs"
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
  - "MSReportServer_ConfigurationSetting Methods"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "поставщик WMI [службы Reporting Services], класс MSReportServer_ConfigurationSetting"
  - "MSReportServer_ConfigurationSetting, класс"
ms.assetid: a08c2476-5b8e-4792-94da-1360fe231c6e
caps.latest.revision: 45
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 45
---
# Методы MSReportServer_ConfigurationSetting
  Класс MSReportServer_ConfigurationSetting поставщика WMI сервера отчетов содержит следующие общие методы.  
  
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
|[Метод ListInstalledSharePointVersions (WMI)](../../reporting-services/wmi-provider-library-reference/listinstalledsharepointversions-method-wmi.md)|Возвращает набор токенов, представляющих версии Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]или [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] , установленных на том же компьютере, что и сервер отчетов.|  
|[Метод ListIPAddresses (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/listipaddresses-method-wmi-msreportserver-configurationsetting.md)|Выводит список IP-адресов для компьютера.|  
|[ListReportServersInDatabase](../../reporting-services/wmi-provider-library-reference/listreportserversindatabase-method-wmi-msreportserver-configurationsetting.md)|Возвращает список установленных экземпляров сервера отчетов, присутствующих в базе данных сервера отчетов, независимо от того, имеют ли эти экземпляры доступ к защищенным сведениям.|  
|[Метод ListReservedURLs (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/listreservedurls-method-wmi-msreportserver-configurationsetting.md)|Выводит список URL-адресов, зарезервированных для всех приложений на сервере отчетов.|  
|[Метод ListSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/listsslcertificatebindings-method-wmi-msreportserver-configurationsetting.md)|Выводит список привязок SSL-сертификатов, существующих в таблице компонента HTTP.SYS, и привязок, ожидаемых в файле RSReportServer.config.|  
|[Метод ListSSLCertificates (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/listsslcertificates-method-wmi-msreportserver-configurationsetting.md)|Выводит список SSL-сертификатов, установленных на компьютере.|  
|[ReencryptSecureInformation](../../reporting-services/wmi-provider-library-reference/reencryptsecureinformation-method-wmi-msreportserver-configurationsetting.md)|Создает новый ключ шифрования и повторно шифрует все защищаемые сведения в базе данных сервера отчетов с этим новым ключом.|  
|[Метод RemoveSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/removesslcertificatebindings-method-wmi-msreportserver-configurationsetting.md)|Удаляет привязку SSL-сертификата.|  
|[RemoveUnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/removeunattendedexecutionaccount-method-wmi-msreportserver-configurationsetting.md)|Удаляет учетную запись автоматического выполнения из конфигурации сервера отчетов.|  
|[Метод RemoveURL (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/removeurl-method-wmi-msreportserver-configurationsetting.md)|Удаляет URL-адрес, зарезервированный для сервера отчетов.|  
|[Метод ReserveURL (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/reserveurl-method-wmi-msreportserver-configurationsetting.md)|Добавляет резервирование URL-адресов для заданного приложения.|  
|[RestoreEncryptionKey](../../reporting-services/wmi-provider-library-reference/restoreencryptionkey-method-wmi-msreportserver-configurationsetting.md)|Повторно применяет заданный ключ шифрования к базе данных сервера отчетов.|  
|[SetDatabaseConnection](../../reporting-services/wmi-provider-library-reference/setdatabaseconnection-method-wmi-msreportserver-configurationsetting.md)|Задает подключение к определенной базе данных сервера отчетов.|  
|[SetDatabaseLogonTimeout](../../reporting-services/wmi-provider-library-reference/setdatabaselogontimeout-method-wmi-msreportserver-configurationsetting.md)|Указывает значение времени ожидания по умолчанию для попыток входа в базу данных сервера отчетов.|  
|[SetDatabaseQueryTimeout](../../reporting-services/wmi-provider-library-reference/setdatabasequerytimeout-method-wmi-msreportserver-configurationsetting.md)|Указывает время ожидания по умолчанию для запросов базы данных сервера отчетов.|  
|[SetEmailConfiguration](../../reporting-services/wmi-provider-library-reference/setemailconfiguration-method-wmi-msreportserver-configurationsetting.md)|Настраивает модуль доставки электронной почты, используемый сервером отчетов для отправки электронной почты.|  
|[SetSecureConnectionLevel](../../reporting-services/wmi-provider-library-reference/setsecureconnectionlevel-method-wmi-msreportserver-configurationsetting.md)|Задает уровень безопасных соединений для сервера отчетов.|  
|[SetServiceState](../../reporting-services/wmi-provider-library-reference/setservicestate-method-wmi-msreportserver-configurationsetting.md)|Включает и отключает службу сервера отчетов.|  
|[SetUnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/setunattendedexecutionaccount-method-wmi-msreportserver-configurationsetting.md)|Задает учетную запись, используемую для автоматического выполнения отчетов.|  
|[Метод SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/setvirtualdirectory-method-wmi-msreportserver-configurationsetting.md)|Задает виртуальный каталог для приложения.|  
|[SetWindowsServiceIdentity](../../reporting-services/wmi-provider-library-reference/setwindowsserviceidentity-method-wmi-msreportserver-configurationsetting.md)|Обеспечивает запуск службы сервера отчетов как заданного пользователя Windows, а также предоставляет этой учетной записи достаточные разрешения, необходимые для работы сервера отчетов.|  
  
## См. также  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  