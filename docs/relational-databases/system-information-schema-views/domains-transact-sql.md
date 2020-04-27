---
title: ДОМЕны (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cb602bf26b20ea916a46655cf813f4c1a6ab4f1b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67950738"
---
# <a name="domains-transact-sql"></a>DOMAINS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает одну строку для каждого псевдонима типа данных, которые доступны текущему пользователю в текущей базе данных.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA.** _view_name_.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**DOMAIN_CATALOG**|**nvarchar (** 128 **)**|База данных, в которой существует псевдоним типа данных.|  
|**DOMAIN_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей псевдоним типа данных.<br /><br /> **&#42;&#42; важно &#42;&#42;** Не используйте INFORMATION_SCHEMA представления для определения схемы типа данных. Единственный надежный способ найти схему типа — использовать функцию TYPEPROPERTY.|  
|**DOMAIN_NAME**|**sysname**|Псевдоним типа данных.|  
|**DATA_TYPE**|**sysname**|Тип данных, поддерживаемый системой.|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|Максимальная длина в символах для двоичных данных, символьных данных или текстовых данных и изображений.<br /><br /> -1 для данных типа **XML** и больших значений. Иначе возвращается значение NULL. Дополнительные сведения см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md).|  
|**CHARACTER_OCTET_LENGTH**|**int**|Максимальная длина в байтах для двоичных данных, символьных данных или текстовых данных и изображений.<br /><br /> -1 для данных типа **XML** и больших значений. Иначе возвращается значение NULL.|  
|**COLLATION_CATALOG**|**varchar (** 6 **)**|Всегда возвращает значение NULL.|  
|**COLLATION_SCHEMA**|**varchar (** 3 **)**|Всегда возвращает значение NULL.|  
|**COLLATION_NAME**|**nvarchar (** 128 **)**|Возвращает уникальное имя для порядка сортировки, если столбец имеет символьные данные или **текстовый** тип данных. Иначе возвращается значение NULL.|  
|**CHARACTER_SET_CATALOG**|**varchar (** 6 **)**|Возвращает **образец**. Указывает базу данных, в которой находится набор символов, если столбец содержит символьные данные или **текстовый** тип данных. Иначе возвращается значение NULL.|  
|**CHARACTER_SET_SCHEMA**|**varchar (** 3 **)**|Всегда возвращает значение NULL.|  
|**CHARACTER_SET_NAME**|**nvarchar (** 128 **)**|Возвращает уникальное имя для набора символов, если этот столбец имеет символьные данные или тип данных **Text** . Иначе возвращается значение NULL.|  
|**NUMERIC_PRECISION**|**tinyint**|Точность приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Основание системы счисления точности приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|  
|**NUMERIC_SCALE**|**tinyint**|Масштаб приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|  
|**DATETIME_PRECISION**|**smallint**|Код подтипа для **DateTime** и типа данных **интервала** ISO. Для других типов данных этот столбец возвращает значение NULL.|  
|**DOMAIN_DEFAULT**|**nvarchar (** 4000 **)**|Действительный текст определения инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;&#41;Transact-SQL](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;&#41;Transact-SQL](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys. syscharsets &#40;&#41;Transact-SQL](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys. Configurations &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [sys.types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  
