---
title: Поддержка набора строк схемы (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- SQL Server Native Client OLE DB provider, schema rowsets
- rowsets [OLE DB], schema
ms.assetid: a75b4b69-b095-4690-9b31-a2b32a67489e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83b6ea8594d22527f2f9b87a77d70671c5724111
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62625968"
---
# <a name="schema-rowset-support-ole-db"></a>Поддержка набора строк схемы (OLE DB)
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента также поддерживает возвращение информации схемы со связанного сервера при обработке [!INCLUDE[tsql](../../../includes/tsql-md.md)] распределенных запросов.  
  
> [!NOTE]  
>  Хотя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает синонимы, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не возвращает метаданные для синонимов.  
  
 Следующие таблицы перечисляют наборы строк схемы и столбцы ограничений, поддерживаемые [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента.  
  
|Набор строк схемы|Столбцы ограничений|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMN_PRIVILEGES|Поддерживаются все ограничения.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|DBSCHEMA_COLUMNS|Поддерживаются все ограничения.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME<br /><br /> Следующие столбцы являются специфичными для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> -COLUMN_LCID, который является Идентификатором параметров сортировки. Значение COLUMN_LCID совпадает со значением кода языка Windows.<br />-COLUMN_COMPFLAGS определяет, какие сравнения поддерживаются для параметров сортировки. Формат данных совпадает с форматом DBPROB_FINDCOMPAREOPS.<br />-COLUMN_SORTID, представляющий собой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сортировки стиля для параметров сортировки.<br />-COLUMN_TDSCOLLATION, который является [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] параметры сортировки для столбца.<br />-IS_COMPUTED, имеющий значение VARIANT_TRUE, если столбец является вычисляемым столбцом, либо значение VARIANT_FALSE в противном случае.|  
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
 [Поддержка распределенных запросов в наборах строк схемы](schema-rowsets-distributed-query-support.md)  
  
 [Набор строк LINKEDSERVERS &#40;OLE DB&#41;](schema-rowsets-linkedservers-rowset.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;OLE DB&#41;](sql-server-native-client-ole-db.md)   
 [Использование определяемых пользователем типов](../features/using-user-defined-types.md)  
  
  
