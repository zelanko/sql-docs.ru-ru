---
title: Набор строк MDSCHEMA_MEASURES | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 38dcc34b13b7b65508dc99f925fffa76f3420173
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mdschemameasures-rowset"></a>Набор строк MDSCHEMA_MEASURES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Описывает каждую меру в кубе.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **MDSCHEMA_MEASURES** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Имя каталога, которому принадлежит эта мера. Имеет значение**NULL** , если поставщик не поддерживает каталоги.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Имя схемы, которой принадлежит мера. **Значение NULL** Если поставщик не поддерживает схемы.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Имя куба, к которому относится эта мера.|  
|**MEASURE_NAME**|**DBTYPE_WSTR**||Имя меры.|  
|**MEASURE_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя меры. Для поставщиков, формирующих уникальные имена путем использования квалификаторов, компоненты имени разделяются между собой.|  
|**MEASURE_CAPTION**|**DBTYPE_WSTR**||Метка или заголовок, связанный с мерой. В основном используется в целях отображения. Если заголовок не существует, **MEASURE_NAME** возвращается.|  
|**MEASURE_GUID**|**DBTYPE_GUID**||Не поддерживается.|  
|**MEASURE_AGGREGATOR**|**DBTYPE_I4**||Перечисление, определяющее способ, которым была получена мера. Может использоваться одно из следующих значений:<br /><br /> **MDMEASURE_AGGR_SUM** (**1**) определяет, что мера использует статистическую функцию из **сумма**.<br /><br /> **MDMEASURE_AGGR_COUNT** (**2**) определяет, что мера использует статистическую функцию из **число**.<br /><br /> **MDMEASURE_AGGR_MIN** (**3**) определяет, что мера использует статистическую функцию из **MIN**.<br /><br /> **MDMEASURE_AGGR_MAX** (**4**) определяет, что мера использует статистическую функцию из **MAX**.<br /><br /> **MDMEASURE_AGGR_AVG** (**5**) определяет, что мера использует статистическую функцию из **AVG**.<br /><br /> **MDMEASURE_AGGR_VAR** (**6**) определяет, что мера использует статистическую функцию из **VAR**.<br /><br /> **MDMEASURE_AGGR_STD** (**7**) определяет, что мера использует статистическую функцию из **STDEV**.<br /><br /> **MDMEASURE_AGGR_DST** (**8**) определяет, что мера использует статистическую функцию из **числа РАЗЛИЧНЫХ ОБЪЕКТОВ**.<br /><br /> **MDMEASURE_AGGR_NONE** (**9**) определяет, что мера использует статистическую функцию из **NONE**.<br /><br /> **MDMEASURE_AGGR_AVGCHILDREN** (**10**) определяет, что мера использует статистическую функцию из **AVERAGEOFCHILDREN**.<br /><br /> **MDMEASURE_AGGR_FIRSTCHILD** (**11**) определяет, что мера использует статистическую функцию из **FIRSTCHILD**.<br /><br /> **MDMEASURE_AGGR_LASTCHILD** (**12**) определяет, что мера использует статистическую функцию из **LASTCHILD**.<br /><br /> **MDMEASURE_AGGR_FIRSTNONEMPTY** (**13**) определяет, что мера использует статистическую функцию из **FIRSTNONEMPTY**,<br /><br /> **MDMEASURE_AGGR_LASTNONEMPTY** (**14**) определяет, что мера использует статистическую функцию из **LASTNONEMPTY**.<br /><br /> **MDMEASURE_AGGR_BYACCOUNT** (**15**) определяет, что мера использует статистическую функцию из **BYACCOUNT**.<br /><br /> **MDMEASURE_AGGR_CALCULATED** (**127**) определяет, что мера была унаследована от формулы, не перечисленных выше одиночных функций.<br /><br /> **MDMEASURE_AGGR_UNKNOWN** (**0**) определяет, что мера была унаследована от неизвестной статистической функции или формулы.|  
|**ТИП ДАННЫХ**|**DBTYPE_UI2**||Тип данных меры.|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**||Максимальная точность свойства, если тип данных объекта меры — точное число. **Значение NULL** для всех других типов свойств.|  
|**NUMERIC_SCALE**|**DBTYPE_I2**||Количество цифр справа от десятичной запятой, если индикатор типа объекта меры имеет **DBTYPE_NUMERIC** или **DBTYPE_DECIMAL**. В противном случае это значение является **NULL**.|  
|**MEASURE_UNITS**|**DBTYPE_WSTR**||Не поддерживается|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Понятное описание меры. **Значение NULL** Если описания не существует.|  
|**ВЫРАЖЕНИЕ**|**DBTYPE_WSTR**||Выражение для элемента.|  
|**MEASURE_IS_VISIBLE**|**DBTYPE_BOOL**||Логическое значение, всегда возвращается True. Если мера невидима, то она не включается в набор строк схемы.|  
|**LEVELS_LIST**|**DBTYPE_WSTR**||Строка, которая всегда возвращает **NULL**.|  
|**MEASURE_NAME_SQL_COLUMN_NAME**|**DBTYPE_WSTR**||Имя столбца в SQL-запросе, который соответствует имени меры.|  
|**MEASURE_UNQUALIFIED_CAPTION**|**DBTYPE_WSTR**||Имя меры, не определенной с помощью имени группы мер.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||Имя группы мер, которой принадлежит мера.|  
|**MEASURE_DISPLAY_FOLDER**|**DBTYPE_WSTR**||Путь, используемый при отображении меры в пользовательском интерфейсе. Имена папок разделяются точкой с запятой. Вложенные папки указываются обратная косая черта (\\).|  
|**DEFAULT_FORMAT_STRING**|**DBTYPE_WSTR**||Строка форматирования по умолчанию для меры.|  
  
 Набор строк отсортирован по **CATALOG_NAME**, **имя_схемы**, **CUBE_NAME**, **MEASURE_NAME**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **MDSCHEMA_MEASURES** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**MEASURE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**MEASURE_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 CUBE<br /><br /> 2 DIMENSION|  
|**MEASURE_VISIBILITY**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 Отображается<br /><br /> 2 Не отображается|  
  
## <a name="see-also"></a>См. также  
 [OLE DB для OLAP наборы строк схемы](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
