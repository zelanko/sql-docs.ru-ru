---
title: Наборы строк схемы, OLE DB возвращающие табличное значение параметры
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
ms.assetid: 581e3ead-53db-44da-8718-f3fc4b5108f1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3f214bd650a16dceddd68ec90ded84980d9333ef
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86013016"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>Наборы строк схемы, измененные для возвращающих табличное значение параметров OLE DB
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Далее приведены наборы строк схемы, измененные или добавленные для поддержки возвращающих табличные значения параметров.  
  
|Набор строк схемы|Описание|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|В конец набора строк были добавлены два новых столбца с именами SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMANAME. Эти столбцы можно повторно использовать для будущих типов. Столбцы TYPE_NAME и LOCAL_TYPE_NAME содержат имя возвращающего табличное значение параметра типа TABLE. Столбец DATA_TYPE для возвращающих табличные значения параметров принимает значение DBTYPE_TABLE = 143.|  
|DBSCHEMA_TABLE_TYPES|Этот набор строк был добавлен для поддержки возвращающих табличное значение параметров. Он аналогичен набору строк DBSCHEMA_TABLES, за исключением того, что возвращает метаданные только для табличных типов, а не для таблиц, представлений или синонимов. Столбец TABLE_TYPE принимает значение TABLE TYPE.|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|Этот набор строк был добавлен для поддержки возвращающих табличное значение параметров. Он аналогичен набору строк DBSCHEMA_PRIMARY_KEYS, за исключением того, что возвращает метаданные первичных ключей только для табличных типов, а не для таблиц.|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|Этот набор строк был добавлен для поддержки возвращающих табличное значение параметров. Он аналогичен набору строк DBSCHEMA_COLUMNS, за исключением того, что возвращает метаданные столбцов только для табличных типов, а не для таблиц, представлений или синонимов.|  
|||

## <a name="see-also"></a>См. также  
 [Возвращающие табличное значение параметры &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
