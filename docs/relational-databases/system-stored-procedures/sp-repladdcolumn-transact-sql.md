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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 75c66d1077b111837197957cc845b690b794ea24
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771050"
---
# <a name="sprepladdcolumn-transact-sql"></a>sp_repladdcolumn (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
 [ @source_object =] '*source_object*'  
 Имя табличной статьи, в которую будет добавлен столбец. *source_object* имеет тип **nvarchar (358**) и не имеет значения по умолчанию.  
  
 [ @column =] "*столбец*"  
 Имя столбца таблицы, добавляемого для репликации. *столбец* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 [ @typetext =] '*TypeText*'  
 Определение добавляемого столбца. *TypeText* имеет тип **nvarchar (3000)** и не имеет значения по умолчанию. Например, если добавляется столбец order_filled, а — единственное символьное поле, а не NULL, и имеет значение по умолчанию **N**, то order_filled бы был параметром *Column* , а определение столбца, **char (1) NOT NULL. constraint_name по УМОЛЧАНИю "N"** будет значением параметра *TypeText* .  
  
 [ @publication_to_add =] '*publication_to_add*'  
 Имя публикации, к которой добавляется новый столбец. *publication_to_add* имеет тип **nvarchar (4000)** и значение по умолчанию **ALL**. Если **все**, то затрагиваются все публикации, содержащие эту таблицу. Если указан *publication_to_add* , то только эта публикация добавляет новый столбец.  
  
 [ @from_agent =] *from_agent*  
 Выполняется ли хранимая процедура агентом репликации. *from_agent* имеет **тип int**, значение по умолчанию **0**, при котором хранимая процедура выполняется агентом репликации, а во всех остальных случаях используется значение по умолчанию **0**.  
  
 [ @schema_change_script =] '*schema_change_script*'  
 Указывает имя и путь к скрипту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используемому для изменения пользовательских хранимых процедур, сформированных системой. *schema_change_script* имеет тип **nvarchar (4000)** и значение по умолчанию NULL. При репликации транзакций допустимо заменять одну или несколько хранимых процедур по умолчанию пользовательскими. *schema_change_script* выполняется после внесения изменения схемы в реплицированную статью таблицы с помощью sp_repladdcolumn и может использоваться для выполнения одного из следующих действий.  
  
-   Если пользовательские хранимые процедуры автоматически создаются повторно, *schema_change_script* можно использовать для удаления этих пользовательских хранимых процедур и замены их пользовательскими хранимыми процедурами, которые поддерживают новую схему.  
  
-   Если пользовательские хранимые процедуры не формируются автоматически, *schema_change_script*можно использовать для повторного создания этих хранимых процедур или для создания пользовательских хранимых процедур, определяемых пользователем.  
  
 [ @force_invalidate_snapshot =] *force_invalidate_snapshot*  
 Определяет возможность недействительности моментального снимка. параметр *force_invalidate_snapshot* имеет значение **bit**и значение по умолчанию **1**.  
  
 **1** указывает, что изменения в статье могут привести к недействительности моментального снимка, и, если это так, значение **1** дает разрешение на создание нового моментального снимка.  
  
 **0** указывает, что изменения в статье не приводят к недействительности моментального снимка.  
  
 [ @force_reinit_subscription =] *force_reinit_subscription*  
 Включает или отключает возможность повторной инициализации подписки. параметр *force_reinit_subscription* имеет **бит** и значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не приводят к повторной инициализации подписки.  
  
 **1** указывает, что изменения в статье могут привести к повторной инициализации подписки, и если это так, значение **1** дает разрешение на повторную инициализацию подписки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера sysadmin и предопределенной роли базы данных db_owner могут выполнять процедуру sp_repladdcolumn.  
  
## <a name="see-also"></a>См. также  
 [Устаревшие функции в Репликация SQL Server](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
