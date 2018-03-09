---
title: "sp_enumeratependingschemachanges (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_enumeratependingschemachanges
- sp_enumeratependingschemachanges_TSQL
helpviewer_keywords:
- sp_enumeratependingschemachanges
ms.assetid: df169b21-d10a-41df-b3a1-654cfb58bc21
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 63ad21e40d524e2374434d733e1cc4357d6a9b23
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spenumeratependingschemachanges-transact-sql"></a>sp_enumeratependingschemachanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список всех ожидающих изменений схемы. Эта хранимая процедура может использоваться с [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md), который позволяет администратору пропустить выбранные изменения схемы, ожидающие завершения, чтобы они не будут реплицированы. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_enumeratependingschemachanges [ @publication = ] 'publication'   
    [ , [ @starting_schemaversion = ] starting_schemaversion ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=** ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@starting_schemaversion=** ] *starting_schemaversion*  
 Минимальное количество изменений схемы для включения в результирующий набор.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**имя_статьи**|**sysname**|Имя статьи, к которому применяется изменение схемы, или **всей публикации** для изменения схемы, которые применяются ко всей публикации.|  
|**schemaversion**|**int**|Количество изменений схемы, ожидающих завершения.|  
|**SchemaType**|**sysname**|Текстовое значение, представляющее тип изменения схемы.|  
|**schematext**|**nvarchar(max)**|Код [!INCLUDE[tsql](../../includes/tsql-md.md)], описывающий изменение схемы.|  
|**schemastatus**|**nvarchar(10)**|Указывает, ожидает ли своего завершения изменение схемы для данной статьи; может иметь следующие значения:<br /><br /> **активные** = изменение схемы ожидает<br /><br /> **Неактивные** = изменение схемы неактивно<br /><br /> **Пропустить** = изменение схемы не реплицируется.|  
|**schemaguid**|**uniqueidentifier**|Идентифицирует изменение схемы.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_enumeratependingschemachanges** используется в репликации слиянием.  
  
 **sp_enumeratependingschemachanges**вместе с [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md), предназначенной для поддержки репликации слиянием и должна использоваться только тогда, когда другие корректирующие действия, такие как Повторная инициализация, не удалось исправить ситуацию.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_enumeratependingschemachanges**.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sysmergeschemachange &#40; Transact-SQL &#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
