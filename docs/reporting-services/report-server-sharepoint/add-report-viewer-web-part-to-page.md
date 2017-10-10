---
title: "Добавление веб-части для просмотра отчетов служб отчетов SQL Server на страницу SharePoint | Документы Microsoft"
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
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: fbc68b6ff9f1edf5cf6ee13f6e93a3d2d1a8f834
ms.contentlocale: ru-ru
ms.lasthandoff: 10/06/2017

---

# <a name="add-sql-server-reporting-services-report-viewer-web-part-to-a-sharepoint-page"></a>Добавить на страницу SharePoint веб-часть для просмотра отчетов служб отчетов SQL Server

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Отображение отчета, из SQL Server Reporting Services или сервер отчетов в Power BI, путем добавления веб-части средства просмотра отчетов на страницу SharePoint.

![Отчет на страницу SharePoint веб-часть средства просмотра](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="prerequisites"></a>Предварительные требования

* Для успешной загрузки отчетов служба Claims to Windows Token Service (C2WTS), необходимо настроить для Kerberos ограниченного делегирования. Дополнительные сведения о настройке C2WTS см. в разделе [Claims to Windows Token Service (C2WTS) и службы Reporting Services](../install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md).

* Веб-часть средства просмотра отчетов должны быть развернуты в ферму SharePoint. Сведения по развертыванию решений средства просмотра отчетов веб-части проекта см. в разделе [развертывание веб-части средства просмотра отчетов на сайте SharePoint](deploy-report-viewer-web-part.md).

* Чтобы добавить веб-часть на веб-страницу, необходимо иметь разрешение на добавление и настройка страниц на уровне сайта. При использовании параметров безопасности по умолчанию это разрешение предоставлено членам группы **Владельцы** , имеющим уровень разрешений «Полный доступ».

## <a name="add-web-part"></a>Добавление веб-части

1. На сайте SharePoint, выберите **шестеренки** значок в верхнем левом углу и выберите **Добавление страницы**.

    ![Добавление страницы на сайте sharepoint, щелкните значок шестеренки.](media/sharepoint-add-a-page.png)

2. Присвойте странице имя и выберите **создать**.

3. В конструкторе страницы выберите **вставить** вкладку на ленте. Выберите **веб-части** в **частей** раздела.

    ![Вставьте веб-часть на ленте office.](media/sharepoint-insert-web-part.png)

4. В разделе **категории**выберите ** SQL Server Reporting Services (Native mode). В разделе **частей**выберите **средство просмотра отчетов**. Выберите **добавить**.

    ![Добавление веб-части средства просмотра отчетов.](media/sharepoint-report-viewer-web-part.png)

    Могут возникать с ошибкой. Ошибка: так как URL-адрес сервера отчетов по умолчанию задано значение *http://localhost* и могут быть недоступны в этом расположении.

## <a name="configure-the-report-viewer-web-part"></a>Настройка веб-части средства просмотра отчетов

Чтобы настроить веб-части, чтобы она указывала на определенный отчет, выполните следующие действия.

1. При редактировании страницы SharePoint, щелкните стрелку вниз в правом верхнем углу веб-части и выберите **изменить веб-часть**.

    ![Редактирование веб-страницы web части раскрывающегося списка.](media/sharepoint-edit-web-part.png)

2. Введите **URL-адрес сервера отчетов** для сервера отчетов, где размещается отчет. Это должно выглядеть *http://myrsserver/reportserver*.

3. Введите путь и имя отчета, который будет отображаться в веб-части. Это будет выглядеть аналогично *AdventureWorks Sample Reports/Company Sales*. В этом примере отчета *продажи компании* в папку с именем *образцов отчетов AdventureWorks*.

4. Если отчет требует параметров, после введен URL-адрес сервера отчетов и имя отчета, выберите **Загрузка параметров** в **параметры** раздела.

5. Выберите **ОК** для сохранения изменений в Настройка веб-частей.

6. Выберите **Сохранить**, в ленте Office, чтобы сохранить изменения на страницу SharePoint.

![Отчет на страницу SharePoint веб-часть средства просмотра](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="considerations-and-limitations"></a>Рекомендации и ограничения

* Веб-часть средства просмотра отчетов не может использоваться в современных страниц в SharePoint.
* Нельзя использовать в отчетах Power BI в веб-части средства просмотра отчетов.
* Если вы не видите веб-части средства просмотра отчетов, добавление на страницу, убедитесь, что у вас есть [развертывания веб-части средства просмотра отчетов](deploy-report-viewer-web-part.md).

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
