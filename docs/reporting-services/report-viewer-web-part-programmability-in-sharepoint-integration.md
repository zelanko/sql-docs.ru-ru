---
title: "Отчет программирования веб-части средства просмотра в режиме интеграции с SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 714017b7-1bd6-4950-a3c6-d0df8450a877
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6e176aafa062c1184ff120cc1e886b9f5e244712
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="report-viewer-web-part-programmability-in-sharepoint-integration"></a>Использование программирования веб-части обозревателя в интеграции с SharePoint
  Веб-часть средства просмотра отчетов — серверный элемент управления, который содержит набор открытых приложений, программные интерфейсы (API), позволяя разработчикам создавать пользовательские приложения SharePoint. Пользователь может создавать веб-части, предоставляющие путь к отчету и параметры для веб-части средства просмотра отчетов с помощью соединений веб-частей. Также можно внедрить веб-часть в пользовательскую страницу веб-части SharePoint и модифицировать ее с помощью открытого API-интерфейса.  
  
## <a name="connecting-to-report-viewer-web-part-with-custom-web-parts"></a>Соединение с веб-частью средства просмотра отчетов с пользовательскими веб-частями  
 Веб-части средства просмотра отчетов ― это потребитель соединения для веб-части SharePoint, который реализует <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> или T:Microsoft.SharePoint.WebPartPages.IFilterValues. <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Веб-часть, таких как **документов** веб-часть можно предоставить путь отчета для просмотра веб-части отчетов при размещении на одной странице веб-частей с веб-части средства просмотра отчетов. Аналогичным образом, T:Microsoft.SharePoint.WebPartPages.IFilterValues веб-часть, таких как **фильтрации** или **Фильтр выбора**, можно указать параметр отчета для просмотра веб-части отчетов при размещении на одной странице веб-частей с веб-части средства просмотра отчетов.  
  
### <a name="implementing-a-report-path-provider-with-iwebpartrow"></a>Реализация поставщика путей отчетов с интерфейсом IWebPartRow  
 Чтобы указать путь к отчету для веб-части средства просмотра отчетов через соединения веб-части, выполните следующие действия.  
  
1.  Создайте веб-часть, реализующую интерфейс <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>.  
  
2.  Добавьте веб-часть на страницу веб-части, на которой расположена веб-часть средства просмотра отчетов.  
  
3.  Подключите веб-часть к веб-части средства просмотра отчетов в пользовательском интерфейсе проектирования веб-частей.  
  
    > [!NOTE]  
    >  Можно подключить только одну <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> веб-части веб-части средства просмотра отчетов на время и нельзя подключить одновременно <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> веб-части и веб-части T:Microsoft.SharePoint.WebPartPages.IFilterValues веб-части средства просмотра отчетов, в то же время.  
  
 Для вашего <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> веб-части для работы с T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart, необходимо выполнить следующие <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A> метод:  
  
-   Вызовите метод обратного вызова при помощи объекта <xref:System.Data.DataRowView> в качестве параметра входа.  
  
-   Убедитесь, что объект <xref:System.Data.DataRowView> содержит столбец «DocUrl», содержащий путь к отчету.  
  
    > [!NOTE]  
    >  Веб-часть средства просмотра отчетов в надстройке для [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 также поддерживает получение сведений о пути к отчету через столбец «FileRef».  
  
### <a name="implementing-a-report-parameter-provider-with-ifiltervalues"></a>Реализация поставщика параметров отчета с интерфейсом IFilterValues  
 Веб-части, который реализует T:Microsoft.SharePoint.WebPartPages.IFilterValues может предоставлять одно значение параметра веб-части средства просмотра отчетов. Значение параметра, отправляемое веб-части средства просмотра отчетов, попадает под действие тех же ограничений, которые применяются к параметрам отчета в соответствии с определением отчета, включая тип данных, допустимые значения и т. п.  
  
 Чтобы указать параметр отчета для веб-части средства просмотра отчетов, выполните следующие действия.  
  
1.  Создание веб-части, который реализует интерфейс T:Microsoft.SharePoint.WebPartPages.IFilterValues.  
  
2.  Добавьте веб-часть на ту же страницу T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart.  
  
3.  Веб-части T:Microsoft.SharePoint.WebPartPages.IFilterValues подключиться к веб-части средства просмотра отчетов в пользовательском интерфейсе проектирования веб сервера веб-части.  
  
    > [!NOTE]  
    >  Одновременно можно подключиться нескольких T:Microsoft.SharePoint.WebPartPages.IFilterValues веб-частей для веб-части средства просмотра отчетов. Тем не менее, нельзя одновременно подключить <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> веб-части и веб-части T:Microsoft.SharePoint.WebPartPages.IFilterValues веб-части средства просмотра отчетов, в то же время.  
  
  
