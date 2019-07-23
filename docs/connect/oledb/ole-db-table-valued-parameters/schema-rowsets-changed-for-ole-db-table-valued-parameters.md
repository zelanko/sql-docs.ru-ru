---
title: Наборы строк схемы, измененные для возвращающих табличное значение параметров OLE DB | Документы Майкрософт
description: Наборы строк схемы, измененные для возвращающих табличное значение параметров OLE DB
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 0ca6d03779f58719d1b56e8d3de9e45bfa3a36c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015303"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>Наборы строк схемы, измененные для возвращающих табличное значение параметров OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Далее приведены наборы строк схемы, измененные или добавленные для поддержки возвращающих табличные значения параметров.  
  
|Набор строк схемы|Описание|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|В конец набора строк были добавлены два новых столбца с именами SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMANAME. Эти столбцы можно повторно использовать для будущих типов. Столбцы TYPE_NAME и LOCAL_TYPE_NAME содержат имя возвращающего табличное значение параметра типа TABLE. Столбец DATA_TYPE для возвращающих табличные значения параметров принимает значение DBTYPE_TABLE = 143.|  
|DBSCHEMA_TABLE_TYPES|Этот набор строк был добавлен для поддержки возвращающих табличное значение параметров. Он аналогичен набору строк DBSCHEMA_TABLES, за исключением того, что возвращает метаданные только для табличных типов, а не для таблиц, представлений или синонимов. Столбец TABLE_TYPE принимает значение TABLE TYPE.|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|Этот набор строк был добавлен для поддержки возвращающих табличное значение параметров. Он аналогичен набору строк DBSCHEMA_PRIMARY_KEYS, за исключением того, что возвращает метаданные первичных ключей только для табличных типов, а не для таблиц.|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|Этот набор строк был добавлен для поддержки возвращающих табличное значение параметров. Он аналогичен набору строк DBSCHEMA_COLUMNS, за исключением того, что возвращает метаданные столбцов только для табличных типов, а не для таблиц, представлений или синонимов.|  
  
## <a name="see-also"></a>См. также:  
 [Возвращающие табличные значения параметры &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
