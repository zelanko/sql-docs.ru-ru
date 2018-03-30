---
title: Поддержка распределенных запросов в наборах строк схемы | Документы Microsoft
description: Поддержка распределенных запросов в наборах строк схемы
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], OLE DB Driver for SQL Server
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5a1ac686e4dc9da7dee3b444adfbcbda801901d0
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="schema-rowsets---distributed-query-support"></a>Наборы строк схемы — поддержка распределенных запросов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Для поддержки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] распределенные запросы, драйвер OLE DB для SQL Server **IDBSchemaRowset** интерфейс возвращает метаданные связанных серверов.  
  
 Если свойство SSPROP_QUOTEDCATALOGNAMES набора свойств DBPROPSET_SQLSERVERSESSION имеет значение VARIANT_TRUE, можно указать заключенный в кавычки идентификатор имени каталога (например, "my.catalog"). При ограничении вывода набора строк схемы по каталогу, драйвер OLE DB для SQL Server распознает двухкомпонентное имя, состоящее из связанного сервера и имя каталога. Наборы строк схемы в таблице ниже, для указания каталога двухкомпонентное имя в качестве *связанный_сервер***.*** каталог* ограничивает выходные данные подходящим каталогом именованного связанного сервера.  
  
|Набор строк схемы|Ограничение каталога|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMNS|TABLE_CATALOG|  
|DBSCHEMA_PRIMARY_KEYS|TABLE_CATALOG|  
|DBSCHEMA_TABLES|TABLE_CATALOG|  
|DBSCHEMA_FOREIGN_KEYS|PK_TABLE_CATALOG FK_TABLE_CATALOG|  
|DBSCHEMA_INDEXES|TABLE_CATALOG|  
|DBSCHEMA_COLUMN_PRIVILEGES|TABLE_CATALOG|  
|DBSCHEMA_TABLE_PRIVILEGES|TABLE_CATALOG|  
  
> [!NOTE]  
>  Чтобы ограничить набор строк схемы всеми каталогами из связанного сервера, используйте синтаксис *связанный_сервер* (где точка-разделитель является частью спецификации имени). Этот синтаксис эквивалентен указанию значения NULL для ограничения имени каталога; он также используется, когда связанный сервер указывает на источник данных, который не поддерживает каталоги.  
  
 Драйвер OLE DB для SQL Server определяет набор строк схемы LINKEDSERVERS, который возвращает список источников данных OLE DB, зарегистрированные как связанные серверы.  
  
## <a name="see-also"></a>См. также  
 [Поддержка наборов строк схемы &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)   
 [Набор строк LINKEDSERVERS &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
  
