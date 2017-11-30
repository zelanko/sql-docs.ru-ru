---
title: "Добавление веб-части \"Средство просмотра отчетов\" служб SQL Server Reporting Services на страницу SharePoint | Документы Майкрософт"
ms.custom: Display a report, from SQL Server Reporting Services or Power BI Report Server, by adding a Report Viewer web part to a SharePoint page.
ms.date: 09/26/2017
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
ms.workload: Inactive
ms.openlocfilehash: e60dfd8a296c84701dfc30588aba49220c130d9f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="add-sql-server-reporting-services-report-viewer-web-part-to-a-sharepoint-page"></a>Добавление веб-части "Средство просмотра отчетов" служб SQL Server Reporting Services на страницу SharePoint

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Чтобы отобразить отчет из служб SQL Server Reporting Services или с Сервера отчетов Power BI, можно добавить веб-часть "Средство просмотра отчетов" на страницу SharePoint.

![Веб-часть "Средство просмотра отчетов" на странице SharePoint](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="prerequisites"></a>Предварительные требования

* Для успешной загрузки отчетов в службе преобразования утверждений в маркеры безопасности Windows (C2WTS) необходимо настроить ограниченное делегирование Kerberos. Дополнительные сведения о настройке C2WTS см. в разделе [Служба Claims to Windows Token Service (c2WTS) и службы Reporting Services](../install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md).

* Веб-часть "Средство просмотра отчетов" должна быть развернута в ферме SharePoint. Сведения о развертывании проекта решения веб-части "Средство просмотра отчетов" см. в разделе [Развертывание веб-части "Средство просмотра отчетов" на сайте SharePoint](deploy-report-viewer-web-part.md).

* Чтобы добавить веб-часть на веб-страницу, необходимо иметь разрешение "Добавление и настройка страниц" на уровне сайта. При использовании параметров безопасности по умолчанию это разрешение предоставлено членам группы **Владельцы** , имеющим уровень разрешений «Полный доступ».

## <a name="add-web-part"></a>Добавление веб-части

1. На сайте SharePoint щелкните значок **шестеренки** в левом верхнем углу и выберите пункт **Добавить страницу**.

    ![Добавление страницы на сайт SharePoint с помощью меню со значком шестеренки.](media/sharepoint-add-a-page.png)

2. Присвойте странице имя и нажмите **Создать**.

3. В конструкторе страниц перейдите на ленте на вкладку **Вставка**. В разделе **Части** выберите **веб-часть**.

    ![Вставьте веб-часть с ленты Office.](media/sharepoint-insert-web-part.png)

4. В разделе **Категории** выберите **SQL Server Reporting Services (собственный режим). В разделе **Части** выберите **Средство просмотра отчетов**. Нажмите кнопку **Добавить**.

    ![Добавьте веб-часть "Средство просмотра отчетов".](media/sharepoint-report-viewer-web-part.png)

    Сначала может возникнуть ошибка. Причина в том, что URL-адрес сервера отчетов по умолчанию имеет значение *http://localhost*, но по этому адресу сервер может быть недоступен.

## <a name="configure-the-report-viewer-web-part"></a>Настройка веб-части "Средство просмотра отчетов"

Чтобы связать веб-часть с определенным отчетом, выполните указанные ниже действия.

1. При редактировании страницы SharePoint щелкните стрелку вниз в правом верхнем углу веб-части и выберите пункт **Изменить веб-часть**.

    ![Пункт "Изменить веб-часть" в раскрывающемся меню веб-части.](media/sharepoint-edit-web-part.png)

2. Введите **URL-адрес сервера отчетов**, где размещается отчет. Он должен выглядеть так: *http://myrsserver/reportserver*.

3. Введите путь и имя отчета, который должен отображаться в веб-части. Он должен выглядеть так: */AdventureWorks Sample Reports/Company Sales*. В этом примере отчет *Company Sales* находится в папке *AdventureWorks Sample Reports*.

4. Если для отчета требуются параметры, после указания URL-адреса сервера отчетов и имени отчета выберите в разделе **Параметры** элемент **Загрузка параметров**.

5. Нажмите кнопку **ОК**, чтобы сохранить изменения, внесенные в конфигурацию веб-части.

6. На ленте Office нажмите кнопку **Сохранить**, чтобы сохранить изменения на странице SharePoint.

![Веб-часть "Средство просмотра отчетов" на странице SharePoint](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="considerations-and-limitations"></a>Рекомендации и ограничения

* Веб-часть "Средство просмотра отчетов" не может использоваться на современных страницах в SharePoint.
* Отчеты Power BI невозможно использовать с веб-частью "Средство просмотра отчетов".
* Если вы не видите веб-часть "Средство просмотра отчетов", которую хотите добавить на страницу, убедитесь в том, что [веб-часть "Средство просмотра отчетов" развернута](deploy-report-viewer-web-part.md).

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
