---
title: Набор строк DISCOVER_SCHEMA_ROWSETS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7349a3e4877813003212b125de31e7b98343313d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34031921"
---
# <a name="discoverschemarowsets-rowset"></a>Набор строк DISCOVER_SCHEMA_ROWSETS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Возвращает имена, ограничения, описание и другие сведения для всех значений перечисления и дополнительных поставщиком значений перечисления поддерживаемых [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщика.  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_SCHEMA_ROWSETS** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover**возвращает **DISCOVER_SCHEMA_ROWSETS** набора строк.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк DISCOVER_SCHEMA_ROWSETS содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**schemaName**|**DBTYPE_WSTR**||Имя схемы или запроса. Этот запрос возвращает значения в *RequestTypes* перечисления.|  
|**SchemaGuid**|**DBTYPE_GUID**||Идентификатор GUID схемы.|  
|**Ограничения**|**DBTYPE_HCHAPTER**||Массив ограничений, которые поддерживаются поставщиком.|  
|**Description**|**DBTYPE_WSTR**||Локализованное описание схемы.|  
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
|**schemaName**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
