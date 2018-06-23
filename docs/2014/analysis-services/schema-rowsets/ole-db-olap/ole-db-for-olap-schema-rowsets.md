---
title: OLE DB для OLAP наборы строк схемы | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- schema rowsets [Analysis Services], OLE DB for OLAP
- OLE DB for OLAP schema rowsets
- schema rowsets [OLE DB for OLAP]
- rowsets [Analysis Services], OLE DB for OLAP
ms.assetid: 5fad3ecc-407c-4148-862e-ea6119cc7480
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 898749e17cb5b85e61a2b2c3a94b7247a7ab219b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100974"
---
# <a name="ole-db-for-olap-schema-rowsets"></a>Наборы строк схемы для OLAP (OLE DB)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщик поддерживает следующие OLE DB для OLAP наборы строк схемы.  
  
> [!NOTE]  
>  Чтобы проверить, поддерживает ли конкретный поставщик источника данных набор строк, используйте `DISCOVER_ENUMERATIONS` набора строк с [Discover](../../xmla/xml-elements-methods-discover.md) метод.  
  
 Также можно найти подробные сведения об этих наборах строк путем поиска см. в разделе «Наборы строк схемы OLAP,» в библиотеке MSDN на [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkId=15426).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Набор строк схемы<sup>1</sup>|Описание|  
|-------------------------------|-----------------|  
|[Набор строк DISCOVER_INSTANCES](discover-instances-rowset.md)|Описывает экземпляры на сервере.|  
|[Набор строк DISCOVER_KEYWORDS &#40;OLE DB для OLAP&#41;](discover-keywords-rowset-ole-db-for-olap.md)|Перечисляет список слов, зарезервированных поставщиком.|  
|[Набор строк MDSCHEMA_ACTIONS](mdschema-actions-rowset.md)|Описывает действия, доступные для клиентского приложения.|  
|[Набор строк MDSCHEMA_CUBES](mdschema-cubes-rowset.md)|Описывает структуру кубов в базе данных.|  
|[Набор строк MDSCHEMA_DIMENSIONS](mdschema-dimensions-rowset.md)|Описывает общие и закрытые измерения в базе данных.|  
|[Набор строк MDSCHEMA_FUNCTIONS](mdschema-functions-rowset.md)|Описывает функции, доступные клиентским приложениям, подключенным к базе данных.|  
|[Набор строк MDSCHEMA_HIERARCHIES](mdschema-hierarchies-rowset.md)|Описывает каждую иерархию, содержащуюся в конкретном измерении.|  
|[Набор строк MDSCHEMA_INPUT_DATASOURCES](mdschema-input-datasources-rowset.md)|Описывает источники данных, определенные в базе данных.|  
|[Набор строк MDSCHEMA_KPIS](mdschema-kpis-rowset.md)|Описывает ключевые показатели эффективности в базе данных.|  
|[Набор строк MDSCHEMA_LEVELS](mdschema-levels-rowset.md)|Описывает каждый уровень в конкретной иерархии.|  
|[Набор строк MDSCHEMA_MEASUREGROUP_DIMENSIONS](mdschema-measuregroup-dimensions-rowset.md)|Перечисляет измерения группы мер.|  
|[Набор строк MDSCHEMA_MEASUREGROUPS](mdschema-measuregroups-rowset.md)|Описывает группы мер в базе данных.|  
|[Набор строк MDSCHEMA_MEASURES](mdschema-measures-rowset.md)|Описывает каждую меру в кубе.|  
|[Набор строк MDSCHEMA_MEMBERS](mdschema-members-rowset.md)|Описывает элементы в базе данных.|  
|[Набор строк MDSCHEMA_PROPERTIES](mdschema-properties-rowset.md)|Описывает свойства элементов в базе данных.|  
|[Набор строк MDSCHEMA_SETS](mdschema-sets-rowset.md)|Описывает любые наборы, определенные на текущий момент в базе данных, в том числе наборы с областью сеанса.|  
  
 <sup>1</sup> все наборы строк схемы, приведенные здесь поддерживаются поставщиком источника данных MSOLAP для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] поставщика XML для Аналитики.  
  
## <a name="see-also"></a>См. также  
 [Набор строк DISCOVER_ENUMERATORS](../xml/discover-enumerators-rowset.md)   
 [Наборы строк схемы служб Analysis Services](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  