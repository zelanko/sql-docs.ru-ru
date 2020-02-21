---
title: Свойства сервера (страница "Дополнительно") | Документация Майкрософт
description: На странице свойств сервера "Дополнительно" можно задавать системные свойства сервера отчетов. Данное средство предоставляет графический пользовательский интерфейс, позволяющий задавать свойства без написания кода.
author: maggiesMSFT
ms.author: maggies
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
ms.date: 01/28/2020
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 6f7a1e8d3d6341da5812bb44726c5bf8186d3b19
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "76831947"
---
# <a name="server-properties-advanced-page---power-bi-report-server--reporting-services"></a>Свойства сервера (страница "Дополнительно") — Сервер отчетов Power BI и Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

На этой странице можно задавать системные свойства сервера отчетов. Установить системные свойства можно несколькими способами. Данное средство предоставляет графический пользовательский интерфейс, позволяющий задавать свойства без необходимости написания кода.

Чтобы открыть эту страницу, в среде SQL Server Management Studio подключитесь к экземпляру сервера отчетов, щелкните его имя правой кнопкой мыши и выберите пункт **Свойства**. Чтобы открыть эту страницу, щелкните **Дополнительно**.

## <a name="options"></a>Параметры

### <a name="accesscontrolallowcredentials"></a>AccessControlAllowCredentials
(Только Сервер отчетов Power BI, Reporting Services 2017 или более поздней версии.) Указывает, может ли быть предоставлен ответ на запрос клиента, если для флага `credentials` установлено значение true. Значение по умолчанию — **false**.

### <a name="accesscontrolallowheaders"></a>AccessControlAllowHeaders
(Только Сервер отчетов Power BI, Reporting Services 2017 или более поздней версии.) Разделенный запятыми список заголовков, которые сервер разрешает при выполнении запроса клиентом. Это свойство может быть пустой строкой. Значение "*" разрешает любые заголовки.

### <a name="accesscontrolallowmethods"></a>AccessControlAllowMethods
(Только Сервер отчетов Power BI, Reporting Services 2017 или более поздней версии.) Разделенный запятыми список методов HTTP, которые сервер разрешает при выполнении запроса клиентом. Значения по умолчанию: GET, PUT, POST, PATCH, DELETE. Значение "*" разрешает любые методы.

### <a name="accesscontrolalloworigin"></a>AccessControlAllowOrigin
(Только Сервер отчетов Power BI, Reporting Services 2017 или более поздней версии.) Разделенный запятыми список источников, которые сервер разрешает при выполнении запроса клиентом. По умолчанию используется пустое значение, которое запрещает все запросы. Значение "*" разрешает любые источники, если учетные данные не заданы. Если учетные данные указаны, необходимо явным образом задать список источников.

### <a name="accesscontrolexposeheaders"></a>AccessControlExposeHeaders
(Только Сервер отчетов Power BI, Reporting Services 2017 или более поздней версии.) Разделенный запятыми список заголовков, которые сервер предоставляет клиентам. Значение по умолчанию — пусто.

### <a name="accesscontrolmaxage"></a>AccessControlMaxAge
(Только Сервер отчетов Power BI, Reporting Services 2017 или более поздней версии.) Задает время в секундах, в течение которого результаты предварительного запроса могут кэшироваться. Значение по умолчанию — 600 (10 минут).

### <a name="allowedresourceextensionsforupload"></a>AllowedResourceExtensionsForUpload
(Только Сервер отчетов Power BI и Reporting Services 2017 или более поздней версии.) Позволяет задать расширения ресурсов, которые можно отправлять на сервер отчетов. Расширения встроенных типов файлов, таких как &ast;.rdl и &ast;.pbix, включать не нужно. Значение по умолчанию — "&ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx".

### <a name="customheaders"></a>CustomHeaders 

(Только Сервер отчетов Power BI от января 2020 г. и служба Reporting Services 2019 или более поздней версии.)

Они задают значения заголовков для всех URL-адресов, соответствующих указанному шаблону регулярного выражения. Пользователи могут задать значения заголовков для выбранных URL-адресов запросов, указав для настраиваемых заголовков допустимый XML-код. Администраторы могут добавлять любое количество заголовков в XML-код. По умолчанию нет пользовательских заголовков, а значение пусто. 

