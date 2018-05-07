---
title: sys.syscolumns (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-enginel, sql-data-warehouse, pdw
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.syscolumns
- sys.syscolumns_TSQL
- syscolumns_TSQL
- syscolumns
dev_langs:
- TSQL
helpviewer_keywords:
- syscolumns system table
- sys.syscolumns compatibility view
ms.assetid: 863fd87b-ff33-4ac5-9aa9-df21140681da
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ab6fb39894c7cbe10be6d00d5fc74e782ca5650e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="syssyscolumns-transact-sql"></a>sys.syscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Возвращает по одной строке на каждый из столбцов всех таблиц и представлений и по одной строке на каждый из параметров хранимых процедур в базе данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя столбца или параметра процедуры.|  
|**идентификатор**|**int**|Идентификатор объекта таблицы, которому принадлежит столбец, или идентификатор хранимой процедуры, с которой связан данный параметр.|  
|**xtype**|**tinyint**|Тип физического хранилища из **sys.types**.|  
|**typestat**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|Идентификатор расширенного пользовательского типа. Вызывает переполнение или возвращает значение NULL, если количество типов данных превышает 32 767.|  
|**длина**|**smallint**|Максимальная длина физического хранилища из **sys**. **типы**.|  
|**xprec**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**XScale**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**идентификатора столбца**|**smallint**|Идентификатор столбца или параметра.|  
|**xoffset**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Зарезервировано**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|Идентификатор значения по умолчанию для данного столбца.|  
|**Домен**|**int**|Идентификатор правила или ограничения CHECK для данного столбца.|  
|**number**|**smallint**|Номер подпроцедуры, если процедура сгруппирована:<br /><br /> 0 = Непроцедурные элементы.|  
|**colorder**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**varbinary(8000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**smallint**|Смещение в строке, по которому находится данный столбец.|  
|**collationid**|**int**|Идентификатор параметров сортировки для столбца. Для несимвольных столбцов содержит значение NULL.|  
|**status**|**tinyint**|Битовая карта, описывающая свойства столбца или параметра:<br /><br /> 0x08 = В столбце допускаются значения NULL;<br /><br /> 0x10 = заполнение символами ANSI был в силу, если **varchar** или **varbinary** были добавлены столбцы. Замыкающие пробелы сохраняются для **varchar** и замыкающие нули сохраняются для **varbinary** столбцов.<br /><br /> 0x40 = Параметр OUTPUT;<br /><br /> 0x80 = Столбец является столбцом идентификаторов.|  
|**type**|**tinyint**|Тип физического хранилища из **sys**. **типы**.|  
|**usertype**|**smallint**|Идентификатор определяемого пользователем типа из **sys.types**. Вызывает переполнение или возвращает значение NULL, если количество типов данных превышает 32 767.|  
|**printfmt**|**varchar(255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**smallint**|Уровень точности для данного столбца:<br /><br /> -1 = **xml** или тип больших значений.|  
|**масштаб**|**int**|Масштаб для данного столбца.<br /><br /> NULL = данные не числовые.|  
|**iscomputed**|**int**|Флаг, обозначающий, является ли столбец вычисляемым:<br /><br /> 0 = невычисляемый;<br /><br /> 1 = вычисляемый.|  
|**isoutparam**|**int**|Указывает, относится ли параметр процедуры к выходным параметрам:<br /><br /> 1 = True<br /><br /> 0 = False.|  
|**IsNullable**|**int**|Указывает, допускает ли столбец значения NULL:<br /><br /> 1 = True<br /><br /> 0 = False.|  
|**Параметры сортировки**|**sysname**|Имя параметров сортировки для данного столбца. Содержит NULL, если столбец не относится к символьному типу.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
