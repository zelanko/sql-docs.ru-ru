---
title: Сопоставление типов данных в наборах строк и параметрах | Документация Майкрософт
description: Сопоставление типов данных в наборах строк и параметрах
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- DBTYPE_SQLVARIANT data type
- OLE DB Driver for SQL Server, data types
- rowsets [OLE DB], data type mapping
- data types [OLE DB]
- GetColumnInfo function
- parameters [OLE DB]
- SSPROP_ALLOWNATIVEVARIANT property
- GetParameterInfo function
- OLE DB, data types
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: c9c6d56cdbbbcd9b35b09f405154497a5fa3bc8f
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108796"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a>Сопоставление типов данных в наборах строк и параметрах
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В наборах строк и значениях как параметрах драйвер OLE DB для SQL Server представляет данные [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью указанных ниже определенных типов данных OLE DB, сообщаемых в функциях **IColumnsInfo::GetColumnInfo** и **ICommandWithParameters::GetParameterInfo**.  
  
|Тип данных SQL Server|Тип данных OLE DB|  
|--------------------------|----------------------|  
|**bigint**|DBTYPE_I8|  
|**binary**|DBTYPE_BYTES|  
|**bit**|DBTYPE_BOOL|  
|**char**|DBTYPE_STR|  
|**datetime**|DBTYPE_DBTIMESTAMP|  
|**datetime2**|DBTYPE_DBTIME2|  
|**decimal**|DBTYPE_NUMERIC|  
|**float**|DBTYPE_R8|  
|**image**|DBTYPE_BYTES|  
|**int**|DBTYPE_I4|  
|**money**|DBTYPE_CY|  
|**nchar**|DBTYPE_WSTR|  
|**ntext**|DBTYPE_WSTR|  
|**numeric**|DBTYPE_NUMERIC|  
|**nvarchar**|DBTYPE_WSTR|  
|**real**|DBTYPE_R4|  
|**smalldatetime**|DBTYPE_DBTIMESTAMP|  
|**smallint**|DBTYPE_I2|  
|**smallmoney**|DBTYPE_CY|  
|**sql_variant**|DBTYPE_VARIANT, DBTYPE_SQLVARIANT|  
|**sysname**|DBTYPE_WSTR|  
|**text**|DBTYPE_STR|  
|**timestamp**|DBTYPE_BYTES|  
|**tinyint**|DBTYPE_UI1|  
|**UDT**|DBTYPE_UDT|  
|**uniqueidentifier**|DBTYPE_GUID|  
|**varbinary**|DBTYPE_BYTES|  
|**varchar**|DBTYPE_STR|  
|**XML**|DBTYPE_XML|  
  
 Драйвер OLE DB для SQL Server поддерживает данные, запрашиваемые потребителем преобразования, как показано на рисунке.  
  
 Объекты **sql_variant** могут хранить данные [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] любого типа, кроме text, ntext, image, varchar(max), nvarchar(max), varbinary(max), xml, timestamp и пользовательских типов данных CLR платформы Microsoft .NET Framework. Экземпляр данных sql_variant не может также иметь sql_variant в качестве базового типа данных. Например, столбец может содержать значения **smallint** в некоторых строках, значения **float** в других строках и значения **char**/**nchar** в остальных.  
  
> [!NOTE]  
>  Тип данных **sql_variant** аналогичен типу данных Variant в Microsoft Visual Basic® и типу данных DBTYPE_VARIANT, DBTYPE_SQLVARIANT в OLEDB.  
  
 Если данные **sql_variant** получены как DBTYPE_VARIANT, они размещаются в структуре VARIANT в буфере. Однако подтипы в структуре VARIANT могут не соответствовать подтипам, определенным в типе данных **sql_variant**. Затем данные **sql_variant** должны быть выбраны как DBTYPE_SQLVARIANT для сопоставления всех подтипов.  
  
## <a name="dbtypesqlvariant-data-type"></a>Тип данных DBTYPE_SQLVARIANT  
 Для поддержки типа данных **sql_variant** драйвер OLE DB для SQL Server предоставляет специфический для поставщика тип данных, называемый DBTYPE_SQLVARIANT. Если данные **sql_variant** получены как DBTYPE_SQLVARIANT, они размещаются в специфической для поставщика структуре SSVARIANT. Структура SSVARIANT содержит все подтипы, сопоставленные с подтипами типа данных **sql_variant**.  
  
 Свойство сеанса SSPROP_ALLOWNATIVEVARIANT должно быть равно true.  
  
## <a name="provider-specific-property-sspropallownativevariant"></a>Специфическое для поставщика свойство SSPROP_ALLOWNATIVEVARIANT  
 При выборке данных можно явно указать разновидность типа данных, которые должны быть возвращены для столбца или для параметра. Интерфейс **IColumnsInfo** может также использоваться с целью получения сведений о столбце и их применения для привязки. Если интерфейс **IColumnsInfo** используется для получения сведений о столбце с целью привязки, а свойство сеанса SSPROP_ALLOWNATIVEVARIANT имеет значение FALSE (по умолчанию), для столбцов **sql_variant** возвращается DBTYPE_VARIANT. Если свойство SSPROP_ALLOWNATIVEVARIANT имеет значение FALSE, DBTYPE_SQLVARIANT не поддерживается. Если свойство SSPROP_ALLOWNATIVEVARIANT имеет значение TRUE, возвращается тип столбца DBTYPE_SQLVARIANT. В этом случае в буфере сохраняется структура SSVARIANT. При выборке данных **sql_variant** как данных типа DBTYPE_SQLVARIANT свойство сеанса SSPROP_ALLOWNATIVEVARIANT должно быть равно TRUE.  
  
 Свойство SSPROP_ALLOWNATIVEVARIANT является частью специфического для поставщика набора свойств DBPROPSET_SQLSERVERSESSION и свойством сеанса.  
  
 DBTYPE_VARIANT применяется ко всем другим поставщикам OLE DB.  
  
## <a name="sspropallownativevariant"></a>Свойство SSPROP_ALLOWNATIVEVARIANT  
 Свойство SSPROP_ALLOWNATIVEVARIANT является свойством сеанса и частью набора свойств DBPROPSET_SQLSERVERSESSION.  
  
|||  
|-|-|  
|Свойство SSPROP_ALLOWNATIVEVARIANT|Тип: VT_BOOL<br /><br /> И запись: чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание: определяет, имеют ли данные, полученные в результате выборки, тип DBTYPE_VARIANT или DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE: возвращается тип столбца DBTYPE_SQLVARIANT. В этом случае в буфере сохраняется структура SSVARIANT.<br /><br /> VARIANT_FALSE: возвращается столбец типа DBTYPE_VARIANT, и в буфере сохраняется структура VARIANT.|  
  
## <a name="see-also"></a>См. также:  
 [Типы данных &#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
