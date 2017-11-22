---
title: "Сопоставление типов данных в интерфейсе ITableDefinition | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-data-types
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
ms.assetid: 13292d1f-c17e-4d11-bf98-3460a10cbb18
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c9e8c3fbcce7146c2de17caa97e70a539de6a90b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="data-type-mapping-in-itabledefinition"></a>Сопоставление типов данных в интерфейсе ITableDefinition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  При создании таблицы с помощью **ITableDefinition::CreateTable** функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителем поставщика OLE DB для собственного клиента можно указать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных в *pwszTypeName* члена массива DBCOLUMNDESC, передается. Если потребитель указывает тип данных столбца по имени, тип данных OLE DB сопоставление, представленное *wType* структуры DBCOLUMNDESC, учитывается.  
  
 При указании новых типов данных столбцов с типами данных OLE DB с помощью структуры DBCOLUMNDESC *wType* член, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента сопоставляет типы данных OLE DB, как показано ниже.  
  
|Тип данных OLE DB|SQL Server<br /><br /> тип данных|Дополнительные сведения|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**двоичный**, **varbinary**, **изображения,** или **varbinary(max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента проверяет *ulColumnSize* структуры DBCOLUMNDESC. На основе значения и версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **изображения**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина **двоичных** столбец типа данных, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента проверяет структуры DBCOLUMNDESC *rgPropertySets* член. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **двоичных**. Если значение свойства равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **varbinary**. В любом случае структуры DBCOLUMNDESC *ulColumnSize* определяет ширину создаваемого столбца SQL Server.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента проверяет элемент DBCOLUMDESC *bPrecision* и *bScale* членов, чтобы определить точность и масштаб для **числовое** столбца.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **текста,** или **varchar(max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента проверяет *ulColumnSize* структуры DBCOLUMNDESC. На основе значения и версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **текст**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа данных Многобайтовый символ, а затем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента проверяет структуры DBCOLUMNDESC *rgPropertySets* член. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **char**. Если значение свойства равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **varchar**. В любом случае структуры DBCOLUMNDESC *ulColumnSize* определяет ширину [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создан столбец.|  
|DBTYPE_UDT|**UDT**|Следующие сведения используются в **DBCOLUMNDESC** структуры по **ITableDefinition::CreateTable** при необходимы столбцы определяемого пользователем ТИПА:<br /><br /> *pwSzTypeName* учитывается.<br /><br /> *rgPropertySets* должен включать **DBPROPSET_SQLSERVERCOLUMN** свойства, как это описано в разделе на **DBPROPSET_SQLSERVERCOLUMN**в [с помощью определяемого пользователем Типы](../../relational-databases/native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext,** или **nvarchar(max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента проверяет *ulColumnSize* структуры DBCOLUMNDESC. На основе значения, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **ntext**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа данных символов Юникода, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента проверяет структуры DBCOLUMNDESC *rgPropertySets* член. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **nchar**. Если значение свойства равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **nvarchar**. В любом случае структуры DBCOLUMNDESC *ulColumnSize* определяет ширину [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создан столбец.|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  При создании новой таблицы поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сопоставляет только значения перечислений типов данных OLE DB, указанные в предшествующей таблице. Попытка создать таблицу со столбцом любого другого типа данных OLE DB приводит к ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Типы данных &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
