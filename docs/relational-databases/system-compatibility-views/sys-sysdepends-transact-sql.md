---
description: sys.sysdepends (Transact-SQL)
title: sys.sysзависит (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysdepends_TSQL
- sysdepends
- sysdepends_TSQL
- sys.sysdepends
dev_langs:
- TSQL
helpviewer_keywords:
- sysdepends system table
- sys.sysdepends compatibility view
ms.assetid: f9c182cb-386f-4e72-859f-9f1115b389f9
author: rothja
ms.author: jroth
ms.openlocfilehash: 31842603ba31d2ff6b7e631f0652b1f86da469c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427916"
---
# <a name="syssysdepends-transact-sql"></a>sys.sysdepends (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Содержит данные о зависимостях между объектами (представлениями, процедурами и триггерами) в базе данных и объектами (таблицы, представления и процедуры), которые содержатся в их определениях.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор объекта.|  
|**depid**|**int**|Идентификатор зависимого объекта.|  
|**number**|**smallint**|Номер процедуры.|  
|**depnumber**|**smallint**|Номер зависимой процедуры.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**deptype**|**tinyint**|Определяет тип зависимого объекта:<br /><br /> 0 = объект или столбец (только ссылки, не связанные со схемами);<br /><br /> 1 = объект или столбец (ссылки, связанные со схемами);|  
|**depdbid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**depsiteid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**selall**|**bit**|1 = Объект используется в инструкции SELECT *.<br /><br /> 0 = Нет.|  
|**resultobj**|**bit**|1 = Объект обновляется.<br /><br /> 0 = Нет.|  
|**readobj**|**bit**|1 = Объект производит считывание.<br /><br /> 0 = Нет.|  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление системных таблиц с системными представлениями &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [sp_depends &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-depends-transact-sql.md)   
 [sys. sql_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)  
  
  
