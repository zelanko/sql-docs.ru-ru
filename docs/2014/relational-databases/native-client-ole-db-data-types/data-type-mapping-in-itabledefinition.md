---
title: Сопоставление типов данных в интерфейсе ITableDefinition | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c09ac0e561f06236a9580ae7a84ed892ca1fcd31
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099983"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Сопоставление типов данных в интерфейсе ITableDefinition
  При создании таблицы с помощью **ITableDefinition::CreateTable** функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителем поставщика OLE DB для собственного клиента можно указать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных в *pwszTypeName* элемент массива DBCOLUMNDESC, передается. Если потребитель указывает тип данных столбца по имени, тип данных OLE DB сопоставление, представленное *wType* структуры DBCOLUMNDESC, учитывается.  
  
 При указании новых типов данных столбцов с типами данных OLE DB с помощью структуры DBCOLUMNDESC *wType* член, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента сопоставляет типы данных OLE DB, как показано ниже.  
  
|Тип данных OLE DB|SQL Server<br /><br /> тип данных|Дополнительные сведения|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**двоичный**, **varbinary**, **изображения,** или **varbinary(max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента проверяет *ulColumnSize* структуры DBCOLUMNDESC. На основе значения и версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **изображения**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина **двоичных** столбец типа данных, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента проверяет структуры DBCOLUMNDESC  *rgPropertySets* член. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **двоичных**. Если значение свойства равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **varbinary**. В любом случае структуры DBCOLUMNDESC *ulColumnSize* определяет ширину создаваемого столбца SQL Server.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента проверяет элемент DBCOLUMDESC *bPrecision* и *bScale* членов, чтобы определить точность и масштаб для **числовых** столбец.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **текста,** или **varchar(max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента проверяет *ulColumnSize* структуры DBCOLUMNDESC. На основе значения и версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **текст**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа данных Многобайтовый символ, а затем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента проверяет структуры DBCOLUMNDESC *rgPropertySets*член. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **char**. Если значение свойства равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **varchar**. В любом случае структуры DBCOLUMNDESC *ulColumnSize* определяет ширину [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создан столбец.|  
|DBTYPE_UDT|**UDT**|Следующие сведения используются в `DBCOLUMNDESC` структуры по **ITableDefinition::CreateTable** при необходимы столбцы определяемого пользователем ТИПА:<br /><br /> -   *pwSzTypeName* учитывается.<br />-   *rgPropertySets* должен включать `DBPROPSET_SQLSERVERCOLUMN` свойства, как это описано в разделе на `DBPROPSET_SQLSERVERCOLUMN`в [Using User-Defined типов](../native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext,** или **nvarchar(max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента проверяет *ulColumnSize* структуры DBCOLUMNDESC. На основе значения, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **ntext**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа данных символов Юникода, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента проверяет структуры DBCOLUMNDESC *rgPropertySets*член. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **nchar**. Если значение свойства равно VARIANT_FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента сопоставляет тип для **nvarchar**. В любом случае структуры DBCOLUMNDESC *ulColumnSize* определяет ширину [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создан столбец.|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  При создании новой таблицы поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сопоставляет только значения перечислений типов данных OLE DB, указанные в предшествующей таблице. Попытка создать таблицу со столбцом любого другого типа данных OLE DB приводит к ошибке.  
  
## <a name="see-also"></a>См. также  
 [Типы данных &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  