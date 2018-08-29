---
title: Поддержка набора строк схемы (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- SQL Server Native Client OLE DB provider, schema rowsets
- rowsets [OLE DB], schema
ms.assetid: a75b4b69-b095-4690-9b31-a2b32a67489e
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c38b2e26b671a0e7253426adaa192810758c32ab
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43063307"
---
# <a name="schema-rowset-support-ole-db"></a>Поддержка набора строк схемы (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента также поддерживает возвращение информации схемы со связанного сервера при обработке [!INCLUDE[tsql](../../../includes/tsql-md.md)] распределенных запросов.  
  
> [!NOTE]  
>  Хотя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает синонимы, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не возвращает метаданные для синонимов.  
  
 Следующие таблицы перечисляют наборы строк схемы и столбцы ограничений, поддерживаемые [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента.  
  
|Набор строк схемы|Столбцы ограничений|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMN_PRIVILEGES|Поддерживаются все ограничения.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|DBSCHEMA_COLUMNS|Поддерживаются все ограничения.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME<br /><br /> Следующие столбцы являются специфичными для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> COLUMN_LCID, представляющий собой код локали для параметра сортировки. Значение COLUMN_LCID совпадает со значением кода языка Windows.<br /><br /> COLUMN_COMPFLAGS определяет, какие сравнения поддерживаются для данного параметра сортировки. Формат данных совпадает с форматом DBPROB_FINDCOMPAREOPS.<br /><br /> COLUMN_SORTID, представляющий собой стиль сортировки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для параметров сортировки.<br /><br /> COLUMN_TDSCOLLATION, представляющий собой параметр сортировки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для данного столбца.<br /><br /> IS_COMPUTED, имеющий значение VARIANT_TRUE для вычисляемых столбцов и VARIANT_FALSE — для всех остальных.|  
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
  
## <a name="in-this-section"></a>в этом разделе  
 [Поддержка распределенных запросов в наборах строк схемы](../../../relational-databases/native-client/ole-db/schema-rowsets-distributed-query-support.md)  
  
 [Набор строк LINKEDSERVERS &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Использование определяемых пользователем типов](../../../relational-databases/native-client/features/using-user-defined-types.md)  
  
  
