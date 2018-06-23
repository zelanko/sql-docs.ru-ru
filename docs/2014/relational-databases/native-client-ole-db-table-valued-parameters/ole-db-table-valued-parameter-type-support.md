---
title: Поддержка типов OLE DB табличное значение параметра | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4b6416715cc6226766773d3f1d630dc2e42e1e37
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180025"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>Поддержка типа возвращающего табличное значение параметра OLE DB
  Этот раздел содержит описание поддержки типа параметра OLE DB для параметров, возвращающих табличное значение.  
  
## <a name="table-valued-parameter-rowset-object"></a>Объект набора строк параметра, возвращающего табличное значение  
 Можно создать специальный объект набора строк для параметров, возвращающих табличное значение. Создание объекта набора строк возвращающего табличное значение параметра с помощью ITableDefinitionWithConstraints::CreateTableWithConstraints или IOpenRowset::OpenRowset. Чтобы сделать это, задайте *eKind* членом *pTableID* параметр в значение DBKIND_GUID_NAME и укажите CLSID_ROWSET_INMEMORY как *guid* член. Имя типа сервера для возвращающих табличные значения параметра необходимо указать в *pwszName* членом *pTableID* при использовании в идентификаторах. Объект набора строк параметра, возвращающего табличное значение, действует так же, как объект поставщика OLE DB собственного клиента для SQL Server.  
  
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
  
 Прямые и обратные преобразования в тип DBTYPE_TABLE для каких-либо других типов не поддерживаются. IConvertType::CanConvert возвращает значение S_FALSE для неподдерживаемого преобразования применительно к любому запросу, отличному от преобразования DBTYPE_TABLE. Это предполагает использование параметра DBCONVERTFLAGS_PARAMETER объекта команды.  
  
## <a name="methods"></a>Методы  
 Сведения о методах OLE DB, которые поддерживают возвращающие табличные значения параметров см. в разделе [OLE DB Table-Valued параметр типа поддерживает &#40;методы&#41;](ole-db-table-valued-parameter-type-support-methods.md).  
  
## <a name="properties"></a>Свойства  
 Сведения о свойствах свойства OLE DB, которые поддерживают возвращающие табличные значения параметров, в разделе [OLE DB Table-Valued параметр типа поддерживает &#40;свойства&#41;](ole-db-table-valued-parameter-type-support-properties.md).  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметров &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  