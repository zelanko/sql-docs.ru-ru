---
title: "Развертывание веб-части \"Средство просмотра отчетов\" служб SQL Server Reporting Services на сайте SharePoint | Документы Майкрософт"
ms.custom: 
ms.date: 10/05/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-server-sharepoint
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f5fd405e91f9ca16caf9345a4a3e8f7852a3ad37
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="deploy-the-sql-server-reporting-services-report-viewer-web-part-on-a-sharepoint-site"></a>Развертывание веб-части "Средство просмотра отчетов" служб SQL Server Reporting Services на сайте SharePoint

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Веб-часть "Средство просмотра отчетов" — это настраиваемая веб-часть, которую можно использовать для просмотра отчетов служб SQL Server Reporting Services в собственном режиме на сайте SharePoint. Эту веб-часть можно использовать для просмотра, печати и экспорта отчетов на сервере отчетов, а также перемещения по ним. Веб-часть "Средство просмотра отчетов" связана с файлами определения отчетов (RDL), которые обрабатываются сервером отчетов служб SQL Server Reporting Services или Сервером отчетов Power BI. Эту веб-часть нельзя использовать с отчетами Power BI, размещенными на Сервере отчетов Power BI.

Используйте приведенные ниже инструкции, чтобы вручную развернуть пакет решений, который добавляет веб-часть "Средство просмотра отчетов" в среду SharePoint Server 2013 или SharePoint Server 2016. Развертывание решения — необходимый этап настройки веб-части.

**Веб-часть "Средство просмотра отчетов" представляет собой отдельный пакет решения и не связана с режимом интеграции с SharePoint для служб SQL Server Reporting Services.**

## <a name="requirements"></a>Требования

**Поддерживаемые версии SharePoint Server:**  
* SharePoint Server 2016
* SharePoint Server 2013

**Поддерживаемые версии Reporting Services:**  
* Службы SQL Server 2008 Reporting Services (собственный режим) и более поздние версии
* Сервер отчетов Power BI

## <a name="download-the-report-viewer-web-part-solution-package"></a>Скачивание пакета решения веб-части "Средство просмотра отчетов"

Веб-часть "Средство просмотра отчетов" доступна в Центре загрузки Майкрософт.

