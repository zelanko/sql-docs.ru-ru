---
title: "Область данных отчета | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- "10039"
- sql13.rtp.rptdesigner.reportdata.f1
- "10435"
helpviewer_keywords:
- Report Data pane
ms.assetid: aa9614a3-12e7-4e17-9de2-fafccd1f5f9d
caps.latest.revision: 28
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a832dfb9d5e5e3fc57519b8f694bd47fa755852e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="report-data-pane"></a>Область данных отчета
  С помощью области **Данные отчета** можно просмотреть определенные в настоящий момент параметры, источники данных, наборы данных, коллекции полей и изображения в отчете. Область «Данные отчета» отображает иерархическое представление элементов, представляющих данные в отчете. Узлы верхнего уровня представляют встроенные поля, параметры, изображения и ссылки источника данных. Чтобы просмотреть элементы данных, раскройте соответствующие узлы. Например, если раскрывается узел источника данных, отображаются наборы данных, определенные для этого источника. Если раскрывается набор данных, отображается набор полей. Чтобы связать данные с элементами отчета на странице отчета, перетащите нужные элементы в область конструктора отчета.  
  
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
 Представляет отдельный набор данных. Набор данных служит родительским узлом для коллекции полей, указанных в запросе и включающих любые вычисляемые поля. Службы Reporting Services поддерживают конструкторы запросов, чтобы помочь пользователям составлять запросы. Дополнительные сведения см. в разделе [наборов данных отчета &#40; Службы SSRS &#41; ](../../reporting-services/report-data/report-datasets-ssrs.md) и [запроса средства проектирования &#40; Службы SSRS &#41; ](../../reporting-services/report-data/query-design-tools-ssrs.md).  
  
## <a name="see-also"></a>См. также:  
 [Коллекция полей набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Панель группировки](../../reporting-services/tools/grouping-pane.md)  
  
  
