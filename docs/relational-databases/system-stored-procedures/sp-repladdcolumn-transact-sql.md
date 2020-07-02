---
title: sp_repladdcolumn (Transact-SQL) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 05c00137acdf989456903fedddcc45a7b79e0e61
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751632"
---
# <a name="sp_repladdcolumn-transact-sql"></a>sp_repladdcolumn (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Добавляет столбец к существующей статье таблицы, которая была опубликована. Позволяет добавить новый столбец всем издателям, которые публикуют эту статью, или просто добавить столбец к определенной публикации, которая публикует таблицы. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]
>  Данная хранимая процедура устарела и поддерживается для обеспечения обратной совместимости. Его следует использовать только с [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] издателями и [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] повторной публикацией подписчиков. Эта процедура не должна использоваться в столбцах с типами данных, которые были представлены в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии.  
  
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
 [ @source_object =] "*source_object*"  
 Имя табличной статьи, в которую будет добавлен столбец. *source_object* имеет тип **nvarchar (358**) и не имеет значения по умолчанию.  
  
 [ @column =] "*столбец*"  
 Имя столбца таблицы, добавляемого для репликации. *столбец* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 [ @typetext = ] '*TypeText*'  
 Определение добавляемого столбца. *TypeText* имеет тип **nvarchar (3000)** и не имеет значения по умолчанию. Например, если добавляется столбец order_filled и это поле с одним символом, а не NULL, и имеет значение по умолчанию **N**, order_filled будет параметром *столбца* , а определение столбца, **char (1) NOT NULL constraint_name значением по умолчанию "N"** будет значение параметра *TypeText* .  
  
 [ @publication_to_add =] "*publication_to_add*"  
 Имя публикации, к которой добавляется новый столбец. *publication_to_add* имеет тип **nvarchar (4000)** и значение по умолчанию **ALL**. Если **все**, то затрагиваются все публикации, содержащие эту таблицу. Если указан *publication_to_add* , то только эта публикация добавляет новый столбец.  
  
 [ @from_agent =] *from_agent*  
 Выполняется ли хранимая процедура агентом репликации. *from_agent* является **типом int**и значением по умолчанию **0**, где значение **1** используется, если хранимая процедура выполняется агентом репликации, а во всех остальных случаях используется значение по умолчанию **0**.  
  
 [ @schema_change_script =] "*schema_change_script*"  
 Указывает имя и путь к скрипту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используемому для изменения пользовательских хранимых процедур, сформированных системой. *schema_change_script* имеет тип **nvarchar (4000)** и значение по умолчанию NULL. При репликации транзакций допустимо заменять одну или несколько хранимых процедур по умолчанию пользовательскими. *schema_change_script* выполняется после изменения схемы в реплицированной статье таблицы с помощью sp_repladdcolumn и может использоваться для выполнения одного из следующих действий.  
  
-   Если пользовательские хранимые процедуры автоматически создаются повторно, *schema_change_script* можно использовать для удаления этих пользовательских хранимых процедур и замены их пользовательскими хранимыми процедурами, которые поддерживают новую схему.  
  
-   Если пользовательские хранимые процедуры не формируются автоматически, *schema_change_script*можно использовать для повторного создания этих хранимых процедур или для создания пользовательских хранимых процедур, определяемых пользователем.  
  
 [ @force_invalidate_snapshot =] *force_invalidate_snapshot*  
 Определяет возможность недействительности моментального снимка. *force_invalidate_snapshot* является **битом**и имеет значение по умолчанию **1**.  
  
 **1** указывает, что изменения в статье могут привести к недействительности моментального снимка, и, если это так, значение **1** дает разрешение на создание нового моментального снимка.  
  
 **0** указывает, что изменения в статье не приводят к недействительности моментального снимка.  
  
 [ @force_reinit_subscription =] *force_reinit_subscription*  
 Включает или отключает возможность повторной инициализации подписки. *force_reinit_subscription* является **битом** со значением по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не приводят к повторной инициализации подписки.  
  
 **1** указывает, что изменения в статье могут привести к повторной инициализации подписки, и если это так, значение **1** дает разрешение на повторную инициализацию подписки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера sysadmin и предопределенной роли базы данных db_owner могут выполнять процедуру sp_repladdcolumn.  
  
## <a name="see-also"></a>См. также  
 [Устаревшие функции в Репликация SQL Server](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
