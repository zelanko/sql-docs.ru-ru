---
title: Развертывание веб-части "Средство просмотра отчетов" служб SQL Server Reporting Services на сайте SharePoint | Документы Майкрософт
ms.date: 11/15/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e9b2d920b55e412f3b9fa119db0a7cf893659fca
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52502820"
---
# <a name="deploy-the-sql-server-reporting-services-report-viewer-web-part-on-a-sharepoint-site"></a>Развертывание веб-части "Средство просмотра отчетов" служб SQL Server Reporting Services на сайте SharePoint

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2016-2019](../../includes/ssrs-appliesto-sharepoint-2016-2019.md)] [!INCLUDE[ssrs-appliesto-not-sharepoint-online](../../includes/ssrs-appliesto-not-sharepoint-online.md)]

Веб-часть "Средство просмотра отчетов" — это настраиваемая веб-часть, которую можно использовать для просмотра отчетов служб SQL Server Reporting Services в собственном режиме на сайте SharePoint. Эту веб-часть можно использовать для просмотра, печати и экспорта отчетов на сервере отчетов, а также перемещения по ним. Веб-часть "Средство просмотра отчетов" связана с файлами определения отчетов (RDL), которые обрабатываются сервером отчетов служб SQL Server Reporting Services или Сервером отчетов Power BI. Эту веб-часть нельзя использовать с отчетами Power BI, размещенными на Сервере отчетов Power BI.

Используйте приведенные ниже инструкции, чтобы вручную развернуть пакет решений, который добавляет веб-часть "Средство просмотра отчетов" в среду SharePoint Server 2013 или SharePoint Server 2016. Развертывание решения — необходимый этап настройки веб-части.

**Веб-часть "Средство просмотра отчетов" представляет собой отдельный пакет решения и не связана с режимом интеграции с SharePoint для служб SQL Server Reporting Services.**

## <a name="requirements"></a>Требования

> [!IMPORTANT]
> Начиная с версии 15.X.X.X, установить ReportViewerWebPart можно параллельно с существующими приложениями для устройств, совместно используемых в интегрированном режиме SharePoint в Reporting Services.
> В этом обновлении WSP-решения мы добавили новые файлы. Предыдущее решение должно быть отозвано, а новое — повторно развернуто с помощью командлетов Uninstall-SPSolution и Install-SPSolution, соответственно.
>

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
    Add-SPSolution -LiteralPath "{path to file}\ReportViewerWebPart.wsp"
    ```

    Командлет возвратит имя решения, его идентификатор, а также атрибут Deployed=False. На следующем шаге будет выполнено развертывание решения.

3. Выполните командлет [Install-SPSolution](https://technet.microsoft.com/library/ff607534(v=office.16).aspx), чтобы развернуть решение в ферме.

    **SharePoint 2013**

    ```
    Install-SPSolution -Identity ReportViewerWebPart.wsp -CompatibilityLevel "14,15" -GACDeployment -WebApplication {URL to web application}
    ```

    **SharePoint 2016**

    ```
    Install-SPSolution -Identity ReportViewerWebPart.wsp -GACDeployment -WebApplication {URL to web application}
    ```

## <a name="activate-feature"></a>Активация компонента

1. На сайте SharePoint щелкните значок **шестеренки** в левом верхнем углу и выберите пункт **Параметры сайта**.

    ![Параметры сайта в меню со значком шестеренки.](media/sharepoint-site-settings.png)

    По умолчанию доступ к веб-приложениям SharePoint осуществляется через порт 80. Это означает, что часто к сайту SharePoint можно получить доступ, введя *https://<computer name>*, чтобы открыть корневое семейство веб-сайтов.

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

    По умолчанию доступ к веб-приложениям SharePoint осуществляется через порт 80. Это означает, что часто к сайту SharePoint можно получить доступ, введя *https://<computer name>*, чтобы открыть корневое семейство веб-сайтов.

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

## <a name="troubleshoot"></a>Диагностика

* Ошибка при удалении служб SSRS в том случае, если настроен режим интеграции с SharePoint:

    Install-SPRSService : [A] Microsoft.ReportingServices.SharePoint.SharedService.Service.ReportingWebService cannot be cast to [B]Microsoft.ReportingServices.SharePoint.SharedService.Service.ReportingWebService. Тип A происходит из "Microsoft.ReportingServices.SharePoint.SharedService,Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" в контексте "Default" в расположении "C:\Windows\assembly\GAC_MSIL\Microsoft.Reporting Services.SharePoint.SharedService.dll". Тип B происходит из "Microsoft.ReportingServices.SharePoint.SharedService,Version=12.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" в контексте "Default" в расположении "C:\Windows\assembly\GAC_MSIL\Microsoft.Reporting Services.SharePoint.SharedService.dll".
    
    Решение.
    1. Удаление веб-части средства просмотра отчетов
    2. Удаление служб SSRS
    3. Переустановка веб-части средства просмотра отчетов

* Ошибка при попытке обновить SharePoint в том случае, если настроен режим интеграции с SharePoint:

    Не удалось загрузить файл или сборку "Microsoft.ReportingServices.Alerting.ServiceContract, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" или одну из ее зависимостей. Система не может найти указанный файл. 00000000-0000-0000-0000-000000000000
    
    Решение.
    1. Удаление веб-части средства просмотра отчетов
    2. Удаление служб SSRS
    3. Переустановка веб-части средства просмотра отчетов

## <a name="next-steps"></a>Следующие шаги

После развертывания и активации веб-части "Средство просмотра отчетов" можно добавить ее на страницу SharePoint. Дополнительные сведения см. в разделе [Добавление веб-части "Средство просмотра отчетов" на страницу SharePoint](add-report-viewer-web-part-to-page.md).

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
