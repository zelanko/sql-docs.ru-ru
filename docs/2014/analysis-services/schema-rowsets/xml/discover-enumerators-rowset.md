---
title: Набор строк DISCOVER_ENUMERATORS | Документы Microsoft
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
api_name:
- DISCOVER_ENUMERATORS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_ENUMERATORS rowset
ms.assetid: ddc7b13c-3135-4419-8166-eddd459167da
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2c4eb36f93faba7f32352de41d5c6fde4e0dac2c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192540"
---
# <a name="discoverenumerators-rowset"></a>Набор строк DISCOVER_ENUMERATORS
  Возвращает список имен, типов данных и значений перечисления, поддерживаемых [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщика для конкретного источника данных. Поставщик XMLA публикует все распознаваемые им константы перечисления.  
  
 При вызове метода [Discover](../../xmla/xml-elements-methods-discover.md) метод с `DISCOVER_ENUMERATORS` значения перечисления в [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) элемент, `Discover` возвращает `DISCOVER_ENUMERATORS` набора строк схемы.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Для каждого перечисления имеется несколько элементов, один элемент для каждого значения в перечислении. Набор строк, который представляет каждый перечислитесь, является плоским, а имя перечислителя может повторяться для элементов, принадлежащих одному перечислению.  
  
 `DISCOVER_ENUMERATORS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`EnumName`|`DBTYPE_WSTR`||Имя перечислителя, который содержит набор значений.|  
|`EnumDescription`|`DBTYPE_WSTR`||Локализованное описание перечислителя. Может быть `NULL`.|  
|`EnumType`|`DBTYPE_WSTR`||Тип данных значений перечислителя.|  
|`ElementName`|`DBTYPE_WSTR`||Имя одного из элементов Value в наборе перечислителей.<br /><br /> Пример: `TDP`|  
|`ElementDescription`|`DBTYPE_WSTR`||(Необязательно) Локализованное описание элемента. Может быть `NULL`.|  
|`ElementValue`|`DBTYPE_WSTR`||Значение элемента. Может быть `NULL`.<br /><br /> Пример: `01`|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_ENUMERATORS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`EnumName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  