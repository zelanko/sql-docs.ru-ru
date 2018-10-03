---
title: Набор строк DISCOVER_STORAGE_TABLES | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 13df6f10-8efe-4fe9-83a6-96d108809ed1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bcea65e3ada897e1c6bcd72027ee9d533d95a61e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059304"
---
# <a name="discoverstoragetables-rowset"></a>Набор строк DISCOVER_STORAGE_TABLES
  Позволяет клиенту определить таблицы, которые включены в базу данных служб Analysis Services, работающую в табличном режиме или режиме интеграции с SharePoint.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_STORAGE_TABLES` Набор строк содержит следующие столбцы.  
  
|**Имя столбца**|**Индикатор типа**|**Длина**|**Описание**|  
|---------------------|------------------------|----------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`||Указывает имя базы данных, содержащей эти таблицы.<br /><br /> `DISCOVER_STORAGE_TABLES` Набора строк можно ограничить с помощью этого столбца. Если этот столбец не используется для ограничения состава набора строк, используется текущая база данных.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Указывает куб или модель, содержащие эти таблицы.<br /><br /> `DISCOVER_STORAGE_TABLES` Набора строк можно ограничить с помощью этого столбца.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`||Имя группы мер.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`||Имя секции.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Имя измерения.|  
|`TABLE_ID`|`DBTYPE_WSTR`||Идентификатор таблицы, используемой для хранения атрибутов таблицы.|  
|`TABLE_PARTITIONS_COUNT`|`DBTYPE_ WSTR`||Количество секций таблицы.|  
|`HINT_TABLE_TYPE`|`DBTYPE_ WSTR`||Подсказка, касающаяся табличного типа.|  
|`ROWS_COUNT`|`DBTYPE_UI4`||Количество строк в секции.|  
|`RIVIOLATION_COUNT`|`DBTYPE_UI4`||Количество строк, содержащих нарушения ссылочной целостности данных.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_STORAGE_TABLES` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|**Имя столбца**|**Индикатор типа**|**Состояние ограничения**|  
|---------------------|------------------------|---------------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Необязательно|  
  
## <a name="example"></a>Пример  
 Следующий образец кода возвращает из базы данных по умолчанию для текущего соединения список таблиц хранения и количество строк в каждой.  
  
```  
SELECT TABLE_ID, ROWS_COUNT  
FROM $system.DISCOVER_STORAGE_TABLES  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы служб Analysis Services](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
