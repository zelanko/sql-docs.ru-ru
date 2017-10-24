---
title: "Наборы строк схемы интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- schema rowsets [Analysis Services]
- rowsets [Analysis Services], data mining
- data mining [Analysis Services], schema rowsets
ms.assetid: bd7d5df5-500b-4159-8467-880e141bc043
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ad8ac453d1d299be98f3cb46496685063fd66576
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="data-mining-schema-rowsets"></a>Data Mining Schema Rowsets
  Сервер, на котором выполняется [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживает следующие наборы строк схемы интеллектуального анализа данных. Чтобы проверить, поддерживает ли определенного поставщика XML/A определенного набора строк, используйте [DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md) набора строк с [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод.  
  
 В [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] к наборам строк схемы интеллектуального анализа данных доступ предоставляется так же, как к таблицам на языке Transact-SQL, в схеме $SYSTEM. Например, следующий запрос применительно к экземпляру служб Analysis Services возвращает список схем, доступных в текущем экземпляре.  
  
```  
SELECT * FROM [$system].[DBSCHEMA_TABLES]  
```  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Набор строк схемы|Description|  
|-------------------|-----------------|  
|[Набор строк DMSCHEMA_MINING_COLUMNS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|Описывает отдельные столбцы всех определенных моделей интеллектуального анализа данных, которые развернуты на сервере.|  
|[Набор строк DMSCHEMA_MINING_FUNCTIONS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)|Описывает прогнозирующие функции и функции интеллектуального анализа данных, которые могут использоваться с каждым алгоритмом интеллектуального анализа данных, установленным на сервере.|  
|[Набор строк DMSCHEMA_MINING_MODEL_CONTENT](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|Обеспечивает возможность просматривать в клиентском приложении содержимое модели интеллектуального анализа данных, полученной в результате обучения.|  
|[Набор строк DMSCHEMA_MINING_MODEL_CONTENT_PMML](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)|Возвращает XML-представление (PMML 2.1) содержимого модели интеллектуального анализа данных.|  
|[Набор строк DMSCHEMA_MINING_MODEL_XML](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)|Возвращает структуру XML (PMML 2.1) модели интеллектуального анализа данных. Это — та же схема, что и DMSCHEMA_MINING_MODEL_PMML, сохраняемая для обеспечения обратной совместимости.|  
|[Набор строк DMSCHEMA_MINING_MODELS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|Перечисляет модели интеллектуального анализа данных, которые развернуты на сервере.|  
|[Набор строк DMSCHEMA_MINING_SERVICE_PARAMETERS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|Предоставляет список параметров, которые могут использоваться для настройки поведения каждого алгоритма интеллектуального анализа данных, установленного на сервере.|  
|[Набор строк DMSCHEMA_MINING_SERVICES](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|Предоставляет описание каждого алгоритма интеллектуального анализа данных, который доступен на сервере.|  
|[Набор строк DMSCHEMA_MINING_STRUCTURE_COLUMNS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|Описывает отдельные столбцы всех структур интеллектуального анализа данных, которые развернуты на сервере.|  
|[Набор строк DMSCHEMA_MINING_STRUCTURES](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|Перечисляет сведения о структурах интеллектуального анализа данных.|  
  
 Все наборы строк схемы, приведенные здесь поддерживаются сервером, на котором выполняется [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services наборы строк схемы](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)   
 [Наборы строк схемы интеллектуального анализа данных &#40; Службы SSAs &#41;](../../../analysis-services/data-mining/data-mining-schema-rowsets-ssas.md)  
  
  

