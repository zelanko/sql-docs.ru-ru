---
title: Набор строк DISCOVER_PARTITION_STAT | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 20d339e2-f47f-437f-94d5-5b00b400356a
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 98db8d43f86cc9acaf612da8180498d22e01d037
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194359"
---
# <a name="discoverpartitionstat-rowset"></a>Набор строк DISCOVER_PARTITION_STAT
  Возвращает статистику по агрегатам в заданной секции.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_PARTITION_STAT` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Описание|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Обязательно|Имя базы данных, содержащей измерение.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Обязательно|Имя куба или табличной модели, содержащей секцию.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Обязательно|Имя группы мер в измерении.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Обязательно|Имя секции.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|`AGGREGATION_NAME`|`DBTYPE_WSTR`||Имя агрегата.|  
|`AGGREGATION_SIZE`|`DBTYPE_I8`||Размер агрегата.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd8f-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionStat|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  