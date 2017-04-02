---
title: "Свойства MSReportServer_ConfigurationSetting | Microsoft Docs"
ms.custom: 
  - "force 2/17"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "MSReportServer_ConfigurationSetting Properties"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "поставщик WMI [службы Reporting Services], класс MSReportServer_ConfigurationSetting"
  - "MSReportServer_ConfigurationSetting, класс"
ms.assetid: e75fe1e5-197b-4c65-859b-370821cad003
caps.latest.revision: 48
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 45
---
# Свойства MSReportServer_ConfigurationSetting
  Класс MSReportServer_ConfigurationSetting представляет установочные параметры и параметры времени выполнения для экземпляра сервера отчетов. Эти параметры хранятся в файле конфигурации RSReportServer.config.  
  
## Открытые свойства  
  
|||  
|-|-|  
|[ConnectionPoolSize](../../reporting-services/wmi-provider-library-reference/connectionpoolsize-property-wmi-msreportserver-configurationsetting.md)|Возвращает размер пула соединений, используемого сервером отчетов для связи с экземпляром компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , где размещается база данных сервера отчетов. Только для чтения.|  
|[DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/databaselogonaccount-property-wmi-msreportserver-configurationsetting.md)|Задает учетную запись входа, которую сервер отчетов использует для соединения с экземпляром компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором находится база данных сервера отчетов. Только для чтения.|  
|[DatabaseLogonTimeout](../../reporting-services/wmi-provider-library-reference/databaselogontimeout-property-wmi-msreportserver-configurationsetting.md)|Указывает число секунд ожидания перед тем, как попытка входа в базу данных сервера отчетов признается неуспешной. Только для чтения.|  
|[DatabaseLogonType](../../reporting-services/wmi-provider-library-reference/databaselogontype-property-wmi-msreportserver-configurationsetting.md)|Указывает, использует ли сервер отчетов для доступа к базе данных сервера отчетов учетную запись службы Windows, учетную запись пользователя Windows или имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Только для чтения.|  
|[DatabaseName](../../reporting-services/wmi-provider-library-reference/databasename-property-wmi-msreportserver-configurationsetting.md)|Задает имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в котором размещается база данных сервера отчетов.|  
|[DatabaseQueryTimeout](../../reporting-services/wmi-provider-library-reference/databasequerytimeout-property-wmi-msreportserver-configurationsetting.md)|Задает число секунд, проходящих до истечения времени ожидания команды или ее завершения с ошибкой. Сервер отчетов определяет время для процесса по каталогу SQL Server, а не по источнику данных для отчета.|  
|[DatabaseServerName](../../reporting-services/wmi-provider-library-reference/databaseservername-property-wmi-msreportserver-configurationsetting.md)|Задает имя сервера, на котором установлена база данных сервера отчетов.|  
|[Свойство InstallationID](../../reporting-services/wmi-provider-library-reference/installationid-property-wmi-msreportserver-configurationsetting.md)|Возвращает уникальный идентификатор для определенного экземпляра сервера отчетов.|  
|[InstanceName](../../reporting-services/wmi-provider-library-reference/instancename-property-wmi-msreportserver-configurationsetting.md)|Указывает имя экземпляра сервера отчетов на заданном компьютере.|  
|[IsInitialized](../../reporting-services/wmi-provider-library-reference/isinitialized-property-wmi-msreportserver-configurationsetting.md)|Указывает, инициализирован ли экземпляр сервера отчетов.  Только для чтения.|  
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
  
## См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  