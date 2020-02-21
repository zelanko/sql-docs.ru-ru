---
title: Сопоставление типов данных в интерфейсе ITableDefinition | Документация Майкрософт
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
ms.openlocfilehash: abe874a50e8534291a67393dfaf3485c96405b02
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "68015850"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Сопоставление типов данных в интерфейсе ITableDefinition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  При создании таблиц с помощью функции **ITableDefinition::CreateTable** потребитель драйвера OLE DB для SQL Server может указывать типы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в передаваемом элементе *pwszTypeName* массива DBCOLUMNDESC. Если потребитель указывает тип данных столбца по имени, то сопоставление типов OLE DB, представляемое элементом *wType* структуры DBCOLUMNDESC, не учитывается.  
  
 При использовании элемента *wType* структуры DBCOLUMNDESC для указания новых типов данных столбца с использованием типов данных OLE DB драйвер OLE DB для SQL Server сопоставляет типы данных OLE DB указанным ниже образом.  
  
|Тип данных OLE DB|SQL Server<br /><br /> тип данных|Дополнительные сведения|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** или **varbinary(max)**|OLE DB Driver for SQL Server выполняет проверку элемента *ulColumnSize* структуры DBCOLUMNDESC. В зависимости от значения и от версии экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB Driver for SQL Server сопоставляет тип с типом **image**.<br /><br /> Если значение *ulColumnSize* меньше максимальной длины столбца типа **binary**, то драйвер OLE DB для SQL Server проверяет элемент *rgPropertySets* структуры DBCOLUMNDESC. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, OLE DB Driver for SQL Server сопоставляет этот тип с типом **binary**. Если значение свойства равно VARIANT_FALSE, OLE DB Driver for SQL Server сопоставляет этот тип с типом **varbinary**. В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца SQL Server.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime2**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_I8|**bigint**||
|DBTYPE_NUMERIC|**numeric**|Драйвер OLE DB для SQL Server проверяет элементы *bPrecision* и *bScale* структуры DBCOLUMDESC, чтобы определить точность и число десятичных знаков столбца **numeric**.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **text** или **varchar(max)**|OLE DB Driver for SQL Server выполняет проверку элемента *ulColumnSize* структуры DBCOLUMNDESC. В зависимости от значения и от версии экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB Driver for SQL Server сопоставляет тип с типом **text**.<br /><br /> Если значение *ulColumnSize* меньше максимальной длины столбца многобайтового символьного типа данных, то драйвер OLE DB для SQL Server проверяет элемент *rgPropertySets* структуры DBCOLUMNDESC. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, OLE DB Driver for SQL Server сопоставляет этот тип с типом **char**. Если значение свойства равно VARIANT_FALSE, OLE DB Driver for SQL Server сопоставляет этот тип с типом **varchar**. В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|DBTYPE_UDT|**UDT**|Следующие сведения используются в структурах **DBCOLUMNDESC**, применяемых методом **ITableDefinition::CreateTable**, когда требуются столбцы пользовательских типов:<br /><br /> *pwSzTypeName* игнорируется.<br /><br /> Свойство *rgPropertySets* должно включать набор свойств **DBPROPSET_SQLSERVERCOLUMN**, как описано в пункте **DBPROPSET_SQLSERVERCOLUMN** раздела [Использование определяемых пользователем типов](../../oledb/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_VARIANT|**sql_variant**||
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** или **nvarchar(max)**|OLE DB Driver for SQL Server выполняет проверку элемента *ulColumnSize* структуры DBCOLUMNDESC. В зависимости от значения OLE DB Driver for SQL Server сопоставляет тип с типом **ntext**.<br /><br /> Если значение *ulColumnSize* меньше максимальной длины столбца символов Юникода, то драйвер OLE DB для SQL Server проверяет элемент *rgPropertySets* структуры DBCOLUMNDESC. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, OLE DB Driver for SQL Server сопоставляет этот тип с типом **nchar**. Если значение свойства равно VARIANT_FALSE, OLE DB Driver for SQL Server сопоставляет этот тип с типом **nvarchar**. В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|DBTYPE_XML|**XML**||  

> [!NOTE]  
>  При создании таблицы драйвер OLE DB для SQL Server сопоставляет только значения перечислений типов данных OLE DB, указанные в предшествующей таблице. Попытка создать таблицу со столбцом любого другого типа данных OLE DB приводит к ошибке.  

## <a name="see-also"></a>См. также:  
 [Типы данных (OLE DB)](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
