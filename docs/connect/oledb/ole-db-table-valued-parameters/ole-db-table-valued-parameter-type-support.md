---
title: Поддержка типов параметров OLE DB, возвращающих табличные значения | Документы Майкрософт
description: Поддержка типов параметров OLE DB, возвращающих табличные значения
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
author: pmasl
ms.author: pelopes
ms.openlocfilehash: abff9abb82ad0ff54d9b1126541b98babbd6bd76
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015280"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>Поддержка типа возвращающего табличное значение параметра OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В этой статье описывается поддержка типов OLE DB для параметров, возвращающих табличные значения.  
  
## <a name="table-valued-parameter-rowset-object"></a>Объект набора строк параметра, возвращающего табличное значение  
 Можно создать специальный объект набора строк для параметров, возвращающих табличное значение. Объект набора строк возвращающего табличное значение параметра создается с помощью Итабледефинитионвисконстраинтс:: Креатетаблевисконстраинтс или IOpenRowset:: OpenRowset. Для этого установите элемент *eKind* параметра *pTableID* в значение DBKIND_GUID_NAME и укажите CLSID_ROWSET_INMEMORY как элемент *guid*. Имя типа сервера для возвращающего табличное значение параметра должно быть указано в *pwszName* члене *PTableID* при использовании IOpenRowset:: OPENROWSET. Объект набора строк возвращающего табличное значение параметра ведет себя как обычный драйвер OLE DB для SQL Server объекта.  
  
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
  
 DBTYPE_TABLE имеет такой же формат, что и DBTYPE_IUNKNOWN. Представляет собой указатель на объект в буфере данных. Чтобы определить полную спецификацию в привязках, потребитель заполняет буфер DBOBJECT, задавая для параметра *iid* один из интерфейсов объекта набора строк (IID_IRowset). Если объект DBOBJECT в привязках не указан, то предполагается использование объекта IID_IRowset.  
  
 Прямые и обратные преобразования в тип DBTYPE_TABLE для каких-либо других типов не поддерживаются. Метод IConvertType::CanConvert возвращает значение S_FALSE для неподдерживаемого преобразования применительно к любому запросу, отличному от преобразования DBTYPE_TABLE в DBTYPE_TABLE. При этом предполагается использование параметра DBCONVERTFLAGS_PARAMETER объекта Command.  
  
## <a name="methods"></a>Методы  
 Дополнительные сведения о методах OLE DB, которые поддерживают возвращающие табличное значение параметры, OLE DB см. в разделе [методы &#40;&#41;поддержки типов](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)возвращающих табличное значение параметров.  
  
## <a name="properties"></a>Свойства  
 Дополнительные сведения о OLE DB свойствах, поддерживающих возвращающие табличное значение параметры, см. в разделе OLE DB тип возвращающего табличное значение [параметра Поддержка &#40;свойств&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Возвращающие табличные значения параметры &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
