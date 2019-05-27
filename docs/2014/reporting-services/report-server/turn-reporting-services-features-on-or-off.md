---
title: Включение и отключение компонентов Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- security [Reporting Services], strategies
ms.assetid: b69db02a-43a7-4fdc-ad9b-438d817a7f83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cf44b6af30d5db32c006c5a7d9b59d1810840d18
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66103190"
---
# <a name="turn-reporting-services-features-on-or-off"></a>Включение и отключение компонентов служб Reporting Services
  Неиспользуемые функции сервера отчетов можно отключить в рамках блокирующей стратегии, позволяющей снизить риск атак на рабочий сервер отчетов. В большинстве случаев рекомендуется использовать функции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] параллельно; это позволит использовать все функциональные возможности, предоставляемые службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Однако в зависимости от используемой модели развертывания можно отключить неиспользуемые функции. Например, если вся обработка отчетов производится с использованием операций по расписанию, то можно разрешить только фоновую обработку. Подобным же образом можно ограничиться запуском веб-службы сервера отчетов, если необходимо только интерактивное получение отчетов по требованию.  
  
 В процедурах, приведенных в данном разделе, показывается, как можно отключать функции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме. Настройку функций можно выполнить разными способами, например, напрямую изменив файл `RsReportServer.config` или используя аспект **Настройка контактной зоны для служб Reporting Services** управления на основе политик в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Используйте ссылки, чтобы найти одну или несколько процедур, в которых объясняется, как можно включить или выключить функцию.  
  
