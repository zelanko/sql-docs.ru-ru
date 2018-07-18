---
title: Набор строк DISCOVER_SCHEMA_ROWSETS | Документация Майкрософт
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
- DISCOVER_SCHEMA_ROWSETS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_SCHEMA_ROWSETS rowset
ms.assetid: e5012aa0-6ef8-497f-96c1-2772e2394f62
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa16f7ff677efd8e39367b9e618bdc95d778b405
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220244"
---
# <a name="discoverschemarowsets-rowset"></a>Набор строк DISCOVER_SCHEMA_ROWSETS
  Возвращает имена, ограничения, описание и другие сведения для всех значений перечисления и дополнительных поставщика значений перечисления поддерживаемых [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщика.  
  
 При вызове метода [Discover](../../xmla/xml-elements-methods-discover.md) метод с `DISCOVER_SCHEMA_ROWSETS` значение перечисления в [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) элемент, `Discover` возвращает метод `DISCOVER_SCHEMA_ROWSETS` набора строк.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк DISCOVER_SCHEMA_ROWSETS содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`SchemaName`|`DBTYPE_WSTR`||Имя схемы или запроса. Этот запрос возвращает значения в *RequestTypes* перечисления.|  
|`SchemaGuid`|`DBTYPE_GUID`||Идентификатор GUID схемы.|  
|`Restrictions`|`DBTYPE_HCHAPTER`||Массив ограничений, которые поддерживаются поставщиком.|  
|`Description`|`DBTYPE_WSTR`||Локализованное описание схемы.|  
|`RestrictionsMask`|`DBTYPE_UI8`|||  
  
 Этот набор строк схемы не отсортирован.  
  
 Для поставщика, который поддерживает три ограничения для набора строк схемы DBSCHEMA_MEMBERS, массив `Restrictions` может вернуть следующий результат. Элементы в результате ссылаются на имена столбцов в схеме.  
  
```  
<Restrictions>  
      <CATALOG_NAME type="string" />   
      <SCHEMA_NAME type="string" />   
      <CUBE_NAME type="string" />   
</Restrictions>  
```  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_SCHEMA_ROWSETS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`SchemaName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  
