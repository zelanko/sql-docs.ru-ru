---
title: Сопоставление типов данных в интерфейсе ITableDefinition | Документация Майкрософт
description: Сопоставление типов данных в интерфейсе ITableDefinition
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- OLE DB Driver for SQL Server, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 4101c458b066ec34f010a5733510fb21e25e6840
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834192"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Сопоставление типов данных в интерфейсе ITableDefinition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  При создании таблиц с помощью функции **ITableDefinition::CreateTable** потребитель драйвера OLE DB для SQL Server может указывать типы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в передаваемом элементе *pwszTypeName* массива DBCOLUMNDESC. Если потребитель указывает тип данных столбца по имени, то сопоставление типов OLE DB, представляемое элементом *wType* структуры DBCOLUMNDESC, не учитывается.  
  
 При использовании элемента *wType* структуры DBCOLUMNDESC для указания новых типов данных столбца с использованием типов данных OLE DB драйвер OLE DB для SQL Server сопоставляет типы данных OLE DB указанным ниже образом.  
  
|Тип данных OLE DB|SQL Server<br /><br /> тип данных|Дополнительные сведения|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** или **varbinary(max)**|Драйвер OLE DB для SQL Server проверяет *ulColumnSize* структуры DBCOLUMNDESC. На основе значения и версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра, драйвер OLE DB для SQL Server выполняется сопоставление типа к **изображение**.<br /><br /> Если значение *ulColumnSize* меньше максимальной длины столбца типа **binary**, то драйвер OLE DB для SQL Server проверяет элемент *rgPropertySets* структуры DBCOLUMNDESC. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, драйвер OLE DB для SQL Server сопоставляет тип с типом для **двоичных**. Если значение свойства равно VARIANT_FALSE, драйвер OLE DB для SQL Server сопоставляет тип с типом для **varbinary**. В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца SQL Server.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime2**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_I8|**bigint**||
|DBTYPE_NUMERIC|**numeric**|Драйвер OLE DB для SQL Server проверяет элементы *bPrecision* и *bScale* структуры DBCOLUMDESC, чтобы определить точность и число десятичных знаков столбца **numeric**.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **text** или **varchar(max)**|Драйвер OLE DB для SQL Server проверяет *ulColumnSize* структуры DBCOLUMNDESC. На основе значения и версию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра, драйвер OLE DB для SQL Server выполняется сопоставление типа к **текст**.<br /><br /> Если значение *ulColumnSize* меньше максимальной длины столбца многобайтового символьного типа данных, то драйвер OLE DB для SQL Server проверяет элемент *rgPropertySets* структуры DBCOLUMNDESC. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, драйвер OLE DB для SQL Server сопоставляет тип с типом для **char**. Если значение свойства равно VARIANT_FALSE, драйвер OLE DB для SQL Server сопоставляет тип с типом для **varchar**. В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|DBTYPE_UDT|**UDT**|Следующие сведения используются в структурах **DBCOLUMNDESC**, применяемых методом **ITableDefinition::CreateTable**, когда требуются столбцы пользовательских типов:<br /><br /> *pwSzTypeName* учитывается.<br /><br /> *rgPropertySets* должен включать **DBPROPSET_SQLSERVERCOLUMN** свойство, задайте, как описано в разделе на **DBPROPSET_SQLSERVERCOLUMN**в [Using User-Defined типы ](../../oledb/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_VARIANT|**sql_variant**||
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** или **nvarchar(max)**|Драйвер OLE DB для SQL Server проверяет *ulColumnSize* структуры DBCOLUMNDESC. На основе значения, драйвер OLE DB для SQL Server сопоставляет тип с типом для **ntext**.<br /><br /> Если значение *ulColumnSize* меньше максимальной длины столбца символов Юникода, то драйвер OLE DB для SQL Server проверяет элемент *rgPropertySets* структуры DBCOLUMNDESC. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, драйвер OLE DB для SQL Server сопоставляет тип с типом для **nchar**. Если значение свойства равно VARIANT_FALSE, драйвер OLE DB для SQL Server сопоставляет тип с типом для **nvarchar**. В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|DBTYPE_XML|**XML**||  

> [!NOTE]  
>  При создании таблицы драйвер OLE DB для SQL Server сопоставляет только значения перечислений типов данных OLE DB, указанные в предшествующей таблице. Попытка создать таблицу со столбцом любого другого типа данных OLE DB приводит к ошибке.  

## <a name="see-also"></a>См. также:  
 [Типы данных &#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
