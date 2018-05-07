---
title: Набор строк DISCOVER_STORAGE_TABLES | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0685808f47364f7e88f82b48540034ef0d0e688a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="discoverstoragetables-rowset"></a>Набор строк DISCOVER_STORAGE_TABLES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Позволяет клиенту определить таблицы, которые включены в базу данных служб Analysis Services, работающую в табличном режиме или режиме интеграции с SharePoint.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_STORAGE_TABLES** содержит следующие столбцы.  
  
|**Имя столбца**|**Индикатор типа**|**Длина**|**Description**|  
|---------------------|------------------------|----------------|---------------------|  
|**ИМЯ_БАЗЫ_ДАННЫХ**|**DBTYPE_WSTR**||Указывает имя базы данных, содержащей эти таблицы.<br /><br /> С помощью этого столбца можно ограничить набор строк **DISCOVER_STORAGE_TABLES** . Если этот столбец не используется для ограничения состава набора строк, используется текущая база данных.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Указывает куб или модель, содержащие эти таблицы.<br /><br /> С помощью этого столбца можно ограничить набор строк **DISCOVER_STORAGE_TABLES** .|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**||Имя группы мер.|  
|**ИМЯ_РАЗДЕЛА**|**DBTYPE_WSTR**||Имя секции.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Имя измерения.|  
|**TABLE_ID**|**DBTYPE_WSTR**||Идентификатор таблицы, используемой для хранения атрибутов таблицы.|  
|**TABLE_PARTITIONS_COUNT**|**DBTYPE_ WSTR**||Количество секций таблицы.|  
|**HINT_TABLE_TYPE**|**DBTYPE_ WSTR**||Подсказка, касающаяся табличного типа.|  
|**ROWS_COUNT**|**DBTYPE_UI4**||Количество строк в секции.|  
|**RIVIOLATION_COUNT**|**DBTYPE_UI4**||Количество строк, содержащих нарушения ссылочной целостности данных.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_STORAGE_TABLES** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|**Имя столбца**|**Индикатор типа**|**Состояние ограничения**|  
|---------------------|------------------------|---------------------------|  
|**ИМЯ_БАЗЫ_ДАННЫХ**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|Необязательно|  
|**ИМЯ_РАЗДЕЛА**|**DBTYPE_WSTR**|Необязательно|  
  
## <a name="example"></a>Пример  
 Следующий образец кода возвращает из базы данных по умолчанию для текущего соединения список таблиц хранения и количество строк в каждой.  
  
```  
SELECT TABLE_ID, ROWS_COUNT  
FROM $system.DISCOVER_STORAGE_TABLES  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services наборы строк схемы](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
