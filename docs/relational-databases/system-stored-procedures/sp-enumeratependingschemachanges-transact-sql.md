---
title: sp_enumeratependingschemachanges (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_enumeratependingschemachanges
- sp_enumeratependingschemachanges_TSQL
helpviewer_keywords:
- sp_enumeratependingschemachanges
ms.assetid: df169b21-d10a-41df-b3a1-654cfb58bc21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8a3f0fa918d0247f5fd6dbe11c4a91a2376c52dd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63043938"
---
# <a name="spenumeratependingschemachanges-transact-sql"></a>sp_enumeratependingschemachanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список всех ожидающих изменений схемы. Эта хранимая процедура может использоваться с [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md), что позволяет администратору пропустить выбранные изменения схемы, ожидающие завершения, чтобы они не реплицируются. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_enumeratependingschemachanges [ @publication = ] 'publication'   
    [ , [ @starting_schemaversion = ] starting_schemaversion ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @starting_schemaversion = ] starting_schemaversion` — Это минимальное количество изменений схемы для включения в результирующем наборе.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**имя_статьи**|**sysname**|Имя статьи, к которому применяется изменение схемы, или **всей публикации** для изменения схемы, которые применяются ко всей публикации.|  
|**schemaversion**|**int**|Количество изменений схемы, ожидающих завершения.|  
|**SchemaType**|**sysname**|Текстовое значение, представляющее тип изменения схемы.|  
|**schematext**|**nvarchar(max)**|Код [!INCLUDE[tsql](../../includes/tsql-md.md)], описывающий изменение схемы.|  
|**schemastatus**|**nvarchar(10)**|Указывает, ожидает ли своего завершения изменение схемы для данной статьи; может иметь следующие значения:<br /><br /> **Active** = изменение схемы находится в состоянии ожидания<br /><br /> **Неактивные** = изменение схемы неактивно<br /><br /> **Пропустить** = изменение схемы не реплицируется.|  
|**schemaguid**|**uniqueidentifier**|Идентифицирует изменение схемы.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_enumeratependingschemachanges** используется в репликации слиянием.  
  
 **sp_enumeratependingschemachanges**, которое используется с [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md), предназначенной для поддержки репликации слиянием и должна использоваться только тогда, когда другие действия по исправлению, такие как Повторная инициализация, не удалось исправить ситуацию.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_enumeratependingschemachanges**.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sysmergeschemachange &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
