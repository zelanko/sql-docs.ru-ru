---
title: Набор строк DISCOVER_PROPERTIES | Документы Microsoft
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
- DISCOVER_PROPERTIES
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_PROPERTIES rowset
ms.assetid: 3e2b50e2-3855-4091-8b02-4968e8e57d4c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: af566467345e29362a7b2fdd2c5bda04a35a6dd5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180366"
---
# <a name="discoverproperties-rowset"></a>Набор строк DISCOVER_PROPERTIES
  Возвращает список сведений и значений для стандартных свойств и определяемых поставщиком свойств, которые поддерживаются поставщиком [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) для указанного источника данных. Неподдерживаемые свойства в возвращаемом результирующем наборе не указываются.  
  
 При вызове метода [Discover](../../xmla/xml-elements-methods-discover.md) метод с `DISCOVER_PROPERTIES` значения перечисления в [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) элемент, `Discover` возвращает `DISCOVER_PROPERTIES` строк...  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_PROPERTIES` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Тип|Длина|Описание|  
|-----------------|----------|------------|-----------------|  
|`PropertyName`|`DBTYPE_WSTR`||Имя свойства.|  
|`PropertyDescription`|`DBTYPE_WSTR`||Текст локализованного описания свойства. Может возвращать значение `NULL`.|  
|`PropertyType`|`DBTYPE_WSTR`||Тип данных XML свойства.<br /><br /> Может возвращать значение `NULL`.|  
|`PropertyAccessType`|`DBTYPE_WSTR`||Доступ для свойства. Значением может быть `Read`, `Write` или `ReadWrite`.|  
|`IsRequired`|`DBTYPE_BOOL`||Логическое значение, указывающее, является ли свойство обязательным.<br /><br /> Значение true, если свойство является обязательным. В противном случае — значение false.<br /><br /> Может возвращать значение `NULL`.|  
|`Value`|`DBTYPE_WSTR`||Текущее значение свойства.<br /><br /> Может возвращать значение `NULL`.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_PROPERTIES` может быть ограничен столбцом, указанным в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`PropertyName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  