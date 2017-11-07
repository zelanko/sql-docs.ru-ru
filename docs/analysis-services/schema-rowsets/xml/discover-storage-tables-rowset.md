---
title: "Набор строк DISCOVER_STORAGE_TABLES | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 13df6f10-8efe-4fe9-83a6-96d108809ed1
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d882e8b20949a656c1402af084a6e017c33b444f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="discoverstoragetables-rowset"></a>Набор строк DISCOVER_STORAGE_TABLES
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
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services наборы строк схемы](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  

