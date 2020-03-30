---
title: Область данных отчета
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 24c11796a758d4cbf3b1da35af16565e0e607535
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "74190745"
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
 Представляет ссылку источника данных на внедренный или общий источник данных. В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]общие источники данных отображаются в папке «Общие источники данных» в обозревателе решений. Источник данных задает один из типов источников данных, поддерживаемых службами Reporting Services. Источник данных служит родительским узлом для коллекции основанных на нем наборов данных. См. сведения о [создании строк подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
 **Набор данных**  
 Представляет отдельный набор данных. Набор данных служит родительским узлом для коллекции полей, указанных в запросе и включающих любые вычисляемые поля. Службы Reporting Services поддерживают конструкторы запросов, чтобы помочь пользователям составлять запросы. Дополнительные сведения см. в разделах [Наборы данных отчетов (службы SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md) и [Средства проектирования запросов (службы SSRS)](../../reporting-services/report-data/query-design-tools-ssrs.md).  
  
## <a name="next-steps"></a>Дальнейшие действия

 - [Коллекция полей набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)
 - [Панель группировки](../../reporting-services/tools/grouping-pane.md)