-   [веб-служба сервера отчетов](#RSWebSvc)  
  
-   [запланированные события и обработка;](#Sched)  
  
-   [Диспетчер отчетов](#ReportManager)  
  
-   [построитель отчетов](#ReportBuilder)  
  
-   [встроенная безопасность Windows для источников данных для отчетов](#WinIntSec)  
  
##  <a name="RSWebSvc"></a> Report Server Web Service  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-editing-configuration"></a>Включение или выключение веб-службы сервера отчетов методом изменения конфигурации  
  
1.  Откройте файл `RsReportServer.config` в текстовом редакторе. Дополнительные сведения см. в разделе [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](modify-a-reporting-services-configuration-file-rsreportserver-config.md) в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Для включения веб-службы сервера отчетов установите для свойства `IsWebServiceEnabled` значение `true`.  
  
    ```  
    <IsWebServiceEnabled>true</IsWebServiceEnabled>  
    ```  
  
3.  Для выключения веб-службы сервера отчетов установите для свойства `IsWebServiceEnabled` значение `false`.  
  
    ```  
    <IsWebServiceEnabled>false</IsWebServiceEnabled>  
    ```  
  
4.  Сохраните внесенные изменения и закройте файл.  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-using-sql-server-management-studio"></a>Включение или выключение веб-службы сервера отчетов с использованием среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который следует настроить.  
  
2.  В обозревателе объектов щелкните правой кнопкой узел служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , укажите пункт **Политики**и выберите **Аспекты**.  
  
3.  В списке **Аспект** выберите **Настройка контактной зоны для служб Reporting Services**.  
  
4.  В разделе **Свойства аспекта**можно выполнить следующие действия.  
  
    -   Чтобы включить сервер веб-службы отчетов, присвойте **WebServiceAndHTTPAccessEnabled** для `True`.  
  
    -   Чтобы отключить сервер веб-службы отчетов, присвойте **WebServiceAndHTTPAccessEnabled** для `False`.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="Sched"></a> Запланированные события и доставка  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-editing-configuration"></a>Включение или выключение запланированных событий и доставки методом изменения конфигурации  
  
1.  Откройте файл RsReportServer.config в текстовом редакторе. Дополнительные сведения см. в разделе [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](modify-a-reporting-services-configuration-file-rsreportserver-config.md) в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Чтобы включить запланированные операции по обработке и доставке отчетов, присвойте значение `IsSchedulingService` свойствам `IsNotificationService`, `IsEventService` и `true`:  
  
    ```  
    <IsSchedulingService>true</IsSchedulingService>  
    <IsNotificationService>true</IsNotificationService>  
    <IsEventService>true</IsEventService>  
    ```  
  
3.  Чтобы отключить запланированные операции по обработке и доставке отчетов, присвойте значение `IsSchedulingService` свойствам `IsNotificationService`, `IsEventService` и `false`:  
  
    ```  
    <IsSchedulingService>false</IsSchedulingService>  
    <IsNotificationService>false</IsNotificationService>  
    <IsEventService>false</IsEventService>  
    ```  
  
4.  Сохраните внесенные изменения и закройте файл.  
  
> [!NOTE]  
>  Фоновую обработку нельзя отключить полностью, поскольку она обеспечивает функциональные возможности обслуживания базы данных, необходимые для операций сервера.  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-using-sql-server-management-studio"></a>Включение или отключение запланированных событий и доставки с использованием среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который следует настроить.  
  
2.  В обозревателе объектов щелкните правой кнопкой узел служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , укажите пункт **Политики**и выберите **Аспекты**.  
  
3.  В списке **Аспект** выберите **Настройка контактной зоны для служб Reporting Services**.  
  
4.  В разделе **Свойства аспекта**можно выполнить следующие действия.  
  
    -   Чтобы включить запланированные события и доставку, присвойте **ScheduleEventsAndReportDeliveryEnabled** для `True`.  
  
    -   Чтобы отключить запланированные события и доставку, присвойте **ScheduleEventsAndReportDeliveryEnabled** для `False`.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Фоновую обработку нельзя отключить полностью, поскольку она обеспечивает функциональные возможности обслуживания базы данных, необходимые для операций сервера.  
  
##  <a name="ReportManager"></a> Диспетчер отчетов  
  
#### <a name="to-turn-on-or-off-report-manager-by-editing-configuration"></a>Включение или отключение диспетчера отчетов методом изменения конфигурации  
  
1.  Откройте файл RsReportServer.config в текстовом редакторе. Инструкции см. в разделе [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](modify-a-reporting-services-configuration-file-rsreportserver-config.md) в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Чтобы включить диспетчер отчетов, присвойте свойству `IsReportManagerEnabled` значение `true`.  
  
    ```  
    <IsReportManagerEnabled>true</IsReportManagerEnabled>  
    ```  
  
3.  Чтобы отключить диспетчер отчетов, присвойте свойству `IsReportManagerEnabled` значение `false`.  
  
    ```  
    <IsReportManagerEnabled>false</IsReportManagerEnabled>  
    ```  
  
4.  Сохраните внесенные изменения и закройте файл.  
  
#### <a name="to-turn-on-or-off-report-manager-by-using-sql-server-management-studio"></a>Включение или отключение диспетчера отчетов с использованием среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который следует настроить.  
  
2.  В **обозревателе объектов**щелкните правой кнопкой узел служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , укажите пункт **Политики**и выберите **Аспекты**.  
  
3.  В списке **Аспект** выберите **Настройка контактной зоны для служб Reporting Services**.  
  
4.  В разделе **Свойства аспекта**можно выполнить следующие действия.  
  
    -   Чтобы включить диспетчер отчетов, присвойте **ReportManagerEnabled** для `True`.  
  
    -   Чтобы отключить диспетчер отчетов, задайте **ReportManagerEnabled** для `False`.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="ReportBuilder"></a> построитель отчетов  
  
#### <a name="to-turn-on-or-off-report-builder-by-using-sql-server-management-studio"></a>Включение или отключение построителя отчетов с использованием среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который следует настроить.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши узел служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства сервера** в области **Выбор страницы**щелкните **Безопасность**.  
  
    -   Чтобы включить построитель отчетов, установите флажок **Разрешить выполнение нерегламентированных отчетов** .  
  
    -   Чтобы отключить построитель отчетов, снимите флажок **Разрешить выполнение нерегламентированных отчетов** .  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="WinIntSec"></a> Встроенная безопасность Windows  
  
#### <a name="to-turn-on-or-off-windows-integrated-security-by-using-sql-server-management-studio"></a>Включение или отключение встроенной безопасности Windows с использованием среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который следует настроить.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши узел служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства сервера** в области **Выбор страницы**щелкните **Безопасность**.  
  
    -   Чтобы включить встроенную безопасность Windows, установите флажок **Использовать встроенную безопасность Windows для источников данных для отчетов** .  
  
    -   Чтобы отключить встроенную безопасность Windows, снимите флажок **Использовать встроенную безопасность Windows для источников данных для отчетов** .  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
