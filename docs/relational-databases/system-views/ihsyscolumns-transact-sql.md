---
title: Ихсисколумнс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHsyscolumns
- IHsyscolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHsyscolumns view
ms.assetid: 263452f1-9708-48f0-9536-402a89e7f5bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: a965be50e45300aeca3ba158251c665e8204a6f2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736667"
---
# <a name="ihsyscolumns-transact-sql"></a>IHsyscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Представление **ихсисколумнс** предоставляет сведения о столбцах для статей, опубликованных на издателе, отличном от SQL Server. Это представление хранится в DistributionDatabase.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя столбца или параметра процедуры.|  
|**идентификатор**|**int**|Идентификатор объекта таблицы, к которой принадлежит столбец, или идентификатор хранимой процедуры, с которой данный параметр ассоциирован.|  
|**xtype**|**tinyint**|Тип физического хранилища из [типовsys.sys&#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**typestat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**tinyint**|Идентификатор расширенного определяемого пользователем типа данных.|  
|**length**|**bigint**|Максимальная длина физического хранилища [sys.sysтипов &#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**xprec**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xscale**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**идентификатора столбца**|**int**|Идентификатор столбца или параметра.|  
|**xoffset**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**процессу**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|Идентификатор значения по умолчанию для этого столбца.|  
|**поддомен**|**int**|Идентификатор правила или ограничения CHECK для этого столбца.|  
|**number**|**int**|Номер подпроцедуры при группировании процедуры (**0** для непроцедурных записей).|  
|**colorder**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**int**|Сдвиг в строке, в которой встречается этот столбец.|  
|**коллатионид**|**int**|Идентификатор параметров сортировки столбца. Значение NULL для несимвольных столбцов.|  
|**language**|**int**|Идентификатор языка для столбца.|  
|**status**|**int**|Битовая карта, используемая для описания свойства столбца или параметра:<br /><br /> **0x08** = столбец допускает значения NULL.<br /><br /> **0x10** = заполнение ANSI было применено при добавлении столбцов **varchar** или **varbinary** . Замыкающие пробелы сохраняются для **varchar** , а замыкающие нули сохраняются для столбцов типа **varbinary** .<br /><br /> **0x40** = параметр является выходным.<br /><br /> **0x80** = столбец является столбцом идентификаторов.|  
|**type**|**int**|Тип физического хранилища из [типовsys.sys&#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**usertype**|**tinyint**|Идентификатор определяемого пользователем типа данных из [sys.sysтипов &#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**printfmt**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**прек**|**int**|Степень точности для данного столбца.|  
|**масштаб**|**int**|Шкала для данного столбца.|  
|**вычислено**|**int**|Признак, по которому определяется, является ли столбец вычисляемым:<br /><br /> **0** = невычисленный.<br /><br /> **1** = вычисленный.|  
|**исаутпарам**|**int**|Указывает, относится ли параметр процедуры к выходным параметрам:<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**IsNullable**|**int**|Указывает, допускает ли столбец значения NULL:<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**параметры сортировки**|**int**|Имя параметров сортировки столбца. Значение NULL для несимвольных столбцов.|  
|**tdscollation**|**int**|Имя параметров сортировки столбца при возвращении в поток табличных данных (TDS).|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
