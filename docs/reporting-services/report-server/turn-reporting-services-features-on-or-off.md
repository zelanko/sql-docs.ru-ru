---
title: "включать и отключать компоненты служб Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "службы Reporting Services, настройка"
  - "безопасность [службы Reporting Services], стратегии"
ms.assetid: b69db02a-43a7-4fdc-ad9b-438d817a7f83
caps.latest.revision: 10
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 9
---
# включать и отключать компоненты служб Reporting Services
  Неиспользуемые функции сервера отчетов можно отключить в рамках блокирующей стратегии, позволяющей снизить риск атак на рабочий сервер отчетов. В большинстве случаев рекомендуется использовать функции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] параллельно; это позволит использовать все функциональные возможности, предоставляемые службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Однако в зависимости от используемой модели развертывания можно отключить неиспользуемые функции. Например, если вся обработка отчетов производится с использованием операций по расписанию, то можно разрешить только фоновую обработку. Подобным же образом можно ограничиться запуском веб-службы сервера отчетов, если необходимо только интерактивное получение отчетов по требованию.  
  
 В процедурах, приведенных в данном разделе, показывается, как можно отключать функции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме. Настройку функций можно выполнить разными способами, например, напрямую изменив файл `RsReportServer.config` или используя аспект **Настройка контактной зоны для служб Reporting Services** управления на основе политик в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Используйте ссылки, чтобы найти одну или несколько процедур, в которых объясняется, как можно включить или выключить функцию.  
  
