---
title: "Набор строк DISCOVER_PARTITION_STAT | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 20d339e2-f47f-437f-94d5-5b00b400356a
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 649475fa5fd1a4e0bb2a6c734f916270ac7f9a64
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="discoverpartitionstat-rowset"></a>Набор строк DISCOVER_PARTITION_STAT
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Возвращает статистику по агрегатам в заданной секции.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_PARTITION_STAT** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**ИМЯ_БАЗЫ_ДАННЫХ**|**DBTYPE_WSTR**|Обязательно|Имя базы данных, содержащей измерение.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Обязательно|Имя куба или табличной модели, содержащей секцию.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|Обязательно|Имя группы мер в измерении.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|**ИМЯ_РАЗДЕЛА**|**DBTYPE_WSTR**|Обязательно|Имя секции.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|**AGGREGATION_NAME**|**DBTYPE_WSTR**||Имя агрегата.|  
|**AGGREGATION_SIZE**|**DBTYPE_I8**||Размер агрегата.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd8f-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionStat|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
