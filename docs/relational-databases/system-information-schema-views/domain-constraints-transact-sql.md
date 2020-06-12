---
title: DOMAIN_CONSTRAINTS (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DOMAIN_CONSTRAINTS
- DOMAIN_CONSTRAINTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.DOMAIN_CONSTRAINTS view
- DOMAIN_CONSTRAINTS view
ms.assetid: 436c4480-f1e3-403f-b2bd-de04539afe3c
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 277791461943c669b2a768efd14aadd2170251b9
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669554"
---
# <a name="domain_constraints-transact-sql"></a>DOMAIN_CONSTRAINTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого из псевдонимов типов данных в текущей базе данных, к которым привязано правило и которые доступны текущему пользователю.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA.** _view_name_.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar (** 128 **)**|База данных, в которой находится правило.|  
|**CONSTRAINT_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей ограничение.<br /><br /> Важно. не используйте INFORMATION_SCHEMA представления для определения схемы объекта. <strong> \* \* \* \* </strong> INFORMATION_SCHEMA представления представляют только подмножество метаданных объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**CONSTRAINT_NAME**|**sysname**|Имя правила.|  
|**DOMAIN_CATALOG**|**nvarchar (** 128 **)**|База данных, в которой существует псевдоним типа данных.|  
|**DOMAIN_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей псевдоним типа данных.<br /><br /> Важно. не используйте INFORMATION_SCHEMA представления для определения схемы типа данных. <strong> \* \* \* \* </strong> Единственный надежный способ найти схему типа — использовать функцию TYPEPROPERTY.|  
|**DOMAIN_NAME**|**sysname**|Псевдоним типа данных.|  
|**IS_DEFERRABLE**|**varchar (** 2 **)**|Указывает, возможна ли отсрочка проверки ограничения. Всегда возвращает NO.|  
|**INITIALLY_DEFERRED**|**varchar (** 2 **)**|Указывает, отложена ли первоначальная проверка ограничения. Всегда возвращает NO.|  
  
## <a name="see-also"></a>См. также:  
 [Системные представления &#40;&#41;Transact-SQL](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;&#41;Transact-SQL](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys. Objects &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  
