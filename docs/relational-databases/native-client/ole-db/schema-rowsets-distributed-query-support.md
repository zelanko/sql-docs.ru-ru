---
description: Наборы строк схемы — поддержка распределенных запросов в SQL Server Native Client
title: Поддержка распределенных запросов в наборах строк схемы | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], SQL Server Native Client OLE DB provider
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
ms.assetid: 11354bb6-be42-4d8d-854c-42dd3dc38656
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a09330a2ce78c9282a0980897df65d65e10a73c6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428066"
---
# <a name="schema-rowsets---distributed-query-support-in-sql-server-native-client"></a>Наборы строк схемы — поддержка распределенных запросов в SQL Server Native Client
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Для поддержки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] распределенных запросов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] интерфейс **IDBSchemaRowset** поставщика собственного OLE DB клиента возвращает метаданные на связанных серверах.  
  
 Если свойство SSPROP_QUOTEDCATALOGNAMES набора свойств DBPROPSET_SQLSERVERSESSION имеет значение VARIANT_TRUE, можно указать заключенный в кавычки идентификатор имени каталога (например, "my.catalog"). При сужении вывода набора строк схемы по каталогу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента распознает имя, состоящий из двух частей, содержащего имя связанного сервера и каталога. Для наборов строк схемы, приведенных в таблице ниже, укажите имя каталога из двух частей как _linked_server_**.** _Каталог_ разрешает вывод в соответствующий каталог именованного связанного сервера.  
  
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
>  Чтобы ограничить набор строк схемы всеми каталогами со связанного сервера, используйте синтаксис *связанный_сервер* (где точка-разделитель является частью спецификации имени). Этот синтаксис эквивалентен указанию значения NULL для ограничения имени каталога; он также используется, когда связанный сервер указывает на источник данных, который не поддерживает каталоги.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента определяет набор строк схемы LINKEDSERVERS, возвращая список OLE DB источников данных, зарегистрированных как связанные серверы.  
  
## <a name="see-also"></a>См. также:  
 [Поддержка набора строк схемы &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)   
 [Набор строк LINKEDSERVERS (OLE DB)](../../../relational-databases/native-client/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
  
