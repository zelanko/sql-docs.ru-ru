---
title: "Наборы строк схемы изменены табличное значение параметров OLE DB | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
ms.assetid: 581e3ead-53db-44da-8718-f3fc4b5108f1
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3ec3496be31125f86ff672845421391b3995fe5
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>Наборы строк схемы, измененные для возвращающих табличное значение параметров OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Далее приведены наборы строк схемы, измененные или добавленные для поддержки возвращающих табличные значения параметров.  
  
|Набор строк схемы|Description|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|В конец набора строк были добавлены два новых столбца с именами SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMANAME. Эти столбцы можно повторно использовать для будущих типов. Столбцы TYPE_NAME и LOCAL_TYPE_NAME содержат имя возвращающего табличное значение параметра типа TABLE. Столбец DATA_TYPE для возвращающих табличные значения параметров принимает значение DBTYPE_TABLE = 143.|  
|DBSCHEMA_TABLE_TYPES|Этот набор строк был добавлен для поддержки возвращающих табличное значение параметров. Он аналогичен набору строк DBSCHEMA_TABLES, за исключением того, что возвращает метаданные только для табличных типов, а не для таблиц, представлений или синонимов. Столбец TABLE_TYPE принимает значение TABLE TYPE.|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|Этот набор строк был добавлен для поддержки возвращающих табличное значение параметров. Он аналогичен набору строк DBSCHEMA_PRIMARY_KEYS, за исключением того, что возвращает метаданные первичных ключей только для табличных типов, а не для таблиц.|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|Этот набор строк был добавлен для поддержки возвращающих табличное значение параметров. Он аналогичен набору строк DBSCHEMA_COLUMNS, за исключением того, что возвращает метаданные столбцов только для табличных типов, а не для таблиц, представлений или синонимов.|  
  
## <a name="see-also"></a>См. также:  
 [Возвращающие табличные значения параметры &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметры &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
