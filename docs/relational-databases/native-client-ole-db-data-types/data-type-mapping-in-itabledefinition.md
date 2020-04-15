---
title: Сопоставление типов данных в интерфейсе ITableDefinition | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d3e828efa513db1ace272e59379f77d063220290
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297088"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Сопоставление типов данных в интерфейсе ITableDefinition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  При создании таблиц с помощью функции **ITableDefinition::CreateTable** потребитель-поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB может указать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных в пройденных biszTypeName массива DBCOLUMNDESC. *pwszTypeName* Если потребитель указывает тип данных столбца по имени, то сопоставление типов OLE DB, представляемое элементом *wType* структуры DBCOLUMNDESC, не учитывается.  
  
 При указании новых типов данных столбцов с типами данных OLE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB с использованием структуры DBCOLUMNDESC *wType,* поставщик данных NATIVE Client OLE DB отображает данные OLE DB следующим образом.  
  
|Тип данных OLE DB|SQL Server<br /><br /> тип данных|Дополнительные сведения|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** или **varbinary(max)**|Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB проверяет участника *ulColumnSize,* являватого членом структуры DBCOLUMNDESC. Основываясь на значении и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, поставщик Native Client OLE DB отображает тип **изображения.**<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина **двоичного** столбца типа данных, то поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB проверяет участника DBCOLUMNDESC *rgPropertySets.* Если DBPROP_COL_FIXEDLENGTH VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB отображает тип **двоичного.** Если стоимость имущества VARIANT_FALSE, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB отображает тип **varbinary.** В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца SQL Server.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**UNIQUEIDENTIFIER**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**INT**||  
|DBTYPE_NUMERIC|**Числовые**|Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB проверяет участников DBCOLUMDESC *bPrecision* и *bScale* для определения точности и масштаба **цифрового** столбца.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**FLOAT**||  
|DBTYPE_STR|**char**, **varchar**, **text** или **varchar(max)**|Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB проверяет участника *ulColumnSize,* являватого членом структуры DBCOLUMNDESC. Основываясь на значении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и версии экземпляра, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client OLE DB отображает тип **текста.**<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа данных мультибайт, то поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB проверяет участника DBCOLUMNDESC *rgPropertySets.* Если DBPROP_COL_FIXEDLENGTH VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB отображает тип для **char.** Если стоимость имущества VARIANT_FALSE, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client OLE DB отображает тип **varchar.** В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|DBTYPE_UDT|**Udt**|Следующие сведения используются в структурах **DBCOLUMNDESC**, применяемых методом **ITableDefinition::CreateTable**, когда требуются столбцы пользовательских типов:<br /><br /> *pwSzTypeName* игнорируется.<br /><br /> Свойство *rgPropertySets* должно включать набор свойств **DBPROPSET_SQLSERVERCOLUMN**, как описано в пункте **DBPROPSET_SQLSERVERCOLUMN** раздела [Использование определяемых пользователем типов](../../relational-databases/native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** или **nvarchar(max)**|Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB проверяет участника *ulColumnSize,* являватого членом структуры DBCOLUMNDESC. Основываясь на значении, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB отображает тип к **ntext.**<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных символов Unicode, то поставщик Native Client OLE DB проверяет участника DBCOLUMNDESC *rgPropertySets.* Если DBPROP_COL_FIXEDLENGTH VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB отображает тип **nchar.** Если стоимость имущества VARIANT_FALSE, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client OLE DB отображает тип **nvarchar.** В любом случае элемент *ulColumnSize* структуры DBCOLUMNDESC определяет ширину создаваемого столбца [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|DBTYPE_XML|**Xml**||  
  
> [!NOTE]  
>  При создании новой таблицы поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сопоставляет только значения перечислений типов данных OLE DB, указанные в предшествующей таблице. Попытка создать таблицу со столбцом любого другого типа данных OLE DB приводит к ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (OLE DB)](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
