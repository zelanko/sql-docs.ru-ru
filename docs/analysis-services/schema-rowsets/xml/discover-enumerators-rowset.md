---
title: Набор строк DISCOVER_ENUMERATORS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4324869aec4da69731f6256148a4767b23ee6804
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="discoverenumerators-rowset"></a>Набор строк DISCOVER_ENUMERATORS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Возвращает список имен, типов данных и значений перечисления, поддерживаемых [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщика для конкретного источника данных. Поставщик XMLA публикует все распознаваемые им константы перечисления.  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_ENUMERATORS** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover** метод возвращает **DISCOVER_ENUMERATORS** набора строк схемы.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Для каждого перечисления имеется несколько элементов, один элемент для каждого значения в перечислении. Набор строк, который представляет каждый перечислитесь, является плоским, а имя перечислителя может повторяться для элементов, принадлежащих одному перечислению.  
  
 **DISCOVER_ENUMERATORS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**Имя_перечисления**|**DBTYPE_WSTR**||Имя перечислителя, который содержит набор значений.|  
|**EnumDescription**|**DBTYPE_WSTR**||Локализованное описание перечислителя. Может быть **NULL**.|  
|**EnumType**|**DBTYPE_WSTR**||Тип данных значений перечислителя.|  
|**ElementName**|**DBTYPE_WSTR**||Имя одного из элементов Value в наборе перечислителей.<br /><br /> Пример: **TDP**|  
|**ElementDescription**|**DBTYPE_WSTR**||(Необязательно) Локализованное описание элемента. Может быть **NULL**.|  
|**ElementValue**|**DBTYPE_WSTR**||Значение элемента. Может быть **NULL**.<br /><br /> Пример: **01**|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **DISCOVER_ENUMERATORS** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**Имя_перечисления**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