> [!NOTE]
> Слишком большое количество заголовков может повлиять на производительность. 

Рекомендуется проверить конфигурацию топологии, чтобы обеспечить совместимость набора заголовков с развертыванием Reporting Services. Существует также вероятность выбора параметров, вызывающих ошибки в браузерах, если у последних нет соответствующих параметров. Например, не следует добавлять конфигурацию HSTS, если сервер не настроен для использования протокола HTTPS. Несовместимые заголовки могут привести к ошибкам отрисовки в браузере.

#### <a name="customheaders-xml-format"></a>Формат CustomHeaders XML

```xml
<CustomHeaders>
    <Header>
        <Name>{Name of the header}</Name>
        <Pattern>{Regex pattern to match URLs}</Pattern>
        <Value>{Value of the header}</Value>
    </Header>
</CustomHeaders>
```

#### <a name="setting-the-customheaders-property"></a>Установка свойства CustomHeaders

- Вы можете задать его с помощью [SetSystemProperties](https://docs.microsoft.com/dotnet/api/reportservice2010.reportingservice2010.setsystemproperties) (конечная точка SOAP), передав свойство CustomHeaders в качестве параметра.
- Вы можете задать его с помощью [UpdateSystemProperties](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0#/System/UpdateSystemProperties): `/System/Properties` (конечная точка REST), передав свойство CustomHeaders.

#### <a name="example"></a>Пример

В приведенном ниже примере показано, как задать HSTS и другие пользовательские заголовки для URL-адресов с совпадающим шаблоном регулярного выражения.

```xml
<CustomHeaders>
    <Header>
        <Name>Strict-Transport-Security</Name>
        <Pattern>\/Reports\/mobilereport</Pattern>
        <Value>max-age=86400</Value>
    </Header>
    <Header>
        <Name>Embed</Name>
        <Pattern>(.+)(/reports/)(.+)(rs:embed=true)</Pattern>
        <Value>True</Value>
    </Header>
</CustomHeaders>
```

Первый заголовок в приведенном выше коде XML добавляет заголовок `Strict-Transport-Security: max-age=86400` к совпадающим запросам.
- http://adventureworks/Reports/mobilereport/New%20Mobile%20Report  — регулярное выражение сопоставлено и установит заголовок HSTS.
- http://adventureworks/ReportServer/mobilereport/New%20Mobile%20Report  — ошибка соответствия.

Второй заголовок в приведенном выше XML добавляет заголовок `Embed: True` для URL-адреса, содержащего параметр запроса `/reports/` и `rs:embed=true`.
- https://adventureworks/reports/mobilereport/New%20Mobile%20Report?rs:embed=true  — соответствует.
- https://adventureworks/reports/mobilereport/New%20Mobile%20Report?rs:embed=false  — не соответствует.

### <a name="editsessioncachelimit"></a>EditSessionCacheLimit
Указывает количество записей кэша данных, которые могут быть активны в сеансе изменения отчета. По умолчанию количество задается равным 5.  

### <a name="editsessiontimeout"></a>EditSessionTimeout
Указывает время (в секундах) до завершения сеанса изменения отчета. Значение по умолчанию — 7200 секунд (два часа). 

### <a name="enablecdnvisuals"></a>EnableCDNVisuals 
(Только Сервер отчетов Power BI.) При включении отчеты Power BI загружают новейшие сертифицированные пользовательские визуальные элементы из сети доставки содержимого (CDN), размещенной корпорацией Майкрософт. Если у сервера нет доступа к ресурсам Интернета, этот параметр можно отключить. В этом случае пользовательские визуальные элементы загружаются из отчета, опубликованного на сервере. Значение по умолчанию — **True**.  

###  <a name="enableclientprinting"></a>EnableClientPrinting  
Определяет, доступен ли элемент управления ActiveX RSClientPrint для загрузки с сервера отчетов. Возможные значения: **true** и **false**. Значение по умолчанию — **true** Сведения о дополнительных настройках, необходимых для данного элемента управления, см. в разделе [Включение и отключение печати на стороне клиента для служб Reporting Services](../../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  

### <a name="enablecustomvisuals"></a>EnableCustomVisuals 
(Только Сервер отчетов Power BI.) Для включения отображения пользовательских визуальных элементов Power BI. Допустимыми являются значения True и False. *По умолчанию задано значение True.*  

###  <a name="enableexecutionlogging"></a>EnableExecutionLogging  
Указывает, включено ли ведение журнала выполнения отчета. Значение по умолчанию — **true** Дополнительные сведения о журнале выполнения сервера отчетов см. в разделе [Журнал выполнения сервера отчетов и представление ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md).  

### <a name="enableintegratedsecurity"></a>EnableIntegratedSecurity
Определяет, поддерживается ли встроенная система безопасности Windows для соединений с источниками данных для отчетов. Значение по умолчанию равно **True**. Допустимы следующие значения.

|Значения|Описание|
|---------|---------|
|**True**|Встроенная система безопасности Windows включена.|
|**False**|Встроенная система безопасности Windows отключена. Источники данных для отчетов, использующие встроенную систему безопасности Windows, не будут работать.|

### <a name="enableloadreportdefinition"></a>EnableLoadReportDefinition
Этот параметр определяет, могут ли пользователи выполнять незапланированные запросы из отчета построителя отчетов. Настройка этого параметра определяет значение свойства **EnableLoadReportDefinition** на сервере отчетов.  

Если этот флажок снят, свойство имеет значение False. Сервер отчетов не будет формировать отчеты с дополнительной информацией в случае отчетов, где в качестве источника данных используется модель отчета. Любые вызовы метода LoadReportDefinition блокируются.  

Отключение этого параметра снижает угрозу, при которой пользователи-злоумышленники запускают атаку типа «отказ в обслуживании», перегружая сервер отчетов запросами LoadReportDefinition.  

### <a name="enablemyreports"></a>EnableMyReports  
Указывает, разрешено ли применение функции «Мои отчеты». Значение **true** указывает, что применение этой функции разрешено.  

### <a name="enablepowerbireportexportdata"></a>EnablePowerBIReportExportData 
(Только Сервер отчетов Power BI.) Включение экспорта данных Сервера отчетов Power BI из визуальных элементов Power BI. Возможные значения: True, False.  Значение по умолчанию — True. 

### <a name="enableremoteerrors"></a>EnableRemoteErrors
Включает информацию о внешних ошибках (например, информацию об ошибках в источниках данных для отчетов) в сообщения об ошибках, которые были возвращены пользователям, запрашивающим отчеты из удаленных компьютеров. Допустимые значения: **true** и **false**. Значение по умолчанию — **false**. Дополнительные сведения см. в разделе [Включение отслеживания удаленных ошибок (службы Reporting Services)](../../reporting-services/report-server/enable-remote-errors-reporting-services.md).  

### <a name="enabletestconnectiondetailederrors"></a>EnableTestConnectionDetailedErrors
Указывает, следует ли отправлять подробные сообщения об ошибках на клиентские компьютеры при использовании пользователями сервера отчетов для проверки соединения с источниками данных. Значение по умолчанию — **true** Если для параметра устанавливается значение **false**, то отправляются только общие сообщения об ошибке.

###  <a name="executionlogdayskept"></a>ExecutionLogDaysKept  
Количество суток, в течение которых необходимо хранить сведения о выполнении отчетов в журнале выполнения. Для этого свойства допустимы значения от **-1** до **2**,**147**,**483**,**647**. Если значение равно **–1**, записи из таблицы журнала выполнения не удаляются. Значение по умолчанию — **60**.  

> [!NOTE]
> При указании значения **0** *удаляются* все записи из журнала выполнения. Значение **–1** сохраняет записи журнала выполнения и не удаляет их.

### <a name="executionloglevel"></a>ExecutionLogLevel
Задает уровень журнала выполнения. *Значение по умолчанию — "Normal".*

### <a name="externalimagestimeout"></a>ExternalImagesTimeout
Определяет время, в течение которого должен быть получен внешний файл изображения, прежде чем истечет время ожидания соединения. Значение по умолчанию — **600** секунд.  

### <a name="interprocesstimeoutminutes"></a>InterProcessTimeoutMinutes
(Только Сервер отчетов Power BI, Reporting Services 2019 или более поздней версии.) Задает время ожидания процесса в минутах. *Значение по умолчанию — 30.*

### <a name="maxfilesizemb"></a>MaxFileSizeMb
Задает максимальный размер файла отчета в МБ. *Значение по умолчанию — 1000.  Максимум — 2000.*

### <a name="modelcleanupcycleminutes"></a>ModelCleanupCycleMinutes 
(Только Сервер отчетов Power BI.) Задает частоту проверки неиспользуемых моделей в памяти в минутах. *Значение по умолчанию — 15.*

### <a name="modelexpirationminutes"></a>ModelExpirationMinutes 
(Только Сервер отчетов Power BI.) Задает частоту удаления неиспользуемых моделей из памяти в минутах. *Значение по умолчанию — 60.*

###  <a name="myreportsrole"></a>MyReportsRole  
Имя роли, которая использовалась при создании политик безопасности для папок «Мои отчеты» пользователя. Значение по умолчанию — **My Reports Role**.  

### <a name="officeaccesstokenexpirationseconds"></a>OfficeAccessTokenExpirationSeconds 
(Только Сервер отчетов Power BI, Reporting Services 2019 или более поздней версии.) Задает срок действия токена доступа для Office в секундах. *Значение по умолчанию — 60.*

### <a name="officeonlinediscoveryurl"></a>OfficeOnlineDiscoveryURL 
(Только Сервер отчетов Power BI.) Задает адрес экземпляра Office Online Server для просмотра книг Excel.

### <a name="rdlxreporttimetout"></a>RDLXReportTimetout
Отчет RDLX *(отчеты Power View на сервере SharePoint Server)* . Значение времени ожидания обработки отчетов в секундах для всех отчетов, управляемых в пространстве имен сервера отчетов. Это значение может быть переопределено на уровне отчета. Если это свойство задано, сервер отчетов пытается остановить обработку отчета по истечении указанного времени. Допустимые значения: от **-1** до **2** **147** **483** **647**. Если значение равно **-1**, то при обработке отчетов в пространстве имен время ожидания не истекает. Значение по умолчанию — **1800**.

### <a name="requireintune"></a>RequireIntune
(Только Сервер отчетов Power BI, Reporting Services 2017 или более поздней версии.) Для доступа к отчетам организации через мобильное приложение Power BI требуется Intune. *Значение по умолчанию — False.*

### <a name="restrictedresourcemimetypeforupload"></a>RestrictedResourceMimeTypeForUpload
(Только Сервер отчетов Power BI от января 2019 г. и служба Reporting Services 2017 или более поздней версии.) Задает типы MIME, с которыми пользователи не могут отправлять содержимое. Все ресурсы, которые уже хранятся с ограниченным типом MIME, можно скачать в браузере только как application/octet-stream, а не как opened/executed.  По умолчанию в этом списке нет ограниченных элементов, но мы рекомендуем для организаций заполнить его, чтобы обеспечить лучшую безопасность.

### <a name="schedulerefreshtimeoutminutes"></a>ScheduleRefreshTimeoutMinutes 
(Только Сервер отчетов Power BI.) Время ожидания обновления данных в минутах для запланированного обновления отчетов Power BI с внедренными моделями AS. Значение по умолчанию — 120 минут.

### <a name="sessiontimeout"></a>SessionTimeout
Продолжительность времени в секундах, в течение которого сеанс остается активным. Значение по умолчанию — **600**.  

### <a name="sharepointintegratedmode"></a>SharePointIntegratedMode
Это свойство только для чтения определяет режим работы сервера. Значение false означает, что сервер отчетов запущен в собственном режиме.  

### <a name="showdownloadmenu"></a>ShowDownloadMenu
(Только Сервер отчетов Power BI, Reporting Services 2017 или более поздней версии.) Включает меню скачивания для клиентских средств. *Значение по умолчанию — True.*

### <a name="sitename"></a>SiteName
Имя сайта сервера отчетов, отображаемое в заголовке страницы веб-портала. Значение по умолчанию ― [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Значением этого свойства может быть пустая строка. Максимальная длина составляет 8000 символов.  

### <a name="snapshotcompression"></a>SnapshotCompression
Определяет, как происходит сжатие моментальных снимков. Значение по умолчанию — **SQL**. Допустимы следующие значения.

|Значения|Описание|
|---------|---------|
|**SQL**|Моментальные снимки сжимаются при сохранении в базе данных сервера отчетов. Именно таково поведение системы в настоящее время.|
|**None**|Моментальные снимки не сжимаются.|
|**все**|Моментальные снимки сжимаются во всех вариантах хранения, в том числе в базе данных сервера отчетов и в файловой системе.|

### <a name="storedparameterslifetime"></a>StoredParametersLifetime
Максимальное количество суток, в течение которых может храниться хранимый параметр. Допустимые значения: от **-1**и **+1** до **2 147 483 647**. Значение по умолчанию — **180** дней.  

### <a name="storedparametersthreshold"></a>StoredParametersThreshold
Максимальное количество значений параметра, которые могут быть сохранены на сервере отчетов. Допустимые значения: от **-1**и **+1** до **2 147 483 647**. Значение по умолчанию — **1500**.  

### <a name="supportedhyperlinkschemes"></a>SupportedHyperlinkSchemes 
(Только Сервер отчетов Power BI от января 2019 г. и служба Reporting Services 2019 или более поздней версии.) Задает разделенный запятыми список схем URI, которые можно определять для действий гиперссылок, разрешенных к обработке. Чтобы включить все схемы гиперссылок, укажите значение "&ast;". Например, значение "http,https" разрешает гиперссылки на "https://www. contoso.com", но удаляет гиперссылки на "mailto:bill@contoso.com" или "javascript:window.open(‘ www.contoso.com’, ‘_blank’)". Значение по умолчанию — "&ast;".

### <a name="systemreporttimeout"></a>SystemReportTimeout
Применяемое по умолчанию значение времени ожидания обработки отчетов в секундах для всех отчетов, управляемых в пространстве имен сервера отчетов. Это значение может быть переопределено на уровне отчета. Если это свойство задано, сервер отчетов пытается остановить обработку отчета по истечении указанного времени. Допустимые значения: от **-1** до **2** **147** **483** **647**. Если значение равно **-1**, то при обработке отчетов в пространстве имен время ожидания не истекает. Значение по умолчанию — **1800**.  

### <a name="systemsnapshotlimit"></a>SystemSnapshotLimit
Максимальное количество моментальных снимков, которые хранятся для отчета. Допустимые значения: от **-1** до **2** **147** **483** **647**. Значение **-1**указывает на то, что число моментальных снимков не ограничено.  

### <a name="timerinitialdelayseconds"></a>TimerInitialDelaySeconds
(Только Сервер отчетов Power BI, Reporting Services 2017 или более поздней версии.) Задает время начальной задержки в секундах. *Значение по умолчанию — 60.*

### <a name="trustedfileformat"></a>TrustedFileFormat
(Только Сервер отчетов Power BI, Reporting Services 2017 или более поздней версии.) Задает список форматов внешних файлов на портале Reporting Services, которые будут открываться в браузере. Для не указанных форматов внешних файлов в браузере будет открываться диалоговое окно скачивания. Значения по умолчанию — jpg, jpeg, jpe, wav, bmp, pdf, img, gif, json, mp4, web, png.

### <a name="usesessioncookies"></a>UseSessionCookies
Указывает, должны ли использоваться куки-файлы сеанса на сервере отчетов при обмене данными с браузерами клиентов. Значение по умолчанию — **true**  

## <a name="see-also"></a>См. также:

[Установка свойств сервера отчетов (среда Management Studio)](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
[Подключение к серверу отчетов в среде Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
[Свойства Reporting Services](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties.md)   
[Справка F1 по использованию сервера отчетов среде Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
[Свойства системы сервера отчетов](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)   
[Написание скриптов для задач развертывания и администрирования](../../reporting-services/tools/script-deployment-and-administrative-tasks.md)   
[Включение и отключение папки «Мои отчеты»](../../reporting-services/report-server/enable-and-disable-my-reports.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
