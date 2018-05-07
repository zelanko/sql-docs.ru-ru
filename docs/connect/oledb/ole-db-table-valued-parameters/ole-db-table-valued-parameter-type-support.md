---
title: Поддержка типов OLE DB табличное значение параметра | Документы Microsoft
description: Поддержка типов параметров OLE DB Table-Valued
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 8f1a20a09e4c15b0dbe84352a4bfbbef59b5d784
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-table-valued-parameter-type-support"></a>Поддержка типа возвращающего табличное значение параметра OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этой статье описывается поддержка типов OLE DB для возвращающей табличное значение параметров.  
  
## <a name="table-valued-parameter-rowset-object"></a>Объект набора строк параметра, возвращающего табличное значение  
 Можно создать специальный объект набора строк для параметров, возвращающих табличное значение. Создание объекта набора строк возвращающего табличное значение параметра с помощью ITableDefinitionWithConstraints::CreateTableWithConstraints или IOpenRowset::OpenRowset. Чтобы сделать это, задайте *eKind* членом *pTableID* параметр в значение DBKIND_GUID_NAME и укажите CLSID_ROWSET_INMEMORY как *guid* член. Имя типа сервера для возвращающих табличные значения параметра необходимо указать в *pwszName* членом *pTableID* при использовании в идентификаторах. Объект набора строк возвращающего табличное значение параметра ведет себя как обычный драйвер OLE DB для SQL Server объекта.  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtypetable"></a>DBTYPE_TABLE  
 Новый тип, DBTYPE_TABLE, представляет собой табличный тип. Этот тип описывает возвращающие табличное значение параметры в различных интерфейсах OLE DB, где требуется тип DBTYPE.  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 DBTYPE_TABLE имеет такой же формат, что и DBTYPE_IUNKNOWN. Представляет собой указатель на объект в буфере данных. Определить полную спецификацию в привязках, пользователь заполняет буфер DBOBJECT *iid* задать один из интерфейсов объекта набора строк (IID_IRowset). Если DBOBJECT не указан в привязках, будет считаться IID_IRowset.  
  
 Преобразования в и из DBTYPE_TABLE для любых других типов не поддерживаются. IConvertType::CanConvert возвращает значение S_FALSE для неподдерживаемого преобразования применительно к любому запросу, отличному от преобразования DBTYPE_TABLE. Это предполагает использование параметра DBCONVERTFLAGS_PARAMETER объекта команды.  
  
## <a name="methods"></a>Методы  
 Сведения о методах OLE DB, которые поддерживают возвращающие табличные значения параметров см. в разделе [OLE DB Table-Valued параметр типа поддерживает &#40;методы&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md).  
  
## <a name="properties"></a>Свойства  
 Сведения о свойствах OLE DB, которые поддерживают возвращающие табличные значения параметров см. в разделе [OLE DB Table-Valued параметр типа поддерживает &#40;свойства&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md).  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметров &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметры & #40; OLE DB & #41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
