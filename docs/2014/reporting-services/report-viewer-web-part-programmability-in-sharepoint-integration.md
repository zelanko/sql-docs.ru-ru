---
title: Использование программирования веб-части обозревателя в режиме интеграции с SharePoint | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
ms.assetid: 714017b7-1bd6-4950-a3c6-d0df8450a877
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 427acf4413bba023f8ff3c8300cfb7a53a4b0b0e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062164"
---
# <a name="report-viewer-web-part-programmability-in-sharepoint-integration"></a>Использование программирования веб-части обозревателя в интеграции с SharePoint
  Веб-часть средства просмотра отчетов ― это серверный элемент управления `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`, который содержит набор открытых API, позволяющих разработчикам создавать пользовательские приложения SharePoint. Пользователь может создавать веб-части, предоставляющие путь к отчету и параметры для веб-части средства просмотра отчетов с помощью соединений веб-частей. Также можно внедрить веб-часть в пользовательскую страницу веб-части SharePoint и модифицировать ее с помощью открытого API-интерфейса.  
  
## <a name="connecting-to-report-viewer-web-part-with-custom-web-parts"></a>Соединение с веб-частью средства просмотра отчетов с пользовательскими веб-частями  
 Веб-часть средства просмотра отчетов ― это потребитель соединения с веб-частями SharePoint, реализующими интерфейс <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> или `T:Microsoft.SharePoint.WebPartPages.IFilterValues`. Веб-часть <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>, например веб-часть **Документы**, может предоставлять веб-части средства просмотра отчетов путь к отчету, если она помещается на той же странице веб-части, что и веб-часть средства просмотра отчетов. Аналогичным образом `T:Microsoft.SharePoint.WebPartPages.IFilterValues` веб-часть, такие как **текстовый фильтр** или **Фильтр выбора**, может предоставлять параметр отчета для просмотра веб-части отчетов при размещении на той же странице веб-части, так как веб-средство просмотра отчетов Часть.  
  
### <a name="implementing-a-report-path-provider-with-iwebpartrow"></a>Реализация поставщика путей отчетов с интерфейсом IWebPartRow  
 Чтобы указать путь к отчету для веб-части средства просмотра отчетов через соединения веб-части, выполните следующие действия.  
  
1.  Создайте веб-часть, реализующую интерфейс <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>.  
  
2.  Добавьте веб-часть на страницу веб-части, на которой расположена веб-часть средства просмотра отчетов.  
  
3.  Подключите веб-часть к веб-части средства просмотра отчетов в пользовательском интерфейсе проектирования веб-частей.  
  
    > [!NOTE]  
    >  Можно подключить только одну веб-часть <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> к веб-части средства просмотра отчетов одновременно, и нельзя подключить одновременно веб-часть <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> и веб-часть `T:Microsoft.SharePoint.WebPartPages.IFilterValues` к веб-части средства просмотра отчетов.  
  
 Чтобы веб-часть <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> правильно работала с частью `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`, в методе <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A> необходимо сделать следующее:  
  
-   Вызовите метод обратного вызова при помощи объекта <xref:System.Data.DataRowView> в качестве параметра входа.  
  
-   Убедитесь, что объект <xref:System.Data.DataRowView> содержит столбец «DocUrl», содержащий путь к отчету.  
  
    > [!NOTE]  
    >  Веб-часть средства просмотра отчетов в надстройке для [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 также поддерживает получение сведений о пути к отчету через столбец «FileRef».  
  
### <a name="implementing-a-report-parameter-provider-with-ifiltervalues"></a>Реализация поставщика параметров отчета с интерфейсом IFilterValues  
 Веб-часть, реализующая интерфейс `T:Microsoft.SharePoint.WebPartPages.IFilterValues`, может предоставлять одно значение параметра веб-части средства просмотра отчетов. Значение параметра, отправляемое веб-части средства просмотра отчетов, попадает под действие тех же ограничений, которые применяются к параметрам отчета в соответствии с определением отчета, включая тип данных, допустимые значения и т. п.  
  
 Чтобы указать параметр отчета для веб-части средства просмотра отчетов, выполните следующие действия.  
  
1.  Создайте веб-часть, реализующую интерфейс `T:Microsoft.SharePoint.WebPartPages.IFilterValues`.  
  
2.  Добавьте веб-часть на ту же страницу, где расположена веб-часть `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`  
  
3.  Подключите веб-часть `T:Microsoft.SharePoint.WebPartPages.IFilterValues` к веб-части средства просмотра отчетов в пользовательском интерфейсе проектирования веб-частей.  
  
    > [!NOTE]  
    >  Можно подключить одновременно несколько веб-частей `T:Microsoft.SharePoint.WebPartPages.IFilterValues` к веб-части средства просмотра отчетов. Однако нельзя одновременно подключить веб-часть <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> и веб-часть `T:Microsoft.SharePoint.WebPartPages.IFilterValues` к веб-части средства просмотра отчетов.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IFilterValues](https://msdn.microsoft.com/en-us/library/office/microsoft.sharepoint.webpartpages.ifiltervalues\(v=office.15\).aspx)  
  
  
