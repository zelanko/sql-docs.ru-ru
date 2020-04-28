---
title: Включение событий служб Reporting Services для журнала трассировки SharePoint (ULS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81110ef6-4289-405c-a931-e7e9f49e69ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1e1e2d9cf44435ad61d81ae1f63e4e616c5e673c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "78177209"
---
# <a name="turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls"></a>Включение событий служб Reporting Services для журнала трассировки SharePoint (ULS)
  Начиная с версии [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]серверы служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint могут записывать события служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в журнал трассировки единой службы ведения журнала SharePoint. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] доступны на странице «Наблюдение» центра администрирования SharePoint.

 В этом разделе.

-   [Общие рекомендации в отношении журнала ULS](#bkmk_general)

-   [Включение и отключение событий служб Reporting Services в категории служб Reporting Services](#bkmk_turnon)

-   [Рекомендуемая конфигурация](#bkmk_recommended)

-   [Чтение записей журнала](#bkmk_readentries)

-   [Список событий служб SQL Server Reporting Services](#bkmk_list)

-   [Просмотр файла журнала с помощью PowerShell](#bkmk_powershell)

-   [Расположение журнала трассировки](#bkmk_trace)

##  <a name="general-uls-log-recommendations"></a><a name="bkmk_general"></a> Общие рекомендации в отношении журнала ULS
 В следующей таблице перечислены категории и уровни событий, которые рекомендуется использовать при наблюдении за средой служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] . При регистрации события каждая запись включает время регистрации, имя процесса и идентификатор потока.

|Категория|Level|Description|
|--------------|-----------|-----------------|
|База данных|Подробный|Регистрирует события, требующие доступа к базе данных.|
|Общие сведения|Подробный|Регистрирует события, требующие доступа к следующим элементам.<br /><br /> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .<br /><br /> Обработчик HTTP-данных средства просмотра отчетов.<br /><br /> Доступ к отчету (RDL-файлы).<br /><br /> Источники данных (RSDS-файлы).<br /><br /> URL-адреса на сайте SharePoint (SMDL-файлы).|
|Office Server General|Исключение|Регистрирует ошибки входа.|
|Топология|Подробный|Регистрирует текущую информацию пользователя.|
|веб-части|Подробный|Регистрирует события, для которых требуется доступ к веб-части средства просмотра отчетов.|

##  <a name="to-turn-on-and-off-reporting-services-events-in-the-reporting-services-category"></a><a name="bkmk_turnon"></a> Включение и отключение событий служб Reporting Services в категории служб Reporting Services

1.  В центре администрирования SharePoint выполните следующие действия.

2.  Выберите **Наблюдение**.

3.  Выберите **Настройка журнала диагностики** в группе **Отчеты** .

4.  Найдите в списке категорий **Службы SQL Server Reporting Services** .

5.  Щелкните значок "плюс" (+), чтобы развернуть подкатегории в разделе **Службы SQL Server Reporting Services**.

6.  Выберите подкатегории, которые будут добавлены в журнал трассировки.

7.  В нижней части списка категорий выберите уровень событий для параметра **Событие наименьшей важности для занесения в журнал трассировки**. Чтобы отключить трассировку выберите **Нет** .

> [!NOTE]
>  Параметр **Событие наименьшей важности для занесения в журнал событий** не поддерживается в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Параметр не обрабатывается.

##  <a name="recommended-configuration"></a><a name="bkmk_recommended"></a> Рекомендуемая конфигурация
 Приведенные ниже параметры ведения журнала рекомендуются в качестве стандартной конфигурации.

-   **HTTP-перенаправитель**

-   **Прокси-сервер клиента SOAP**

-   При наличии неполадок с настройкой добавьте **Страницы настройки**.

 Можно выполнить просмотр всех текущих параметров журнала диагностики фермы с помощью следующего командлета PowerShell:

```powershell
Get-SPDiagnosticConfig
```

##  <a name="reading-the-logs-entries"></a><a name="bkmk_readentries"></a> Чтение записей журнала
 Записи служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в журнале отформатированы следующим образом.

1.  **Продукт: службы SQL Server Reporting Services**

2.  **Категория:** события, связанные с сервером, будут иметь символы Report Server в начале имени. Например, Report Server Alerting Runtime. Эти события также регистрируются в файлах журнала сервера отчета.

3.  **Категория:** события, связанные клиентской веб-частью или полученные от нее, не содержащие символы Report Server. Например, Service Application Proxy (в отличие от Report Server Alerting Runtime). Записи WFE содержат идентификатор CorrelationID; записи сервера его не содержат.

##  <a name="list-of-sql-server-reporting-services-events"></a><a name="bkmk_list"></a> Список событий служб SQL Server Reporting Services
 В следующей таблице приведен список событий в категории служб SQL Server Reporting Services.

|Имя области|Описание или образцы записей|
|---------------|-----------------------------------|
|Страницы настройки||
|HTTP-перенаправитель||
|Обработка в локальном режиме||
|Подготовка локального режима||
|Прокси-сервер клиента SOAP||
|Страницы пользовательского интерфейса||
|Power View|Записи журналов, занесенные в **LogClientTraceEvents** API. Источником этих записей являются клиентские приложения, в том [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]числе, компонент [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] надстройки для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] выпуска Enterprise.<br /><br /> Все записи журнала от API-интерфейса LogClientTraceEvents заносятся в **категорию** SQL Server Reporting Services и в **область** Power View.<br /><br /> Содержание записей, занесенных в область Power View, определяется клиентским приложением.|
|Среда выполнения системы предупреждений сервера отчетов||
|Диспетчер домена приложений сервера отчетов||
|Буферизованный ответ сервера отчетов||
|Кэш сервера отчетов||
|Каталог сервера отчетов||
|Фрагмент данных сервера отчетов||
|Очистка данных сервера отчетов||
|Диспетчер конфигурации сервера отчетов|Образцы записей:<br /><br /> Внутренний URL-адрес сервера отчетов MediumUsing http://localhost:80/ReportServer.<br /><br /> UnexpectedMissing или недопустимый параметр ExtendedProtectionLevel|
|Шифрование сервера отчетов||
|Модуль обработки данных сервера отчетов||
|Опрос базы данных сервера отчетов||
|Значение по умолчанию для сервера отчетов||
|Расширение электронной почты сервера отчетов||
|Модуль подготовки отчетов Excel сервера отчетов||
|Фабрика расширений сервера отчетов||
|Среда выполнения HTTP сервера отчетов||
|Модуль подготовки изображений сервера отчетов||
|Мониторинг памяти сервера отчетов||
|Уведомление сервера отчетов||
|Средства обработки сервера отчетов||
|Поставщик для сервера отчетов||
|Подготовка отчетов сервера отчетов||
|Средство просмотра отчетов сервера отчетов||
|Программа ресурсов сервера отчетов|Образцы записей:<br /><br /> Начальный номер SKU служб MediumReporting Services. Ознакомительная версия<br /><br /> Копия MediumEvaluation: осталось 180 дней|
|Выполняющиеся задания сервера отчетов||
|Выполняющиеся запросы сервера отчетов||
|Расписание сервера отчетов||
|Средства безопасности сервера отчетов||
|Контроллер служб сервера отчетов||
|Сеанс сервера отчетов||
|Подписка сервера отчетов||
|Среда выполнения WCF сервера отчетов||
|Веб-сервер сервера отчетов||
|Прокси-сервер приложения службы||
|Общая служба|Образцы записей:<br /><br /> MediumUpdating ReportingWebServiceApplication<br /><br /> Доступ MediumGranting к базам данных содержимого.<br /><br /> Экземпляры MediumProvisioning для ReportingWebServiceApplication<br /><br /> Изменение учетной записи службы MediumProcessing для ReportingWebServiceApplication<br /><br /> Разрешения базы данных MediumSetting.|

##  <a name="view-a-log-file-with-powershell"></a><a name="bkmk_powershell"></a> Просмотр файла журнала с помощью PowerShell
 ![Содержимое, связанное с PowerShelll](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")PowerShell можно использовать для возвращения списка связанных событий служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] из файла журнала ULS. Введите следующую команду в консоли управления SharePoint 2010, чтобы получить из файла журнала ULS UESQL11SPOINT-20110606-1530.log отфильтрованный список строк, содержащих подстроку **sql server reporting services**:

```powershell
Get-Content -Path "C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\LOGS\UESQL11SPOINT-20110606-1530.log" | Select-String "sql server reporting services"
```

 Также существует множество инструментов, доступных для загрузки, которые позволяют читать журналы ULS. Например, [SharePoint LogViewer](https://sharepointlogviewer.codeplex.com/) или [SharePoint ULS Log Viewer](http://ulsviewer.codeplex.com/workitem/list/basic). Оба доступны в CodePlex.

 Дополнительные сведения о том, как использовать PowerShell для просмотра данных журнала, см. в разделе [Просмотр диагностического журнала (SharePoint Server 2010)](https://technet.microsoft.com/library/ff463595.aspx).

##  <a name="trace-log-location"></a><a name="bkmk_trace"></a>Расположение журнала трассировки
 Файлы журнала трассировки обычно находятся в папке **c:\Program Files\Common files\Microsoft Shared\Web Server Extensions\14\logs** , но этот путь можно проверить или изменить на странице **Журнал диагностики** в центре администрирования SharePoint.

