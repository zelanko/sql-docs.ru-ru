---
title: "Создание базы данных сервера отчетов (диспетчер конфигурации служб SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "серверы отчетов [службы Reporting Services], базы данных"
  - "база данных сервера отчетов"
  - "базы данных [службы Reporting Services], создание"
ms.assetid: 8a3a6ffe-4001-46be-8548-94532550f6a5
caps.latest.revision: 12
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Создание базы данных сервера отчетов (диспетчер конфигурации служб SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **основном режиме** , используют две реляционные базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения метаданных и объектов сервера отчетов. Одна база данных используется как основное хранилище, а вторая — для хранения временных данных. Эти базы данных создаются одновременно и связываются по именам. В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию базы данных именуются **reportserver** и **reportservertempdb**. В совокупности эти две базы данных называются «базой данных сервера отчетов» или «каталогом сервера отчетов».  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **режиме интеграции с SharePoint** , имеют третью базу данных, которая используется для метаданных предупреждений об изменении данных. Эти три базы данных создаются для каждого приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , а в их имена по умолчанию включается идентификатор GUID, представляющий приложение службы. Далее приводятся примеры имен этих трех баз данных, используемых в режиме интеграции с SharePoint.  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370TempDB  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370_Alerting  
  
> [!IMPORTANT]  
>  Выполнять запросы к базе данных сервера отчетов из приложений не рекомендуется, схема базы данных сервера отчетов не предназначена для общего доступа. Структура таблиц в разных версиях может различаться. При создании приложений, которым необходим доступ к базе данных сервера отчетов, всегда используйте API-интерфейсы служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
>   
>  Исключением являются представления журнала выполнения. Дополнительные сведения см. в разделе [Журнал выполнения сервера отчетов и представление ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md).  
  
## Способы создания базы данных сервера отчетов  
 **Основной режим.** Создать базу данных сервера отчетов, работающего в основном режиме, вы можете одним из следующих способов:  
  
-   Автоматически. Если выбран вариант установки с конфигурацией по умолчанию, используйте мастер установки SQL Server. В мастере установки SQL Server это раздел **Установка и настройка** на странице «Параметры установки сервера отчетов». Если выбран параметр **Установить только** , то для создания базы данных необходимо воспользоваться диспетчером конфигурации служб Reporting Services.  
  
-   Вручную. Используйте диспетчер конфигурации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . При использовании удаленного компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] для хранения базы данных следует создавать базу данных сервера отчетов вручную. Дополнительные сведения см. в разделе [Создание базы данных сервера отчетов, работающего в собственном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/create-a-native-mode-report-server-database-ssrs-configuration-manager.md).  
  
 **Режим интеграции с SharePoint.** На странице "Параметры установки сервера отчетов" имеется только один вариант для режима интеграции с SharePoint: **Установить только**. При выборе этого параметра устанавливаются все файлы служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и общая служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Следующий шаг заключается в создании по крайней мере одного приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] одним из следующих способов.  
  
-   Использование центра администрирования SharePoint для создание приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в подразделе «Приложение службы» раздела [Step 3: Create a Reporting Services Service Application](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md#bkmk_create_serrviceapplication).  
  
-   Создание приложения службы и базы данных сервера отчетов с помощью командлетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] PowerShell. Дополнительные сведения см. в образце для создания приложений служб в разделе [PowerShell cmdlets для режима SharePoint службы Reporting Services](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).  
  
## Требования к версии сервера баз данных  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется для размещения баз данных сервера отчетов. Экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] может быть локальным или удаленным экземпляром. Далее перечислены поддерживаемые версии компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], которые можно использовать для размещения баз данных сервера отчетов.  
  
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
 Для создания базы данных сервера отчетов на удаленном компьютере необходимо настроить соединение через учетную запись пользователя домена или учетную запись службы с сетевым доступом. Если планируется использовать удаленный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то внимательно продумайте, с помощью каких учетных данных сервер отчетов будет подключаться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Настройка соединения с базой данных сервера отчетов (диспетчер конфигурации SSRS)](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
> [!IMPORTANT]  
>  Сервер отчетов и экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором хранится база данных сервера отчетов, могут находиться в разных доменах. При развертывании в Интернете сервер, как правило, защищают с помощью брандмауэра. При настройке доступа в Интернет на сервере отчетов для защиты соединения при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который защищен брандмауэром и IPSEC, следует использовать учетные данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Требования к выпуску сервера баз данных  
 При создании базы данных сервера отчетов убедитесь в том, что данный выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может быть использован для ее хранения. Дополнительные сведения см. в подразделе "Требования к выпуску серверной базы данных сервера отчетов" раздела [Возможности, поддерживаемые различными выпусками SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
## См. также:  
 [Диспетчер конфигурации служб Reporting Services (службы Reporting Services в собственном режиме)](http://msdn.microsoft.com/ru-ru/63519ef4-e68a-42fb-9cf7-31228ea4e434)  
  
  