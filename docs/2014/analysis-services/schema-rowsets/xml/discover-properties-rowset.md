---
title: Набор строк DISCOVER_PROPERTIES | Документация Майкрософт
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bc02dd29ee02ad4d1730a6af72c5df3c3fee1c55
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271840"
---
# <a name="discoverproperties-rowset"></a>Набор строк DISCOVER_PROPERTIES
  Возвращает список сведений и значений для стандартных свойств и определяемых поставщиком свойств, которые поддерживаются поставщиком [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) для указанного источника данных. Неподдерживаемые свойства в возвращаемом результирующем наборе не указываются.  
  
 При вызове метода [Discover](../../xmla/xml-elements-methods-discover.md) метод с `DISCOVER_PROPERTIES` значение перечисления в [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) элемент, `Discover` возвращает метод `DISCOVER_PROPERTIES` набора строк...  
  
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
  
  
