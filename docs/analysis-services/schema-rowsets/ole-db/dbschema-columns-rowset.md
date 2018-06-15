---
title: Набор строк DBSCHEMA_COLUMNS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2bb1fec6a1633f545f0c65feda93c7e19c649a6e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34029695"
---
# <a name="dbschemacolumns-rowset"></a>Набор строк DBSCHEMA_COLUMNS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Предоставляет сведения обо всех столбцах, удовлетворяющих указанному критерию ограничения.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **DBSCHEMA_COLUMNS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**ЗНАЧЕНИЯМ TABLE_CATALOG**|**DBTYPE_WSTR**||Имя базы данных.|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**||Не поддерживается.|  
|**ИМЯ_ТАБЛИЦЫ**|**DBTYPE_WSTR**||Имя куба.|  
|**COLUMN_NAME**|**DBTYPE_WSTR**||Имя иерархии атрибутов или меры.|  
|**COLUMN_GUID**|**DBTYPE_GUID**||Не поддерживается.|  
|**COLUMN_PROPID**|**DBTYPE_UI4**||Не поддерживается.|  
|**ORDINAL_POSITION**|**DBTYPE_UI4**||Позиция столбца, начиная с 1.|  
|**COLUMN_HAS_DEFAULT**|**DBTYPE_BOOL**||Не поддерживается.|  
|**COLUMN_DEFAULT**|**DBTYPE_WSTR**||Не поддерживается.|  
|**COLUMN_FLAGS**|**DBTYPE_UI4**||Объект **DBCOLUMNFLAGS** Битовая маска, указывающая свойства столбца. В разделе «DBCOLUMNFLAGS перечисляемый тип» в [IColumnsInfo::GetColumnInfo](http://msdn2.microsoft.com/library/ms722704.aspx)|  
|**IS_NULLABLE**|**DBTYPE_BOOL**||Всегда возвращает **false**.|  
|**ТИП ДАННЫХ**|**DBTYPE_WSTR**<br /><br /> **DBTYPE_VARIANT**||Тип данных столбца. Возвращает значения типа String для столбцов измерений и значения типа Variant для мер.|  
|**TYPE_GUID**|**DBTYPE_GUID**||Не поддерживается.|  
|**CHARACTER_MAXIMUM_LENGTH**|**DBTYPE_UI4**||Максимально возможная длина значения в пределах столбца.<br /><br /> Эти данные извлекаются из **DataSize** свойство в **DataItem**.|  
|**CHARACTER_OCTET_LENGTH**|**DBTYPE_UI4**||Максимальная возможная длина в байтах значения в столбце для символьных или двоичных столбцов.<br /><br /> Нулевое значение (0) указывает, что для столбца максимальная длина не задана.<br /><br /> **Значение NULL** будет возвращаться для столбцов, которые не возвращают типы двоичных или символьных данных.|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**||Максимальная точность столбца для числовых данных типов, отличных от **DBTYPE_VARNUMERIC**.|  
|**NUMERIC_SCALE**|**DBTYPE_I2**||Количество цифр справа от десятичной запятой в **DBTYPE_DECIMAL**, **DBTYPE_NUMERIC**, **DBTYPE_VARNUMERIC**. В противном случае это **NULL**.|  
|**DATETIME_PRECISION**|**DBTYPE_UI4**||Не поддерживается.|  
|**CHARACTER_SET_CATALOG**|**DBTYPE_WSTR**||Не поддерживается.|  
|**CHARACTER_SET_SCHEMA**|**DBTYPE_WSTR**||Не поддерживается.|  
|**CHARACTER_SET_NAME**|**DBTYPE_WSTR**||Не поддерживается.|  
|**COLLATION_CATALOG**|**DBTYPE_WSTR**||Не поддерживается.|  
|**COLLATION_SCHEMA**|**DBTYPE_WSTR**||Не поддерживается.|  
|**COLLATION_NAME**|**DBTYPE_WSTR**||Не поддерживается.|  
|**DOMAIN_CATALOG**|**DBTYPE_WSTR**||Не поддерживается.|  
|**DOMAIN_SCHEMA**|**DBTYPE_WSTR**||Не поддерживается.|  
|**ИМЯ_ДОМЕНА**|**DBTYPE_WSTR**||Не поддерживается.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Не поддерживается.|  
|**COLUMN_OLAP_TYPE**|**DBTYPE_WSTR**||Тип OLAP объекта.<br /><br /> **МЕРЫ** указывает объект является мерой.<br /><br /> **АТРИБУТ** указывает объект атрибута измерения.<br /><br /> **СХЕМЫ** указывает столбец в схеме объекта.|  
  
 Набор строк отсортирован по **значениям TABLE_CATALOG**, **TABLE_SCHEMA**, **TABLE_NAME**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **DBSCHEMA_COLUMNS** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**ЗНАЧЕНИЯМ TABLE_CATALOG**|**DBTYPE_WSTR**|Необязательно|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|Необязательно|  
|**ИМЯ_ТАБЛИЦЫ**|**DBTYPE_WSTR**|Необязательно|  
|**COLUMN_NAME**|**DBTYPE_WSTR**|Необязательно|  
|**COLUMN_OLAP_TYPE**|**DBTYPE_WSTR**|Необязательно|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
