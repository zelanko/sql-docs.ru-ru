---
title: Процедура sp_repladdcolumn (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repladdcolumn_TSQL
- sp_repladdcolumn
helpviewer_keywords:
- sp_repladdcolumn
ms.assetid: d6220f9f-c738-4f9c-bcf8-419994e86c81
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1b01a48e15c06f021b41b3bded35a0cd2739313c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006915"
---
# <a name="sprepladdcolumn-transact-sql"></a>sp_repladdcolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет столбец к существующей статье таблицы, которая была опубликована. Позволяет добавить новый столбец всем издателям, которые публикуют эту статью, или просто добавить столбец к определенной публикации, которая публикует таблицы. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]
>  Данная хранимая процедура устарела и поддерживается для обеспечения обратной совместимости. Он должен использоваться только с [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] издателей и [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] переиздающих подписчиков. Эта процедура не должна использоваться в столбцах с типами данных, которые были представлены в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_repladdcolumn [ @source_object = ] 'source_object', [ @column = ] 'column' ]  
    [ , [ @typetext = ] 'typetext' ]  
    [ , [ @publication_to_add = ] 'publication_to_add' ]  
    [ , [ @from_agent = ] from_agent ]  
    [ , [ @schema_change_script = ] 'schema_change_script' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @source_object =] '*source_object*"  
 Имя табличной статьи, в которую будет добавлен столбец. *source_object* является **nvarchar (358**), не имеет значения по умолчанию.  
  
 [ @column =] '*столбец*"  
 Имя столбца таблицы, добавляемого для репликации. *столбец* — **sysname**, не имеет значения по умолчанию.  
  
 [ @typetext =] '*typetext*"  
 Определение добавляемого столбца. *TypeText* — **nvarchar(3000)** , не имеет значения по умолчанию. Например, если добавляется столбец order_filled, и это из одного символа, поле, не равно NULL и имеет значение по умолчанию **N**, будет order_filled *столбец* параметр, при определении столбец, **char(1) NOT NULL CONSTRAINT constraint_name DEFAULT "n"** бы *typetext* значение параметра.  
  
 [ @publication_to_add =] '*publication_to_add*"  
 Имя публикации, к которой добавляется новый столбец. *publication_to_add* — **nvarchar(4000)** , значение по умолчанию **все**. Если **все**, а затем влияют на все публикации, содержащей эту таблицу. Если *publication_to_add* указан, то только этой публикации был добавлен новый столбец.  
  
 [ @from_agent =] *from_agent*  
 Выполняется ли хранимая процедура агентом репликации. *from_agent* — **int**, значение по умолчанию **0**, где значение **1** используется, если эта хранимая процедура выполняется агентом репликации, а в каждом другом случае значение по умолчанию **0**следует использовать.  
  
 [ @schema_change_script =] '*сценарий schema_change_script*"  
 Указывает имя и путь к скрипту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используемому для изменения пользовательских хранимых процедур, сформированных системой. *сценарий schema_change_script* — **nvarchar(4000)** , значение по умолчанию NULL. При репликации транзакций допустимо заменять одну или несколько хранимых процедур по умолчанию пользовательскими. *сценарий schema_change_script* выполняется после изменения схемы реплицируемой таблицы статьи, с помощью процедуры sp_repladdcolumn и может использоваться для выполните одно из следующих:  
  
-   Если пользовательские хранимые процедуры автоматически восстанавливаются, *сценарий schema_change_script* может использоваться для удаления этих пользовательских хранимых процедур и замените их пользовательские пользовательские хранимые процедуры, которые поддерживают новую схему.  
  
-   Если пользовательские хранимые процедуры не восстанавливаются автоматически, *сценарий schema_change_script*может использоваться для повторного создания этих хранимых процедур или для создания пользовательских хранимых процедур.  
  
 [ @force_invalidate_snapshot =] *подписки потребуют*  
 Определяет возможность недействительности моментального снимка. *подписки потребуют* — **бит**, значение по умолчанию **1**.  
  
 **1** указывает, что изменения в статье могут сделать моментальный снимок недействительным, и если это так, значение **1** дает разрешение нового моментального снимка.  
  
 **0** означает, что изменения статьи не приводят к недействительности моментального снимка.  
  
 [ @force_reinit_subscription =] *этот*  
 Включает или отключает возможность повторной инициализации подписки. *Этот* — **бит** значение по умолчанию **0**.  
  
 **0** указывает, что изменения статьи не вызывают повторной инициализации подписки.  
  
 **1** изменения в статье могут привести к повторной инициализации подписки; Если это происходит, значение **1** дает разрешение произвести повторную инициализацию подписки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера sysadmin и предопределенной роли базы данных db_owner могут выполнять процедуру sp_repladdcolumn.  
  
## <a name="see-also"></a>См. также  
 [Устаревшие функции репликации в SQL Server](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
