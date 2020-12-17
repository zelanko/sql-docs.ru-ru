---
title: Страницы "Параметры сайта" и "Функции сайта" служб Reporting Services (режим интеграции с SharePoint) | Документы Майкрософт
description: Существует ряд пользовательских компонентов уровня сайта, а также компонентов сайта, которыми можно управлять на странице "Параметры сайта SharePoint" для служб Reporting Services в режиме интеграции с SharePoint.
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
monikerRange: '>=sql-server-2016 <=sql-server-2016'
ms.openlocfilehash: feabf5c1a0847983af4a10dea5d4c15a5f51199d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461435"
---
# <a name="reporting-services-site-settings-and-site-features-sharepoint-mode"></a>Страницы "Параметры сайта" и "Функции сайта" служб Reporting Services (режим интеграции с SharePoint)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Службы Reporting Services в режиме интеграции с SharePoint имеют несколько пользовательских компонентов уровня сайта, а также компонент сайта, которым можно управлять со страницы "Параметры сайта SharePoint". Эти параметры распространяются на весь сайт и влияют на все приложения служб Reporting Services. Для просмотра этой страницы требуются разрешения диспетчера содержимого или системного администратора.  

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.

|Параметр сайта|Описание|  
|------------------|-----------------|  
|Параметры сайта служб Reporting Services|Параметры для всего сайта, описанные в этом разделе.|  
|Управление оповещениями об изменении данных|Управление компонентом предупреждения об изменении данных.|  
|Синхронизация файлов сервера отчетов|Компонент уровня сайта, который по умолчанию отключен.<br /><br /> Синхронизирует файлы сервера отчетов (RDL, RSDS, SMDL, RSD, RSC, RDLX) между библиотекой документов SharePoint и сервером отчетов при добавлении или обновлении файлов непосредственно в библиотеке документов.<br /><br /> Дополнительные сведения см. в разделе [активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md).|  
  
## <a name="open-the-reporting-services-site-settings-page"></a>Открытие страницы "Параметры сайта служб Reporting Services"
  
1.  В меню **Действия сайта** сайта SharePoint выберите пункт **Параметры сайта**.  
  
2.  В разделе **Службы Reporting Services** выберите пункт **Параметры сайта служб Reporting Services**.  
  
## <a name="options-for-reporting-services-site-settings"></a>Параметры на странице "Параметры сайта служб Reporting Services"
  
|Параметр|Описание|  
|------------|-----------------|  
|**Разрешить загрузку элемента управления RSClientPrint ActiveX**|Данный элемент управления отображает пользовательское диалоговое окно печати, в котором поддерживаются все стандартные функции: предварительный просмотр, указание отдельных страниц и их диапазонов, поля и ориентация страниц. Дополнительные сведения об этом элементе управления см. в разделе [Using the RSClientPrint Control in Custom Applications](../../reporting-services/report-server-web-service/net-framework/using-the-rsclientprint-control-in-custom-applications.md)|  
|**Разрешить отслеживание удаленных ошибок в локальном режиме**|Показывать или скрывать подробные сообщения об ошибках, возникающих на удаленных компьютерах при работе в локальном режиме. При появлении сообщения об ошибке, аналогичного приведенному далее, может оказаться полезным включение отслеживания удаленных ошибок.<br /><br /> `For more information about this error navigate to the report server on the local server machine or enable remote errors`|  
|**Включить метаданные о специальных возможностях для отчетов**|Включение метаданных о специальных возможностях в выходные данные HTML для отчетов|  
|**Включить точную подгонку визуализации данных под размер для отчетов**|Настройка точной подгонки визуализации данных при использовании внутри табликса. Сюда входят: диаграмма, датчик и карта. Когда этот параметр не установлен, визуализация данных подгоняется приблизительно, при этом может оставаться незанятое место. Этот параметр применяется только к отрисовке в веб-части "Средство просмотра отчетов". Для управления этим поведением при отрисовке на стороне сервера необходимо изменить файл **rsreportserver.config**. Дополнительные сведения см. в следующих разделах:<br /><br /> [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).<br /><br /> [Customize Rendering Extension Parameters in RSReportServer.Config](../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md).<br /><br /> [HTML Device Information Settings](../../reporting-services/html-device-information-settings.md).<br /><br /> Включение этого параметра может негативно сказаться на производительности, поскольку на обработку для определения точного размера может уйти больше времени, чем при приблизительной подгонке.|  
  
## <a name="see-also"></a>См. также раздел

 [Управление приложением службы SharePoint — Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)  
  
  
