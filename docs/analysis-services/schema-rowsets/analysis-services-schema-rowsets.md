---
title: "Наборы строк схемы в службах аналитики | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SSAS, data access interfaces
- Analysis Services data access interfaces, schema rowsets
- data access interfaces [Analysis Services]
- XML for Analysis, schema rowsets
- rowsets [Analysis Services], retrieving schema rowsets
- retrieving schema rowsets
- XMLA, schema rowsets
- rowsets [Analysis Services]
- schema rowsets [Analysis Services], retrieving
ms.assetid: 820d4b59-d428-4616-b792-c848e5da407e
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 21cafe5519f9e657a95578aeccbc5773f8eaee97
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="analysis-services-schema-rowsets"></a>Наборы строк схемы служб Analysis Services
  Наборы строк схемы — это стандартные таблицы, которые содержат сведения об объектах служб Analysis Services и состоянии сервера, включая схему базы данных, активные сеансы, соединения, а также выполняемые сервером команды и задания. Можно запрашивать таблицы набора строк схемы в окне скрипта XML для аналитики в среде SQL Server Management Studio, выполнять к набору строк схемы запрос динамического административного представления или создавать пользовательские приложения, содержащие сведения о наборе строк схемы (например, приложение для составления отчетов, которое получает список доступных измерений, используемый для создания отчета).  
  
> [!NOTE]  
>  При использовании наборов строк схемы XML/A скрипт, данные, которые возвращаются в *результат* параметр [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) структурированы в соответствии с расположениями столбцов набора строк, описанный в этом раздел. [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщик поддерживает наборы строк, необходимых для анализа спецификации XML. Поставщик XMLA поддерживает также некоторые из наборов строк стандартной схемы для OLE DB, OLE DB для OLAP и OLE DB для поставщиков интеллектуального анализа данных. Поддерживаемые наборы строк описываются в следующих подразделах.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[XML для аналитики наборы строк схемы](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)|Описывает наборы строк XMLA, поддерживаемые поставщиком XMLA.|  
|[Наборы строк схемы OLE DB](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)|Описывает наборы строк схемы OLE DB, поддерживаемые поставщиком XMLA.|  
|[OLE DB для OLAP наборы строк схемы](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)|Описывает наборы строк схемы OLE DB для OLAP, поддерживаемые поставщиком XMLA.|  
|[Наборы строк схемы интеллектуального анализа данных](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)|Описывает наборы строк интеллектуального анализа данных, поддерживаемые поставщиком XMLA.|  
  
## <a name="see-also"></a>См. также:  
 [Доступ к данным многомерной модели &#40; Analysis Services — многомерные данные &#41;](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [Использование динамических административных представлений для мониторинга служб Analysis Services](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  

