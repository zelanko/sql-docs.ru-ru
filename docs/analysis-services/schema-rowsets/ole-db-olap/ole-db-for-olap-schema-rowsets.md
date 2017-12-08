---
title: "OLE DB для OLAP наборы строк схемы | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- schema rowsets [Analysis Services], OLE DB for OLAP
- OLE DB for OLAP schema rowsets
- schema rowsets [OLE DB for OLAP]
- rowsets [Analysis Services], OLE DB for OLAP
ms.assetid: 5fad3ecc-407c-4148-862e-ea6119cc7480
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f06af3341034ccc9ddebe1ac6a130be705bdd0cd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="ole-db-for-olap-schema-rowsets"></a>Наборы строк схемы для OLAP (OLE DB)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщик поддерживает следующие OLE DB для OLAP наборы строк схемы.  
  
> [!NOTE]  
>  Чтобы проверить, поддерживает ли конкретный поставщик источника данных набор строк, используйте **DISCOVER_ENUMERATIONS** набора строк с [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод.  
  
 Также можно найти подробные сведения об этих наборах строк путем поиска см. в разделе «Наборы строк схемы OLAP,» в библиотеке MSDN на [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkId=15426).  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Набор строк схемы<sup>1</sup>|Description|  
|-------------------------------|-----------------|  
|[Набор строк DISCOVER_INSTANCES](../../../analysis-services/schema-rowsets/ole-db-olap/discover-instances-rowset.md)|Описывает экземпляры на сервере.|  
|[Набор строк DISCOVER_KEYWORDS &#40; OLE DB для OLAP &#41;](../../../analysis-services/schema-rowsets/ole-db-olap/discover-keywords-rowset-ole-db-for-olap.md)|Перечисляет список слов, зарезервированных поставщиком.|  
|[Набор строк MDSCHEMA_ACTIONS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-actions-rowset.md)|Описывает действия, доступные для клиентского приложения.|  
|[Набор строк MDSCHEMA_CUBES](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-cubes-rowset.md)|Описывает структуру кубов в базе данных.|  
|[Набор строк MDSCHEMA_DIMENSIONS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset.md)|Описывает общие и закрытые измерения в базе данных.|  
|[Набор строк MDSCHEMA_FUNCTIONS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-functions-rowset.md)|Описывает функции, доступные клиентским приложениям, подключенным к базе данных.|  
|[Набор строк MDSCHEMA_HIERARCHIES](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)|Описывает каждую иерархию, содержащуюся в конкретном измерении.|  
|[Набор строк MDSCHEMA_INPUT_DATASOURCES](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)|Описывает источники данных, определенные в базе данных.|  
|[Набор строк MDSCHEMA_KPIS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-kpis-rowset.md)|Описывает ключевые показатели эффективности в базе данных.|  
|[Набор строк MDSCHEMA_LEVELS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-levels-rowset.md)|Описывает каждый уровень в конкретной иерархии.|  
|[Набор строк MDSCHEMA_MEASUREGROUP_DIMENSIONS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md)|Перечисляет измерения группы мер.|  
|[Набор строк MDSCHEMA_MEASUREGROUPS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset.md)|Описывает группы мер в базе данных.|  
|[Набор строк MDSCHEMA_MEASURES](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measures-rowset.md)|Описывает каждую меру в кубе.|  
|[Набор строк MDSCHEMA_MEMBERS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-members-rowset.md)|Описывает элементы в базе данных.|  
|[Набор строк MDSCHEMA_PROPERTIES](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)|Описывает свойства элементов в базе данных.|  
|[Набор строк MDSCHEMA_SETS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-sets-rowset.md)|Описывает любые наборы, определенные на текущий момент в базе данных, в том числе наборы с областью сеанса.|  
  
 <sup>1</sup> все наборы строк схемы, приведенные здесь поддерживаются поставщиком источника данных MSOLAP для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] поставщика XML для Аналитики.  
  
## <a name="see-also"></a>См. также:  
 [Набор строк DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)   
 [Наборы строк схемы служб Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
