---
title: Поддержка наборов строк схемы (OLE DB) | Документы Microsoft
description: Поддержка наборов строк схемы (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- OLE DB Driver for SQL Server, schema rowsets
- rowsets [OLE DB], schema
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 20c6eb1e6b207b5f5d8c923a772bec345246d228
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="schema-rowset-support-ole-db"></a>Поддержка набора строк схемы (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server поддерживает возвращение информации схемы со связанного сервера, при обработке [!INCLUDE[tsql](../../../includes/tsql-md.md)] распределенных запросов.  
  
> [!NOTE]  
>  Несмотря на то что [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает синонимы, метаданные для синонимов не возвращается драйвером OLE DB для SQL Server.  
  
 В следующих таблицах перечислены наборы строк схемы и столбцы ограничений, поддерживаемых драйвером OLE DB для SQL Server.  
  
|Набор строк схемы|Столбцы ограничений|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMN_PRIVILEGES|Поддерживаются все ограничения.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|DBSCHEMA_COLUMNS|Поддерживаются все ограничения.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME<br /><br /> Следующие столбцы являются специфичными для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> COLUMN_LCID, представляющий собой код локали для параметра сортировки. Значение COLUMN_LCID совпадает со значением кода языка Windows.<br /><br /> COLUMN_COMPFLAGS определяет, какие сравнения поддерживаются для данного параметра сортировки. Формат данных совпадает с форматом DBPROB_FINDCOMPAREOPS.<br /><br /> COLUMN_SORTID, представляющий собой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сортировки стиль для параметров сортировки.<br /><br /> COLUMN_TDSCOLLATION, представляющий собой параметр сортировки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для данного столбца.<br /><br /> IS_COMPUTED, имеющий значение VARIANT_TRUE для вычисляемых столбцов и VARIANT_FALSE — для всех остальных.|  
|DBSCHEMA_FOREIGN_KEYS|Поддерживаются все ограничения.<br /><br /> PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME FK_TABLE_CATALOG FK_TABLE_SCHEMA FK_TABLE_NAME|  
|DBSCHEMA_INDEXES|Поддерживаются ограничения 1, 2, 3 и 5.<br /><br /> TABLE_CATALOG TABLE_SCHEMA INDEX_NAME TABLE_NAME|  
|DBSCHEMA_PRIMARY_KEYS|Поддерживаются все ограничения.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_PROCEDURE_PARAMETERS|Поддерживаются все ограничения.<br /><br /> PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME|  
|DBSCHEMA_PROCEDURES|Поддерживаются ограничения 1, 2 и 3.<br /><br /> PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME<br /><br /> DBSCHEMA_PROCEDURES возвращает только процедуры, которые могут быть выполнены текущим пользователем, и те, для которых текущему пользователю предоставлено разрешение VIEW DEFINITION.|  
|DBSCHEMA_PROVIDER_TYPES|Поддерживаются все ограничения.<br /><br /> DATA_TYPE BEST_MATCH|  
|DBSCHEMA_SCHEMATA|Поддерживаются все ограничения.<br /><br /> CATALOG_NAME SCHEMA_NAME SCHEMA_OWNER|  
|DBSCHEMA_STATISTICS|Поддерживаются все ограничения.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_TABLE_CONSTRAINTS|Поддерживаются все ограничения.<br /><br /> CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME CONSTRAINT_TYPE|  
|DBSCHEMA_TABLE_PRIVILEGES|Поддерживаются все ограничения.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME GRANTOR GRANTEE|  
|DBSCHEMA_TABLES|Поддерживаются все ограничения.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
|DBSCHEMA_TABLES_INFO|Поддерживаются все ограничения.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
  
## <a name="in-this-section"></a>В этом разделе  
 [Поддержка распределенных запросов в наборах строк схемы](../../oledb/ole-db/schema-rowsets-distributed-query-support.md)  
  
 [Набор строк LINKEDSERVERS &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для SQL Server программирования](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [Использование определяемых пользователем типов](../../oledb/features/using-user-defined-types.md)  
  
  
