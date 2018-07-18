---
title: Набор строк DBSCHEMA_COLUMNS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DBSCHEMA_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_COLUMNS rowset
ms.assetid: 653bdd07-a533-4a99-8b6a-6e5c7322e1f3
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6fa933eb153b0d8de4c2fec4ba92b072954be141
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267580"
---
# <a name="dbschemacolumns-rowset"></a>Набор строк DBSCHEMA_COLUMNS
  Предоставляет сведения обо всех столбцах, удовлетворяющих указанному критерию ограничения.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DBSCHEMA_COLUMNS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`||Имя базы данных.|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`||Не поддерживается.|  
|`TABLE_NAME`|`DBTYPE_WSTR`||Имя куба.|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||Имя иерархии атрибутов или меры.|  
|`COLUMN_GUID`|`DBTYPE_GUID`||Не поддерживается.|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||Не поддерживается.|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||Позиция столбца, начиная с 1.|  
|`COLUMN_HAS_DEFAULT`|`DBTYPE_BOOL`||Не поддерживается.|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||Не поддерживается.|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||Битовая маска `DBCOLUMNFLAGS`, указывающая свойства столбца. См. в разделе «DBCOLUMNFLAGS перечисляемый тип» в [IColumnsInfo::GetColumnInfo](http://msdn2.microsoft.com/library/ms722704.aspx)|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Всегда возвращает `false`.|  
|`DATA_TYPE`|`DBTYPE_WSTR`<br /><br /> `DBTYPE_VARIANT`||Тип данных столбца. Возвращает значения типа String для столбцов измерений и значения типа Variant для мер.|  
|`TYPE_GUID`|`DBTYPE_GUID`||Не поддерживается.|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||Максимально возможная длина значения в пределах столбца.<br /><br /> Эти данные извлекаются из свойства `DataSize` в `DataItem`.|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||Максимальная возможная длина в байтах значения в столбце для символьных или двоичных столбцов.<br /><br /> Нулевое значение (0) указывает, что для столбца максимальная длина не задана.<br /><br /> Происходит возврат значения `NULL` для столбцов, которые не возвращают двоичный или символьный типы данных.|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||Максимальная точность столбца для числовых типов данных, отличных от `DBTYPE_VARNUMERIC`.|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||Количество цифр справа от десятичного разделителя для `DBTYPE_DECIMAL`, `DBTYPE_NUMERIC`, `DBTYPE_VARNUMERIC`. В противном случае значение `NULL`.|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||Не поддерживается.|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||Не поддерживается.|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||Не поддерживается.|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||Не поддерживается.|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||Не поддерживается.|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||Не поддерживается.|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||Не поддерживается.|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||Не поддерживается.|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||Не поддерживается.|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||Не поддерживается.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Не поддерживается.|  
|`COLUMN_OLAP_TYPE`|`DBTYPE_WSTR`||Тип OLAP объекта.<br /><br /> Параметр `MEASURE` указывает, что объект — мера.<br /><br /> Параметр `ATTRIBUTE` указывает, что объект — атрибут измерения.<br /><br /> `SCHEMA` указывает, что объект представляет собой столбец в схеме.|  
  
 Набор строк отсортирован по `TABLE_CATALOG`, `TABLE_SCHEMA`, `TABLE_NAME`.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DBSCHEMA_COLUMNS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|Необязательно|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|Необязательно|  
|`TABLE_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`COLUMN_OLAP_TYPE`|`DBTYPE_WSTR`|Необязательно|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB](ole-db-schema-rowsets.md)  
  
  