-   [веб-служба сервера отчетов](#RSWebSvc)  
  
-   [запланированные события и обработка;](#Sched)  
  
-   [Диспетчер отчетов](#ReportManager)  
  
-   [построитель отчетов](#ReportBuilder)  
  
-   [встроенная безопасность Windows для источников данных для отчетов](#WinIntSec)  
  
##  <a name="RSWebSvc"></a> веб-служба сервера отчетов  
  
#### Включение или выключение веб-службы сервера отчетов методом изменения конфигурации  
  
1.  Откройте файл `RsReportServer.config` в текстовом редакторе. Дополнительные сведения см. в статье [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Для включения веб-службы сервера отчетов установите для свойства **IsWebServiceEnabled** значение **true**.  
  
    ```  
    <IsWebServiceEnabled>true</IsWebServiceEnabled>  
    ```  
  
3.  Для выключения веб-службы сервера отчетов установите для свойства **IsWebServiceEnabled** значение **false**.  
  
    ```  
    <IsWebServiceEnabled>false</IsWebServiceEnabled>  
    ```  
  
4.  Сохраните внесенные изменения и закройте файл.  
  
#### Включение или выключение веб-службы сервера отчетов с использованием среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который следует настроить.  
  
2.  В обозревателе объектов щелкните правой кнопкой узел служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], укажите пункт **Политики** и выберите **Аспекты**.  
  
3.  В списке **Аспект** выберите **Настройка контактной зоны для служб Reporting Services**.  
  
4.  В разделе **Свойства аспекта**можно выполнить следующие действия.  
  
    -   Для включения веб-службы сервера отчетов установите для свойства **WebServiceAndHTTPAccessEnabled** значение **True**.  
  
    -   Для выключения веб-службы сервера отчетов установите для свойства **WebServiceAndHTTPAccessEnabled** значение **False**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="Sched"></a> Запланированные события и доставка  
  
#### Включение или выключение запланированных событий и доставки методом изменения конфигурации  
  
1.  Откройте файл RsReportServer.config в текстовом редакторе. Дополнительные сведения см. в статье [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Чтобы включить запланированные операции по обработке и доставке отчетов, присвойте значение **IsSchedulingService**свойствам **IsNotificationService**, **IsEventService** и **true**:  
  
    ```  
    <IsSchedulingService>true</IsSchedulingService>  
    <IsNotificationService>true</IsNotificationService>  
    <IsEventService>true</IsEventService>  
    ```  
  
3.  Чтобы отключить запланированные операции по обработке и доставке отчетов, присвойте значение **IsSchedulingService**свойствам **IsNotificationService**, **IsEventService** и **false**:  
  
    ```  
    <IsSchedulingService>false</IsSchedulingService>  
    <IsNotificationService>false</IsNotificationService>  
    <IsEventService>false</IsEventService>  
    ```  
  
4.  Сохраните внесенные изменения и закройте файл.  
  
> [!NOTE]  
>  Фоновую обработку нельзя отключить полностью, поскольку она обеспечивает функциональные возможности обслуживания базы данных, необходимые для операций сервера.  
  
#### Включение или отключение запланированных событий и доставки с использованием среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который следует настроить.  
  
2.  В обозревателе объектов щелкните правой кнопкой узел служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], укажите пункт **Политики** и выберите **Аспекты**.  
  
3.  В списке **Аспект** выберите **Настройка контактной зоны для служб Reporting Services**.  
  
4.  В разделе **Свойства аспекта**можно выполнить следующие действия.  
  
    -   Чтобы включить запланированные события и доставку, присвойте свойству **ScheduleEventsAndReportDeliveryEnabled** значение **True**.  
  
    -   Чтобы отключить запланированные события и доставку, присвойте свойству **ScheduleEventsAndReportDeliveryEnabled** значение **False**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Фоновую обработку нельзя отключить полностью, поскольку она обеспечивает функциональные возможности обслуживания базы данных, необходимые для операций сервера.  
  
##  <a name="ReportManager"></a> Диспетчер отчетов  
  
#### Включение или отключение диспетчера отчетов методом изменения конфигурации  
  
1.  Откройте файл RsReportServer.config в текстовом редакторе. Инструкции см. в разделе [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Чтобы включить диспетчер отчетов, присвойте свойству **IsReportManagerEnabled** значение **true**.  
  
    ```  
    <IsReportManagerEnabled>true</IsReportManagerEnabled>  
    ```  
  
3.  Чтобы отключить диспетчер отчетов, присвойте свойству **IsReportManagerEnabled** значение **false**.  
  
    ```  
    <IsReportManagerEnabled>false</IsReportManagerEnabled>  
    ```  
  
4.  Сохраните внесенные изменения и закройте файл.  
  
#### Включение или отключение диспетчера отчетов с использованием среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который следует настроить.  
  
2.  В **обозревателе объектов** щелкните правой кнопкой узел служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], укажите пункт **Политики** и выберите **Аспекты**.  
  
3.  В списке **Аспект** выберите **Настройка контактной зоны для служб Reporting Services**.  
  
4.  В разделе **Свойства аспекта**можно выполнить следующие действия.  
  
    -   Чтобы включить диспетчер отчетов, присвойте свойству **ReportManagerEnabled** значение **True**.  
  
    -   Чтобы отключить диспетчер отчетов, присвойте свойству **ReportManagerEnabled** значение **False**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="ReportBuilder"></a> построитель отчетов  
  
#### Включение или отключение построителя отчетов с использованием среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который следует настроить.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши узел служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства сервера** в области **Выбор страницы**щелкните **Безопасность**.  
  
    -   Чтобы включить построитель отчетов, установите флажок **Разрешить выполнение нерегламентированных отчетов** .  
  
    -   Чтобы отключить построитель отчетов, снимите флажок **Разрешить выполнение нерегламентированных отчетов** .  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="WinIntSec"></a> Встроенная безопасность Windows  
  
#### Включение или отключение встроенной безопасности Windows с использованием среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который следует настроить.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши узел служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства сервера** в области **Выбор страницы**щелкните **Безопасность**.  
  
    -   Чтобы включить встроенную безопасность Windows, установите флажок **Использовать встроенную безопасность Windows для источников данных для отчетов** .  
  
    -   Чтобы отключить встроенную безопасность Windows, снимите флажок **Использовать встроенную безопасность Windows для источников данных для отчетов** .  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## См. также  
 [Диспетчер конфигурации служб Reporting Services (службы Reporting Services в собственном режиме)](http://msdn.microsoft.com/ru-ru/63519ef4-e68a-42fb-9cf7-31228ea4e434)  
  
  