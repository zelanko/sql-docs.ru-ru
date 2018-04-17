---
title: ДОМЕНЫ (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-information-schema-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DOMAINS_TSQL
- DOMAINS
dev_langs:
- TSQL
helpviewer_keywords:
- DOMAINS view
- INFORMATION_SCHEMA.DOMAINS view
ms.assetid: f0b734d5-816f-4b10-a60c-615931b515c2
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a13c0a859b642c272a99b2a935b41933b558578d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="domains-transact-sql"></a>DOMAINS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает одну строку для каждого псевдонима типа данных, которые доступны текущему пользователю в текущей базе данных.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA. *** view_name*.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**DOMAIN_CATALOG**|**nvarchar (**128**)**|База данных, в которой существует псевдоним типа данных.|  
|**DOMAIN_SCHEMA**|**nvarchar (**128**)**|Имя схемы, содержащей псевдоним типа данных.<br /><br /> **\*\* Важные \* \***  не используйте представления INFORMATION_SCHEMA, чтобы определить схему типа данных. Единственный надежный способ найти схему типа — использовать функцию TYPEPROPERTY.|  
|**ИМЯ_ДОМЕНА**|**sysname**|Псевдоним типа данных.|  
|**ТИП ДАННЫХ**|**sysname**|Тип данных, поддерживаемый системой.|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|Максимальная длина в символах для двоичных данных, символьных данных или текстовых данных и изображений.<br /><br /> -1 для **xml** и данные типов больших значений. Иначе возвращается значение NULL. Дополнительные сведения см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md).|  
|**CHARACTER_OCTET_LENGTH**|**int**|Максимальная длина в байтах для двоичных данных, символьных данных или текстовых данных и изображений.<br /><br /> -1 для **xml** и данные типов больших значений. Иначе возвращается значение NULL.|  
|**COLLATION_CATALOG**|**varchar (**6**)**|Всегда возвращает значение NULL.|  
|**COLLATION_SCHEMA**|**varchar (**3**)**|Всегда возвращает значение NULL.|  
|**COLLATION_NAME**|**nvarchar (**128**)**|Возвращает уникальное имя для порядка сортировки, если столбец содержит символьные данные или **текст** тип данных. Иначе возвращается значение NULL.|  
|**CHARACTER_SET_CATALOG**|**varchar (**6**)**|Возвращает **master**. Это указывает базу данных, в которой находится кодировка, если столбец содержит символьные данные или **текст** тип данных. Иначе возвращается значение NULL.|  
|**CHARACTER_SET_SCHEMA**|**varchar (**3**)**|Всегда возвращает значение NULL.|  
|**CHARACTER_SET_NAME**|**nvarchar (**128**)**|Возвращает уникальное имя для кодировки, если столбец содержит символьные данные или **текст** тип данных. Иначе возвращается значение NULL.|  
|**NUMERIC_PRECISION**|**tinyint**|Точность приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Основание системы счисления точности приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|  
|**NUMERIC_SCALE**|**tinyint**|Масштаб приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|  
|**DATETIME_PRECISION**|**smallint**|Код подтипа для **datetime** и ISO **интервал** тип данных. Для других типов данных этот столбец возвращает значение NULL.|  
|**DOMAIN_DEFAULT**|**nvarchar (**4000**)**|Действительный текст определения инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.syscharsets &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [sys.types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  
