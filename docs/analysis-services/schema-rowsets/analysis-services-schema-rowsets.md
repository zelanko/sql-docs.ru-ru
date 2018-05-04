---
title: Наборы строк схемы в службах аналитики | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
ms.openlocfilehash: 6be6dd4c95d2c44400a202e12179cd1eb5757b2f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="analysis-services-schema-rowsets"></a>Наборы строк схемы служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Наборы строк схемы — это стандартные таблицы, которые содержат сведения об объектах служб Analysis Services и состоянии сервера, включая схему базы данных, активные сеансы, соединения, а также выполняемые сервером команды и задания. Можно запрашивать таблицы набора строк схемы в окне скрипта XML для аналитики в среде SQL Server Management Studio, выполнять к набору строк схемы запрос динамического административного представления или создавать пользовательские приложения, содержащие сведения о наборе строк схемы (например, приложение для составления отчетов, которое получает список доступных измерений, используемый для создания отчета).  
  
> [!NOTE]  
>  При использовании наборов строк схемы XML/A скрипт, данные, которые возвращаются в *результат* параметр [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) структурированы в соответствии с расположениями столбцов набора строк, описанные в этом разделе. [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщик поддерживает наборы строк, необходимых для анализа спецификацией XML. Поставщик XMLA поддерживает также некоторые из наборов строк стандартной схемы для OLE DB, OLE DB для OLAP и OLE DB для поставщиков интеллектуального анализа данных. Поддерживаемые наборы строк описываются в следующих подразделах.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[XML для аналитики наборы строк схемы](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)|Описывает наборы строк XMLA, поддерживаемые поставщиком XMLA.|  
|[Наборы строк схемы OLE DB](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)|Описывает наборы строк схемы OLE DB, поддерживаемые поставщиком XMLA.|  
|[OLE DB для OLAP наборы строк схемы](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)|Описывает наборы строк схемы OLE DB для OLAP, поддерживаемые поставщиком XMLA.|  
|[Наборы строк схемы интеллектуального анализа данных](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)|Описывает наборы строк интеллектуального анализа данных, поддерживаемые поставщиком XMLA.|  
  
## <a name="see-also"></a>См. также:  
 [Доступ к данным многомерной модели & #40; Analysis Services — многомерные данные & #41;](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [Используйте динамические административные представления & #40; динамических административных представлений & #41; для мониторинга служб Analysis Services](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