[Скачать пакет решения веб-части "Средство просмотра отчетов"](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="deploy-the-farm-solution"></a>Развертывание решения в ферме

В этом разделе показано, как развернуть пакет решения в ферме SharePoint. Это задача выполняется один раз.

1. На сервере SharePoint откройте командную консоль SharePoint с помощью команды **Запуск от имени администратора**.

2. Выполните командлет [Add-SPSolution](https://technet.microsoft.com/library/ff607552(v=office.16).aspx), чтобы добавить решение в ферму.

    ```
    Add-SPSolution –LiteralPath "{path to file}\ReportViewerWebPart.wsp"
    ```

    Командлет возвратит имя решения, его идентификатор, а также атрибут Deployed=False. На следующем шаге будет выполнено развертывание решения.

3. Выполните командлет [Install-SPSolution](https://technet.microsoft.com/library/ff607534(v=office.16).aspx), чтобы развернуть решение в ферме.

    **SharePoint 2013**

    ```
    Install-SPSolution –Identity ReportViewerWebPart.wsp -CompatibilityLevel "14,15" -GACDeployment -WebApplication {URL to web application}
    ```

    **SharePoint 2016**

    ```
    Install-SPSolution –Identity ReportViewerWebPart.wsp -GACDeployment -WebApplication {URL to web application}
    ```

## <a name="activate-feature"></a>Активация компонента

1. На сайте SharePoint щелкните значок **шестеренки** в левом верхнем углу и выберите пункт **Параметры сайта**.

    ![Параметры сайта в меню со значком шестеренки.](media/sharepoint-site-settings.png)

    По умолчанию доступ к веб-приложениям SharePoint осуществляется через порт 80. Это означает, что часто к сайту SharePoint можно получить доступ, введя *http://<computer name>*, чтобы открыть корневое семейство веб-сайтов.

3. В области **Администрирование семейства веб-сайтов** щелкните ссылку **Возможности семейства веб-сайтов**.

4. Прокрутите страницу вниз до компонента **Веб-часть "Средство просмотра отчетов"**.

5. Выберите **Активировать**.

    ![Активация веб-части "Средство просмотра отчетов"](media/web-part-activiate-feature.png)

6. Повторите эти действия для дополнительных семейств веб-сайтов, открыв каждый из сайтов и щелкнув "Действия сайта".

При необходимости можно также использовать PowerShell для включения этой функции для всех сайтов с помощью командлета [Enable-SPFeature](https://technet.microsoft.com/library/ff607803.aspx).

```
Get-SPWebApplication "<web application url>" | Get-SPSite -Limit ALL | 
        ForEach-Object {
            Write-Host "Enabling feature for $($_.URL)"
            Enable-SPFeature -identity "ReportViewerWebPart" -URL $_.URL -ErrorAction Continue
        }
```

## <a name="remove-the-solution"></a>Удаление решения

Хотя центр администрирования SharePoint позволяет отзывать решения, для файла **ReportViewerWebPart.wsp** это следует делать только тогда, когда систематически проводится диагностика проблем установки или развертывания исправлений.

1. В разделе **Системные параметры** центра администрирования SharePoint выберите **Управление решениями для фермы**.

2. Выберите **ReportViewerWebPart.wsp**.

3. Нажмите "Отозвать решение".

### <a name="remove-the-web-part-from-site-settings"></a>Удаление веб-части из параметров сайта

При отзыве решения веб-часть "Средство просмотра отчетов" не удаляется из списка веб-частей на сайте SharePoint. Чтобы удалить веб-часть "Средство просмотра отчетов", выполните указанные ниже действия.

1. На сайте SharePoint щелкните значок **шестеренки** в левом верхнем углу и выберите пункт **Параметры сайта**.

    ![Параметры сайта в меню со значком шестеренки.](media/sharepoint-site-settings.png)

    По умолчанию доступ к веб-приложениям SharePoint осуществляется через порт 80. Это означает, что часто к сайту SharePoint можно получить доступ, введя *http://<computer name>*, чтобы открыть корневое семейство веб-сайтов.

2. В разделе **Коллекции веб-дизайнера** выберите **веб-части**.

3. Щелкните **значок изменения** рядом с файлом **ReportViewerNativeMode.dwp**. Он может отсутствовать на первой странице результатов.

4. Выберите команду **Удалить элемент**.

    ![Изменение и удаление веб-части "Средство просмотра отчетов" в собственном режиме](media/report-viewer-native-mode-edit-delete.png)

Удалить веб-часть можно с помощью PowerShell, но специальной команды для этого нет. Пример скрипта см. на странице [Удаление веб-частей из коллекции веб-частей](https://gallery.technet.microsoft.com/office/How-to-delete-Web-Parts-1132701f).

## <a name="supported-languages"></a>Поддерживаемые языки

Для веб-части поддерживаются следующие языки:

* английский (en);
* немецкий (de);
* испанский (sp);
* французский (fr);
* итальянский (it);
* японский (ja);
* корейский (ko);
* португальский (pt);
* русский (ru);
* китайский (упрощенное письмо — zh-HANS и zh-CHS);
* китайский (традиционное письмо — zh-HANT и zh-CHT).

## <a name="next-steps"></a>Следующие шаги

После развертывания и активации веб-части "Средство просмотра отчетов" можно добавить ее на страницу SharePoint. Дополнительные сведения см. в разделе [Добавление веб-части "Средство просмотра отчетов" на страницу SharePoint](add-report-viewer-web-part-to-page.md).

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
