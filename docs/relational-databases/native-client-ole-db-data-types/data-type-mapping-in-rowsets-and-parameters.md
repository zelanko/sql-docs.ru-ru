---
title: Сопоставление типов данных в наборах строк и параметрах | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- DBTYPE_SQLVARIANT data type
- SQL Server Native Client OLE DB provider, data types
- rowsets [OLE DB], data type mapping
- data types [OLE DB]
- GetColumnInfo function
- parameters [OLE DB]
- SSPROP_ALLOWNATIVEVARIANT property
- GetParameterInfo function
- OLE DB, data types
ms.assetid: 3d831ff8-3b79-4698-b2c1-2b5dd2f8235c
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ea9322153c59e3d83e07504236df82b0aa7b3272
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413963"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a>Сопоставление типов данных в наборах строк и параметрах
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В наборах строк и значения параметра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] представляет поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных с помощью следующей OLE DB определенных типов данных, сообщаемых в функциях **IColumnsInfo::GetColumnInfo** и  **ICommandWithParameters::GetParameterInfo**.  
  
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
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает данные, запрашиваемые потребителем преобразования, как показано на рисунке.  
  
 **Sql_variant** объектов может содержать данные любого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных, кроме text, ntext, изображение, varchar(max), nvarchar(max), varbinary(max), xml, timestamp и Microsoft .NET Framework среда CLR (CLR) определяемые пользователем типы. Экземпляр данных sql_variant не может также иметь sql_variant в качестве базового типа данных. Например, столбец может содержать **smallint** для некоторых строк значения **float** значений для других строк, и **char**/**nchar**значения в остальных.  
  
> [!NOTE]  
>  **Sql_variant** подобен типу данных в тип данных Variant в Microsoft Visual Basic® и DBTYPE_VARIANT, DBTYPE_SQLVARIANT в OLEDB.  
  
 Когда **sql_variant** данные получены как DBTYPE_VARIANT, они размещаются в структуре VARIANT в буфере. Но подтипы в структуре VARIANT могут не соответствовать подтипам, определенным в **sql_variant** тип данных. **Sql_variant** данных должны быть выбраны как DBTYPE_SQLVARIANT в порядке все подтипы для сопоставления.  
  
## <a name="dbtypesqlvariant-data-type"></a>Тип данных DBTYPE_SQLVARIANT  
 Для поддержки **sql_variant** тип данных, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента предоставляет тип поставщика данных, называемый DBTYPE_SQLVARIANT. Когда **sql_variant** данные извлекаются в как DBTYPE_SQLVARIANT, они сохраняются в структуру SSVARIANT поставщика. Структура SSVARIANT содержит все подтипы подтипами **sql_variant** тип данных.  
  
 Свойство сеанса SSPROP_ALLOWNATIVEVARIANT должно быть равно true.  
  
## <a name="provider-specific-property-sspropallownativevariant"></a>Специфическое для поставщика свойство SSPROP_ALLOWNATIVEVARIANT  
 При выборке данных можно явно указать разновидность типа данных, которые должны быть возвращены для столбца или для параметра. **IColumnsInfo** также можно получить сведения о столбце и использовать его для привязки. Когда **IColumnsInfo** используется для получения сведения о столбце для привязки, если свойство сеанса SSPROP_ALLOWNATIVEVARIANT имеет значение FALSE (значение по умолчанию), возвращается DBTYPE_VARIANT **sql_variant**столбцов. Если свойство SSPROP_ALLOWNATIVEVARIANT имеет значение FALSE, DBTYPE_SQLVARIANT не поддерживается. Если свойство SSPROP_ALLOWNATIVEVARIANT имеет значение TRUE, возвращается тип столбца DBTYPE_SQLVARIANT. В этом случае в буфере сохраняется структура SSVARIANT. При выборке **sql_variant** данных как DBTYPE_SQLVARIANT свойство сеанса SSPROP_ALLOWNATIVEVARIANT должно быть присвоено значение TRUE.  
  
 Свойство SSPROP_ALLOWNATIVEVARIANT является частью специфического для поставщика набора свойств DBPROPSET_SQLSERVERSESSION и свойством сеанса.  
  
 DBTYPE_VARIANT применяется ко всем другим поставщикам OLE DB.  
  
## <a name="sspropallownativevariant"></a>Свойство SSPROP_ALLOWNATIVEVARIANT  
 Свойство SSPROP_ALLOWNATIVEVARIANT является свойством сеанса и частью набора свойств DBPROPSET_SQLSERVERSESSION.  
  
|||  
|-|-|  
|Свойство SSPROP_ALLOWNATIVEVARIANT|Тип: VT_BOOL<br /><br /> И запись: чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание: Определяет, является ли данные, полученные в качестве DBTYPE_VARIANT или DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE: Тип столбца возвращается как DBTYPE_SQLVARIANT, в котором регистр буфера будет содержать структура SSVARIANT.<br /><br /> VARIANT_FALSE: Тип столбца возвращается DBTYPE_VARIANT и буфера будет иметь структура VARIANT.|  
  
## <a name="see-also"></a>См. также  
 [Типы данных &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
