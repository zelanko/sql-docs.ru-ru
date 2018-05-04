---
title: sys.assembly_modules (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.assembly_modules
- sys.assembly_modules_TSQL
- assembly_modules
- assembly_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_modules catalog view
ms.assetid: 5f9e644e-8065-49a2-b53d-db7df98f70d8
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 43ab83d17d9bca58790dc06b37ed46b157a97408
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysassemblymodules-transact-sql"></a>sys.assembly_references (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Возвращает по одной строке для каждой функции, процедуры или триггера, которые определены сборкой среды CLR. Это представление каталога сопоставляет хранимые процедуры, триггеры или функции среды CLR с их базовой реализацией. Объекты типов TA, AF, PC, FS и FT имеют связанный с ними модуль сборки. Чтобы найти взаимосвязь между объектом и сборкой, можно соединить это представление каталога с другими представлениями каталога. Например, при создании хранимой процедурой CLR она представлена одной строкой в **sys.objects**по одной строке в **sys.procedures** (наследуется от класса **sys.objects**), и одна строка в **sys.assembly_modules**. Сама хранимая процедура представлена метаданными **sys.objects** и **sys.procedures**. Ссылки на процедуры базовой реализацией среды CLR можно найти на **sys.assembly_modules**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификационный номер объекта SQL. Уникален в базе данных.|  
|**assembly_id**|**int**|Идентификатор той сборки, откуда был создан этот модуль.|  
|**assembly_class**|**sysname**|Имя класса в сборке, определяющее этот модуль.|  
|**assembly_method**|**sysname**|Имя метода в рамках **assembly_class** , определяющее этот модуль.<br /><br /> Для агрегатных функций (AF) имеет значение NULL.|  
|**null_on_null_input**|**бит**|Модуль выдает выходные значения NULL при любых входных значениях NULL.|  
|**execute_as_principal_id**|**int**|Идентификатор участника базы данных, в контексте которого производится выполнение, как указано в предложении EXECUTE AS функции, хранимой процедуры или триггера среды CLR. <br /><br /> NULL = EXECUTE AS CALLER. Это значение по умолчанию.<br /><br /> Идентификатор указанного участника базы данных = EXECUTE AS SELF, EXECUTE AS *имя_пользователя*, или EXECUTE AS *login_name*.<br /><br /> -2 = EXECUTE AS OWNER.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
