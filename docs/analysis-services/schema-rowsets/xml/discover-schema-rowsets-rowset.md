---
title: Набор строк DISCOVER_SCHEMA_ROWSETS | Документы Microsoft
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
ms.topic: reference
apiname:
- DISCOVER_SCHEMA_ROWSETS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_SCHEMA_ROWSETS rowset
ms.assetid: e5012aa0-6ef8-497f-96c1-2772e2394f62
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 73fe1580fb43a090a7df04a43432e5b213e86369
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="discoverschemarowsets-rowset"></a>Набор строк DISCOVER_SCHEMA_ROWSETS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Возвращает имена, ограничения, описание и другие сведения для всех значений перечисления и дополнительных поставщиком значений перечисления поддерживаемых [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщика.  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_SCHEMA_ROWSETS** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover**возвращает **DISCOVER_SCHEMA_ROWSETS** набора строк.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк DISCOVER_SCHEMA_ROWSETS содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**SchemaName**|**DBTYPE_WSTR**||Имя схемы или запроса. Этот запрос возвращает значения в *RequestTypes* перечисления.|  
|**SchemaGuid**|**DBTYPE_GUID**||Идентификатор GUID схемы.|  
|**Ограничения**|**DBTYPE_HCHAPTER**||Массив ограничений, которые поддерживаются поставщиком.|  
|**Описание**|**DBTYPE_WSTR**||Локализованное описание схемы.|  
|**RestrictionsMask**|**DBTYPE_UI8**|||  
  
 Этот набор строк схемы не отсортирован.  
  
 Для поставщика, который поддерживает три ограничения для набора строк схемы DBSCHEMA_MEMBERS **ограничения** массива может вернуть следующий результат. Элементы в результате ссылаются на имена столбцов в схеме.  
  
```  
<Restrictions>  
      <CATALOG_NAME type="string" />   
      <SCHEMA_NAME type="string" />   
      <CUBE_NAME type="string" />   
</Restrictions>  
```  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **DISCOVER_SCHEMA_ROWSETS** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**SchemaName**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
