---
title: Поддержка распределенных запросов в наборах строк схемы | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a47dd9575132210bbd5d664fbb3c73b57289693f
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704230"
---
# <a name="distributed-query-support-in-schema-rowsets"></a>Поддержка распределенных запросов в наборах строк схемы
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
  
## <a name="see-also"></a>См. также  
 [&#40;OLE DB поддерживает набор строк схемы&#41;](schema-rowset-support-ole-db.md)   
 [Набор строк LINKEDSERVERS (OLE DB)](schema-rowsets-linkedservers-rowset.md)  
  
  
