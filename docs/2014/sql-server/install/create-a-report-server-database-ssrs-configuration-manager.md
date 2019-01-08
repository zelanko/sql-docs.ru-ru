---
title: Создание базы данных сервера отчетов (диспетчер конфигураций служб SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], databases
- report server database
- databases [Reporting Services], creating
ms.assetid: 8a3a6ffe-4001-46be-8548-94532550f6a5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 595b6dcddc49b8f8b4ffb13af9c3d4feaf02f3fc
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52403324"
---
# <a name="create-a-report-server-database--ssrs-configuration-manager"></a>Создание базы данных сервера отчетов (диспетчер конфигурации служб SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **основном режиме** , используют две реляционные базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения метаданных и объектов сервера отчетов. Одна база данных используется как основное хранилище, а вторая — для хранения временных данных. Эти базы данных создаются одновременно и связываются по именам. В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию базы данных именуются `reportserver` и `reportservertempdb`. В совокупности эти две базы данных называются «базой данных сервера отчетов» или «каталогом сервера отчетов».  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **режиме интеграции с SharePoint** , имеют третью базу данных, которая используется для метаданных предупреждений об изменении данных. Эти три базы данных создаются для каждого приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , а в их имена по умолчанию включается идентификатор GUID, представляющий приложение службы. Далее приводятся примеры имен этих трех баз данных, используемых в режиме интеграции с SharePoint.  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370TempDB  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370_Alerting  
  
> [!IMPORTANT]  
>  Выполнять запросы к базе данных сервера отчетов из приложений не рекомендуется, схема базы данных сервера отчетов не предназначена для общего доступа. Структура таблиц в разных версиях может различаться. При создании приложений, которым необходим доступ к базе данных сервера отчетов, всегда используйте API-интерфейсы служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
>   
>  Исключением являются представления журнала выполнения. Дополнительные сведения см. в разделе [журнал выполнения сервера отчетов и представление ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
## <a name="ways-to-create-the-report-server-database"></a>Способы создания базы данных сервера отчетов  
 **Собственный режим.** Создать базу данных сервера отчетов, работающего в собственном режиме, вы можете одним из следующих способов.  
  
-   Автоматически. Если выбран вариант установки с конфигурацией по умолчанию, используйте мастер установки SQL Server. В мастере установки SQL Server это раздел **Установка и настройка** на странице «Параметры установки сервера отчетов». Если выбран параметр **Установить только** , то для создания базы данных необходимо воспользоваться диспетчером конфигурации служб Reporting Services.  
  
-   Вручную. Используйте диспетчер конфигурации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. При использовании удаленного компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] для хранения базы данных следует создавать базу данных сервера отчетов вручную. Дополнительные сведения см. в разделе [Создание базы данных сервера отчетов, работающего в собственном режиме (диспетчер конфигураций служб SSRS)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 **Режим интеграции с SharePoint.** На странице параметров установки сервера отчетов имеется только один вариант для режима интеграции с SharePoint **только установка**. При выборе этого параметра устанавливаются все файлы служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и общая служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Следующий шаг заключается в создании по крайней мере одного приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] одним из следующих способов.  
  
-   Использование центра администрирования SharePoint для создание приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе «Приложение службы» из [Step 3: Создание приложения службы Reporting Services](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_create_serrviceapplication).  
  
-   Создание приложения службы и базы данных сервера отчетов с помощью командлетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] PowerShell. Дополнительные сведения см. в образце для создания приложений служб в разделе [PowerShell cmdlets для режима SharePoint службы Reporting Services](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).  
  
## <a name="database-server-version-requirements"></a>Требования к версии сервера баз данных  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется для размещения баз данных сервера отчетов. Экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] может быть локальным или удаленным экземпляром. Далее перечислены поддерживаемые версии компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , которые можно использовать для размещения баз данных сервера отчетов.  
  
- SQL Server 2014
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
 Для создания базы данных сервера отчетов на удаленном компьютере необходимо настроить соединение через учетную запись пользователя домена или учетную запись службы с сетевым доступом. Если планируется использовать удаленный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то внимательно продумайте, с помощью каких учетных данных сервер отчетов будет подключаться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Настройка подключения к базе данных сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
> [!IMPORTANT]  
>  Сервер отчетов и экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором хранится база данных сервера отчетов, могут находиться в разных доменах. При развертывании в Интернете сервер, как правило, защищают с помощью брандмауэра. При настройке доступа в Интернет на сервере отчетов для защиты соединения при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который защищен брандмауэром и IPSEC, следует использовать учетные данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="database-server-edition-requirements"></a>Требования к выпуску сервера баз данных  
 При создании базы данных сервера отчетов убедитесь в том, что данный выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может быть использован для ее хранения. Дополнительные сведения см. в разделе «Сервера базы данных сервера требования к выпуску отчетов» из [функции, поддерживаемые различными выпусками SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>См. также  
 [Диспетчер конфигурации служб Reporting Services &#40;del&#41;](/sql/2014/sql-server/install/reporting-services-configuration-manager-native-mode)  
  
  
