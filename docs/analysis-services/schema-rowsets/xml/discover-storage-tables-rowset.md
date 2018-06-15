---
title: Набор строк DISCOVER_STORAGE_TABLES | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b87759d736044febc89099d493fb357d7e5153b9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34029295"
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
  
  
