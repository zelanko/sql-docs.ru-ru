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
ms.openlocfilehash: da5579c52d1ffe1400e3b4c8c01210ca5856597b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68124582"
---
# <a name="sp_enumeratependingschemachanges-transact-sql"></a>sp_enumeratependingschemachanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список всех ожидающих изменений схемы. Эта хранимая процедура может использоваться с [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md), что позволяет администратору пропустить выбранные ожидающие изменения схемы, чтобы они не были реплицированы. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_enumeratependingschemachanges [ @publication = ] 'publication'   
    [ , [ @starting_schemaversion = ] starting_schemaversion ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @starting_schemaversion = ] starting_schemaversion`Наименьшее число изменений схемы, которое необходимо включить в результирующий набор.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**article_name**|**sysname**|Имя статьи, к которой применяется изменение схемы, или **всей публикации** для изменений схемы, применяемых ко всей публикации.|  
|**schemaVersion**|**int**|Количество изменений схемы, ожидающих завершения.|  
|**schematype**|**sysname**|Текстовое значение, представляющее тип изменения схемы.|  
|**schematext**|**nvarchar(max)**|Код [!INCLUDE[tsql](../../includes/tsql-md.md)], описывающий изменение схемы.|  
|**schemastatus**|**nvarchar (10)**|Указывает, ожидает ли своего завершения изменение схемы для данной статьи; может иметь следующие значения:<br /><br /> **Active** = ожидается изменение схемы<br /><br /> **Inactive** = изменение схемы неактивно<br /><br /> **пропустить** = изменение схемы не реплицируется|  
|**schemaguid**|**uniqueidentifier**|Идентифицирует изменение схемы.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_enumeratependingschemachanges** используется в репликации слиянием.  
  
 **sp_enumeratependingschemachanges**, используемый с [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md), предназначен для поддержки репликации слиянием и должен использоваться только в том случае, если другие корректирующие действия, такие как повторная инициализация, не могли исправить ситуацию.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_enumeratependingschemachanges**.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры репликации &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sysmergeschemachange &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
