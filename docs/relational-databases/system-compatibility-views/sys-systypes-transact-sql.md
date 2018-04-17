---
title: sys.systypes (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.systypes_TSQL
- systypes_TSQL
- sys.systypes
- systypes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.systypes compatibility view
- systypes system table
ms.assetid: 1b0b1d0c-5f7b-470b-bd52-8bfa922d7889
caps.latest.revision: 50
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ffbf54921f463e749d36b89985af5e5a98ef5518
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="syssystypes-transact-sql"></a>sys.systypes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает по одной строке для каждого из системных и определяемых пользователем типов данных, определенных в базе данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя типа данных.|  
|**xtype**|**tinyint**|Тип физического хранилища.|  
|**status**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|Расширенный пользовательский тип. Вызывает переполнение или возвращает значение NULL, если количество типов данных превышает 32 767.|  
|**длина**|**smallint**|Физическая длина типа данных.|  
|**xprec**|**tinyint**|Внутренняя точность, используемая сервером. Не для использования в запросах.|  
|**XScale**|**tinyint**|Внутренний масштаб, используемый сервером. Не для использования в запросах.|  
|**tdefault**|**int**|Идентификатор хранимой процедуры, содержащей проверку целостности для этого типа данных.|  
|**Домен**|**int**|Идентификатор хранимой процедуры, содержащей проверку целостности для этого типа данных.|  
|**UID**|**smallint**|Идентификатор схемы владельца типа.<br /><br /> Для баз данных, обновленных из предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Идентификатор схемы эквивалентен идентификатору владельца.<br /><br /> **\*\* Важные \* \***  при использовании одного из следующих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкции DDL, необходимо использовать [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) представления вместо каталога **sys.systypes**.<br /><br /> ALTER AUTHORIZATION ON TYPE<br /><br /> CREATE TYPE<br /><br /> Вызывает переполнение или возвращает значение NULL, если количество пользователей и ролей превышает 32 767.|  
|**Зарезервировано**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**collationid**|**int**|Для символьного **collationid** идентификатор параметров сортировки текущей базы данных; в противном случае возвращается значение NULL.|  
|**usertype**|**smallint**|Идентификатор пользовательского типа. Вызывает переполнение или возвращает значение NULL, если количество типов данных превышает 32 767.|  
|**variable**|**бит**|Тип данных с переменной длиной.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|**allownulls**|**бит**|Указывает для этого типа данных возможность принимать значения NULL по умолчанию. Это значение по умолчанию переопределяется, если допустимость значения NULL указана с помощью [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) или [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).|  
|**type**|**tinyint**|Тип данных физического хранилища.|  
|**printfmt**|**varchar(255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**smallint**|Уровень точности для этого типа данных.<br /><br /> -1 = **xml** или типы больших значений.|  
|**масштаб**|**tinyint**|Масштаб для этого типа данных на основе точности.<br /><br /> NULL = данные не числовые.|  
|**Параметры сортировки**|**sysname**|Для символьного **сортировки** являются параметры сортировки текущей базы данных; в противном случае возвращается значение NULL.|  
  
## <a name="see-also"></a>См. также  
 [Представления совместимости &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
