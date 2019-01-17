---
title: Область данных отчета
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 603229e289c7a5902a7c68b106f079136b249ea0
ms.sourcegitcommit: 2f5773f4bc02bfff4f2924226ac5651eb0c00924
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53553036"
---
# <a name="report-data-pane-in-sql-server-reporting-services-ssrs"></a>Область данных отчета в SQL Server Reporting Services (SSRS)

  С помощью области **Данные отчета** можно просмотреть определенные в настоящий момент параметры, источники данных, наборы данных, коллекции полей и изображения в отчете. Область "Данные отчета" содержит иерархическое представление элементов, представляющих данные в отчете. Узлы верхнего уровня представляют встроенные поля, параметры, изображения и ссылки источника данных. Чтобы просмотреть элементы данных, раскройте соответствующие узлы. Например, если раскрывается узел источника данных, отображаются наборы данных, определенные для этого источника. Если раскрывается набор данных, отображается набор полей. Чтобы связать данные с элементами отчета на странице отчета, перетащите нужные элементы в область конструктора отчета.  
  
## <a name="options"></a>Параметры

 **Встроенные поля**  
 Представляет часто применяемые в отчете поля, предоставляемые службами Reporting Services, например имя отчета или номер страницы. Дополнительные сведения см. в разделе [Встроенные коллекции в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **Параметры**  
 Представляет коллекцию параметров отчета, каждый из которых может быть однозначным или многозначным. Дополнительные сведения см. в разделе [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
 **Изображения**  
 Представляет набор изображений, используемых в отчете. Дополнительные сведения см. в разделе [Изображения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/images-report-builder-and-ssrs.md).  
  
 **Источник данных**  
 Представляет ссылку источника данных на внедренный или общий источник данных. В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]общие источники данных отображаются в папке «Общие источники данных» в обозревателе решений. Источник данных задает один из типов источников данных, поддерживаемых службами Reporting Services. Источник данных служит родительским узлом для коллекции основанных на нем наборов данных. Дополнительные сведения см. в разделе [Подключения к данным, источники данных и строки подключения (построитель отчетов и службы SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
 **Набор данных**  
 Представляет отдельный набор данных. Набор данных служит родительским узлом для коллекции полей, указанных в запросе и включающих любые вычисляемые поля. Службы Reporting Services поддерживают конструкторы запросов, чтобы помочь пользователям составлять запросы. Дополнительные сведения см. в разделах [Наборы данных отчетов (службы SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md) и [Средства проектирования запросов (службы SSRS)](../../reporting-services/report-data/query-design-tools-ssrs.md).  
  
## <a name="next-steps"></a>Следующие шаги

 - [Коллекция полей набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)
 - [Панель группировки](../../reporting-services/tools/grouping-pane.md)