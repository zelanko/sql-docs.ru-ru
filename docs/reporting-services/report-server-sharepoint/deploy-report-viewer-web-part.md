---
title: "Развертывание веб-части средства просмотра отчетов на сайте SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 09/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a9397f427cac18d0c8bfc663f6bd477b0440b8a3
ms.openlocfilehash: ed93b0fd5161686becb4cca05c005fd281f2c176
ms.contentlocale: ru-ru
ms.lasthandoff: 09/15/2017

---

# <a name="deploy-the-report-viewer-web-part-on-a-sharepoint-site"></a>Развертывание веб-части средства просмотра отчетов на сайте SharePoint

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Веб-части средства просмотра отчетов является собственной веб-части, который может использоваться для просмотра отчетов служб SQL Server Reporting Services (собственный режим) на сайте SharePoint. Веб-части, чтобы просматривать, печатать и экспортировать отчеты на сервере отчетов. Веб-части средства просмотра отчетов связан с файлы определения отчетов (RDL), обрабатываемых на сервере отчетов служб отчетов SQL Server или сервера отчетов Power BI. Эта веб-часть средства просмотра отчетов не может использоваться с отчетами Power BI, размещенных на сервере отчетов Power BI.

Используйте следующие инструкции, чтобы вручную развернуть пакет решения, добавить веб-части средства просмотра отчетов в среде SharePoint Server 2013 или SharePoint Server 2016. При развертывании решения — это обязательный шаг по настройке веб-части.

**Веб-часть средства просмотра отчетов — это пакет решения автономной и не связан с режима интеграции с SharePoint для служб SQL Server Reporting Services.**

## <a name="requirements"></a>Требования

**Поддерживаемые операционные системы:**  
* Windows Server 2008 R2 SP1 и более поздних версий

**Поддерживает версии SharePoint Server:**  
* SharePoint Server 2016
* SharePoint Server 2013

**Поддерживает версии служб Reporting Services:**  
* SQL Server 2008 Reporting Services (Native mode) и более поздних версий.
* Сервер отчетов Power BI

## <a name="download-the-report-viewer-web-part-solution-package"></a>Загрузка пакета средства просмотра отчетов веб-части решения

Веб-часть средства просмотра отчетов доступен в центре загрузки Майкрософт.

[Загрузка пакета решения веб-части средства просмотра отчетов](https://www.microsoft.com/en-us/download/details.aspx?id=55949)

## <a name="deploy-the-farm-solution"></a>Развертывание решения фермы

В этом разделе показано, как выполнить развертывание пакета решения фермы SharePoint. Это задача выполняется один раз.

1. На сервере SharePoint, откройте консоль управления SharePoint с помощью **Запуск от имени администратора** параметр.

2. Запустите [Add-SPSolution](https://technet.microsoft.com/library/ff607552(v=office.16).aspx) для добавления решения фермы.

    ```
    Add-SPSolution –LiteralPath "{path to file}\ReportViewerWebPart.wsp"
    ```

    Командлет возвратит имя решения, его идентификатор, а также атрибут Deployed=False. На следующем шаге будет выполнено развертывание решения.

3. Запустите [Install-SPSolution](https://technet.microsoft.com/library/ff607534(v=office.16).aspx) командлет, чтобы развернуть решение фермы.

    **SharePoint 2013**

    ```
    Install-SPSolution –Identity ReportViewerWebPart.wsp -CompatibilityLevel "14,15" -GACDeployment -WebApplication {URL to web application}
    ```

    **SharePoint 2016**

    ```
    Install-SPSolution –Identity ReportViewerWebPart.wsp -GACDeployment -WebApplication {URL to web application}
    ```

## <a name="activate-feature"></a>Активация функции

1. На сайте SharePoint, выберите **шестеренки** значок в верхнем левом углу и выберите **параметры сайта*.

    ![Параметры сайта, щелкните значок шестеренки.](media/sharepoint-site-settings.png)

    По умолчанию доступ к веб-приложениям SharePoint осуществляется через порт 80. Это означает, что часто доступен сайта SharePoint, введя *http://<computer name> * открыть корневой коллекции сайтов.

3. В **Администрирование семейства сайтов**выберите **компоненты семейства веб-**.

4. Прокрутите вниз страницы, пока не найдете **веб-части средства просмотра отчетов** компонентов.

5. Выберите **Активировать**.

    ![Активация функции веб-части средства просмотра отчетов](media/web-part-activiate-feature.png)

6. Повторите для дополнительных семейств, открыв каждого сайта и выбрав действия сайта.

При необходимости можно также использовать PowerShell для включения этой функции для всех сайтов, с помощью [Enable-SPFeature](https://technet.microsoft.com/library/ff607803.aspx) командлета.

```
Get-SPWebApplication "<web application url>" | Get-SPSite -Limit ALL | 
        ForEach-Object {
            Write-Host "Enabling feature for $($_.URL)"
            Enable-SPFeature -identity "ReportViewerWebPart" -URL $_.URL -ErrorAction Continue
        }
```

## <a name="remove-the-solution"></a>Удаление решения

Несмотря на то, что центр администрирования SharePoint позволяет отзывать решения, необходимо отозвать **ReportViewerWebPart.wsp** файла, если только вы систематически неполадок установки или обновления развертывания.

1. В центре администрирования SharePoint в **параметры системы**выберите **управление решениями фермы**.

2. Выберите **ReportViewerWebPart.wsp**.

3. Выберите отзыв решения.

### <a name="remove-the-web-part-from-site-settings"></a>Удалить веб-части из параметров сайта

Отзыве решения не удаляет веб-части средства просмотра отчетов в списке веб-частей на сайте SharePoint. Чтобы удалить веб-часть средства просмотра отчетов, выполните следующие действия.

1. На сайте SharePoint, выберите **шестеренки** значок в верхнем левом углу и выберите **параметры сайта*.

    ![Параметры сайта, щелкните значок шестеренки.](media/sharepoint-site-settings.png)

    По умолчанию доступ к веб-приложениям SharePoint осуществляется через порт 80. Это означает, что часто доступен сайта SharePoint, введя *http://<computer name> * открыть корневой коллекции сайтов.

2. В разделе **веб-дизайнера**выберите **веб-части**.

3. Выберите **изменить значок** рядом с **ReportViewerNativeMode.dwp**. Могут не отображаться на первой странице результатов.

4. Выберите **удалить элемент**.

    ![Изменение и удаление веб-части средства просмотра отчетов: собственный режим](media/report-viewer-native-mode-edit-delete.png)

Удаление веб-части может выполняться с помощью PowerShell, но не является прямой командой, для него. Пример скрипта см. в разделе [удаление веб-частей из коллекции веб-частей](https://gallery.technet.microsoft.com/office/How-to-delete-Web-Parts-1132701f).

## <a name="next-steps"></a>Следующие шаги

После развертывания веб-части средства просмотра отчетов и активизирован можно добавить веб-части на страницу SharePoint. Дополнительные сведения см. в разделе [веб-части средства просмотра отчетов, добавьте на страницу SharePoint](add-report-viewer-web-part-to-page.md).

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
