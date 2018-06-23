---
title: Набор строк MDSCHEMA_MEASURES | Документы Microsoft
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
api_name:
- MDSCHEMA_MEASURES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASURES rowset
ms.assetid: 6ff5bd1a-aad0-49b8-9f8d-7df2637caacf
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6608c64caa882499282ad7a7e30090ab4118b522
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086741"
---
# <a name="mdschemameasures-rowset"></a>Набор строк MDSCHEMA_MEASURES
  Описывает каждую меру в кубе.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `MDSCHEMA_MEASURES` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Имя каталога, которому принадлежит эта мера. Имеет значение `NULL`, если поставщик не поддерживает каталоги.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Имя схемы, которой принадлежит мера. Имеет значение `NULL`, если поставщик не поддерживает схемы.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Имя куба, к которому относится эта мера.|  
|`MEASURE_NAME`|`DBTYPE_WSTR`||Имя меры.|  
|`MEASURE_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя меры. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|`MEASURE_CAPTION`|`DBTYPE_WSTR`||Метка или заголовок, связанный с мерой. В основном используется в целях отображения. Если заголовок не существует, возвращается `MEASURE_NAME`.|  
|`MEASURE_GUID`|`DBTYPE_GUID`||Не поддерживается.|  
|`MEASURE_AGGREGATOR`|`DBTYPE_I4`||Перечисление, определяющее способ, которым была получена мера. Может использоваться одно из следующих значений:<br /><br /> -   `MDMEASURE_AGGR_SUM` (`1`) определяет, что мера использует статистическую функцию из `SUM`.<br />-   `MDMEASURE_AGGR_COUNT` (`2`) определяет, что мера использует статистическую функцию из `COUNT`.<br />-   **MDMEASURE_AGGR_MIN** (`3`) определяет, что мера использует статистическую функцию из `MIN`.<br />-   **MDMEASURE_AGGR_MAX** (`4`) определяет, что мера использует статистическую функцию из `MAX`.<br />-   `MDMEASURE_AGGR_AVG` (`5`) определяет, что мера использует статистическую функцию из `AVG`.<br />-   `MDMEASURE_AGGR_VAR` (`6`) определяет, что мера использует статистическую функцию из `VAR`.<br />-   `MDMEASURE_AGGR_STD` (`7`) определяет, что мера использует статистическую функцию из `STDEV`.<br />-   `MDMEASURE_AGGR_DST` (`8`) определяет, что мера использует статистическую функцию из `DISTINCT COUNT`.<br />-   `MDMEASURE_AGGR_NONE` (`9`) определяет, что мера использует статистическую функцию из `NONE`.<br />-   `MDMEASURE_AGGR_AVGCHILDREN` (`10`) определяет, что мера использует статистическую функцию из `AVERAGEOFCHILDREN`.<br />-   `MDMEASURE_AGGR_FIRSTCHILD` (`11`) определяет, что мера использует статистическую функцию из `FIRSTCHILD`.<br />-   `MDMEASURE_AGGR_LASTCHILD` (`12`) определяет, что мера использует статистическую функцию из `LASTCHILD`.<br />-   `MDMEASURE_AGGR_FIRSTNONEMPTY` (`13`) определяет, что мера использует статистическую функцию из `FIRSTNONEMPTY`,<br />-   `MDMEASURE_AGGR_LASTNONEMPTY` (`14`) определяет, что мера использует статистическую функцию из `LASTNONEMPTY`.<br />-   `MDMEASURE_AGGR_BYACCOUNT` (`15`) определяет, что мера использует статистическую функцию из `BYACCOUNT`.<br />-   `MDMEASURE_AGGR_CALCULATED` (`127`) определяет, что мера была унаследована от формулы, не перечисленных выше одиночных функций.<br />-   `MDMEASURE_AGGR_UNKNOWN` (`0`) определяет, что мера была унаследована от неизвестной статистической функции или формулы.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Тип данных меры.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Максимальная точность свойства, если тип данных объекта меры — точное число. Значение `NULL` для всех других типов свойств.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Число цифр справа от десятичного разделителя, если индикатор типа объекта меры имеет значение `DBTYPE_NUMERIC` или `DBTYPE_DECIMAL`. В противном случае это значение равно `NULL`.|  
|`MEASURE_UNITS`|`DBTYPE_WSTR`||Не поддерживается|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание меры. Имеет значение `NULL`, если описание отсутствует.|  
|`EXPRESSION`|`DBTYPE_WSTR`||Выражение для элемента.|  
|`MEASURE_IS_VISIBLE`|`DBTYPE_BOOL`||Логическое значение, всегда возвращается True. Если мера невидима, то она не включается в набор строк схемы.|  
|`LEVELS_LIST`|`DBTYPE_WSTR`||Строка, которая всегда возвращает значение `NULL`.|  
|`MEASURE_NAME_SQL_COLUMN_NAME`|`DBTYPE_WSTR`||Имя столбца в SQL-запросе, который соответствует имени меры.|  
|`MEASURE_UNQUALIFIED_CAPTION`|`DBTYPE_WSTR`||Имя меры, не определенной с помощью имени группы мер.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Имя группы мер, которой принадлежит мера.|  
|`MEASURE_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Путь, используемый при отображении меры в пользовательском интерфейсе. Имена папок разделяются точкой с запятой. Вложенные папки указываются обратная косая черта (\\).|  
|`DEFAULT_FORMAT_STRING`|`DBTYPE_WSTR`||Строка форматирования по умолчанию для меры.|  
  
 Набор строк отсортирован по полям `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `MEASURE_NAME`.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `MDSCHEMA_MEASURES` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MEASURE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MEASURE_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> -КУБ 1<br />-2 ИЗМЕРЕНИЯ.<br /><br /> Значение по умолчанию для ограничения — 1.|  
|`MEASURE_VISIBILITY`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> — Visible 1<br />-2 не отображается<br /><br /> Значение по умолчанию для ограничения — 1.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB для OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  