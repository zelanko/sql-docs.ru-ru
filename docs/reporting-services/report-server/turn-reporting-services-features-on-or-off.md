---
title: Включение и отключение компонентов Reporting Services | Документы Майкрософт
ms.date: 06/10/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- security [Reporting Services], strategies
ms.assetid: b69db02a-43a7-4fdc-ad9b-438d817a7f83
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 67945db1fd131b27b37a7e34853987c38fad8d84
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "67140378"
---
# <a name="turn-reporting-services-features-on-or-off"></a>Включение и отключение компонентов служб Reporting Services
  Неиспользуемые функции сервера отчетов можно отключить в рамках блокирующей стратегии, позволяющей снизить риск атак на рабочий сервер отчетов. В большинстве случаев рекомендуется использовать функции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] параллельно; это позволит использовать все функциональные возможности, предоставляемые службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Однако в зависимости от используемой модели развертывания можно отключить неиспользуемые функции. Например, если вся обработка отчетов производится с использованием операций по расписанию, то можно разрешить только фоновую обработку. Подобным же образом можно ограничиться запуском веб-службы сервера отчетов, чтобы только получать отчеты по требованию в интерактивном режиме.  
  
 В процедурах, описанных в этой статье, показывается, как можно отключать функции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме. Настройку функций можно выполнить разными способами, например, напрямую изменив файл `RsReportServer.config` или используя аспект **Настройка контактной зоны для служб Reporting Services** управления на основе политик в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Используйте ссылки, чтобы найти одну или несколько процедур, в которых объясняется, как можно включить или выключить функцию.  
  
-   [Веб-службы сервера отчетов](#RSWebSvc)  
  
-   [запланированные события и обработка;](#Sched)  
  
-   [Веб-портал](#WebPortal)  
  
-   [Встроенная безопасность Windows для источников данных для отчетов](#WinIntSec)  
  
##  <a name="RSWebSvc"></a> Веб-службы сервера отчетов  
  
### <a name="to-turn-on-or-off-the-report-server-web-service-by-editing-configuration"></a>Включение или выключение веб-службы сервера отчетов путем изменения конфигурации  
  
1.  Откройте файл `RsReportServer.config` в текстовом редакторе. Дополнительные сведения см. в статье [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
2.  Чтобы включить веб-службу сервера отчетов, присвойте свойству **IsWebServiceEnabled** значение **true**.  
  
    ```  
    <IsWebServiceEnabled>true</IsWebServiceEnabled>  
    ```  
  
3.  Чтобы выключить веб-службу сервера отчетов, присвойте свойству **IsWebServiceEnabled** значение **false**.  
  
    ```  
    <IsWebServiceEnabled>false</IsWebServiceEnabled>  
    ```  
  
4.  Сохраните внесенные изменения и закройте файл.  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-using-sql-server-management-studio"></a>Включение или выключение веб-службы сервера отчетов с помощью SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который следует настроить.  
  
2.  В обозревателе объектов щелкните правой кнопкой узел служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , укажите пункт **Политики**и выберите **Аспекты**.  
  
3.  В списке **Аспект** выберите **Настройка контактной зоны для служб Reporting Services**.  
  
4.  В разделе **Свойства аспекта**можно выполнить следующие действия.  
  
    -   Для включения веб-службы сервера отчетов установите для свойства **WebServiceAndHTTPAccessEnabled** значение **True**.  
  
    -   Для выключения веб-службы сервера отчетов установите для свойства **WebServiceAndHTTPAccessEnabled** значение **False**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="Sched"></a> Запланированные события и доставка  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-editing-configuration"></a>Включение или выключение запланированных событий и доставки методом изменения конфигурации  
  
1.  Откройте файл RsReportServer.config в текстовом редакторе. Дополнительные сведения см. в статье [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
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
  
##  <a name="WebPortal"></a> Веб-портал
  
Начиная с SQL Server 2016 Reporting Services накопительный пакет обновления 2 веб-портал всегда включен.
  
##  <a name="WinIntSec"></a> Встроенная безопасность Windows  
  
### <a name="to-turn-on-or-off-windows-integrated-security-by-using-sql-server-management-studio"></a>Включение или отключение встроенной безопасности Windows с помощью SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который следует настроить.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши узел служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства сервера** в разделе **Выбор страницы** щелкните **Безопасность**.  
  
    -   Чтобы включить встроенную безопасность Windows, установите флажок **Использовать встроенную безопасность Windows для источников данных для отчетов**.  
  
    -   Чтобы отключить встроенную безопасность Windows, снимите флажок **Использовать встроенную безопасность Windows для источников данных для отчетов**.  
  
4.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также раздел  
[Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../install-windows/reporting-services-configuration-manager-native-mode.md)

 Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
  
