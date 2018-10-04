---
title: Поддержка распределенных запросов в наборах строк схемы | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 93b285b2e06fbe9227f9012f22ded8e932c35457
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164312"
---
# <a name="distributed-query-support-in-schema-rowsets"></a>Поддержка распределенных запросов в наборах строк схемы
  Для поддержки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] распределенные запросы, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента **IDBSchemaRowset** интерфейс возвращает метаданные связанных серверов.  
  
 Если свойство SSPROP_QUOTEDCATALOGNAMES набора свойств DBPROPSET_SQLSERVERSESSION имеет значение VARIANT_TRUE, можно указать заключенный в кавычки идентификатор имени каталога (например, "my.catalog"). При ограничении вывода набора строк схемы по каталогу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента распознает двухкомпонентное имя, содержащее имя связанного сервера и каталога. Для наборов строк схемы в приведенной ниже таблице указание двухкомпонентного имени каталога в виде *связанный_сервер ***.*** каталог* ограничивает выводимые данные подходящим каталогом именованного связанного сервера.  
  
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
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента определяет набор строк схемы LINKEDSERVERS, который возвращает список источников данных OLE DB, зарегистрированные как связанные серверы.  
  
## <a name="see-also"></a>См. также  
 [Поддержка набора строк схемы &#40;OLE DB&#41;](schema-rowset-support-ole-db.md)   
 [Набор строк LINKEDSERVERS &#40;OLE DB&#41;](schema-rowsets-linkedservers-rowset.md)  
  
  
