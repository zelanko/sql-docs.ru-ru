---
title: sp_repldropcolumn (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repldropcolumn_TSQL
- sp_repldropcolumn
helpviewer_keywords:
- sp_repldropcolumn
ms.assetid: fdc1ec5f-f108-42b4-a2d8-f06a71913ab8
author: stevestein
ms.author: sstein
ms.openlocfilehash: a6b398a4dd7e93521b38708d3a7e37ae09e70a15
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771470"
---
# <a name="sp_repldropcolumn-transact-sql"></a>sp_repldropcolumn (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Удаляет столбец из существующей статьи таблицы, которая была опубликована. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]
>  Данная хранимая процедура устарела и поддерживается в основном для обеспечения обратной совместимости. Его следует использовать только с [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] издателями и [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] повторной публикацией подписчиков. Эта процедура не должна использоваться в столбцах с типами данных, которые были представлены в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_repldropcolumn [ @source_object = ] 'source_object', [ @column = ] 'column'   
    [ , [ @from_agent = ] from_agent]   
    [ , [ @schema_change_script = ] 'schema_change_script' ]   
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]   
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [ @source_object = ] "*source_object*"  
 Имя статьи таблицы, которая содержит столбец, подлежащий удалению. *source_object* имеет тип nvarchar (258) и не имеет значения по умолчанию.  
  
 [ @column = ] "*Column*"  
 Имя удаляемого столбца таблицы. *столбец* имеет тип sysname и не имеет значения по умолчанию.  
  
 [ @from_agent = ] *from_agent*  
 Выполняется ли хранимая процедура агентом репликации. *from_agent* является типом int и значением по умолчанию 0, где значение 1 используется, если хранимая процедура выполняется агентом репликации, а во всех остальных случаях используется значение по умолчанию 0.  
  
 [ @schema_change_script = ] "*schema_change_script*"  
 Указывает имя и путь к скрипту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используемому для изменения пользовательских хранимых процедур, сформированных системой. *schema_change_script* имеет тип nvarchar (4000) и значение по умолчанию NULL. При репликации транзакций допустимо заменять одну или несколько хранимых процедур по умолчанию пользовательскими. *schema_change_script* выполняется после изменения схемы в реплицированной статье таблицы с помощью sp_repldropcolumn и может использоваться для выполнения одного из следующих действий.  
  
-   Если пользовательские хранимые процедуры автоматически создаются повторно, *schema_change_script* можно использовать для удаления этих пользовательских хранимых процедур и замены их пользовательскими хранимыми процедурами, которые поддерживают новую схему.  
  
-   Если пользовательские хранимые процедуры не формируются автоматически, *schema_change_script*можно использовать для повторного создания этих хранимых процедур или для создания пользовательских хранимых процедур, определяемых пользователем.  
  
 [ @force_invalidate_snapshot = ] *force_invalidate_snapshot*  
 Определяет возможность недействительности моментального снимка. *force_invalidate_snapshot* является битом и имеет значение по умолчанию 1.  
  
 Значение 1 указывает, что изменения в статье могут сделать моментальный снимок недействительным. В этом случае значение 1 дает разрешение на создание нового моментального снимка.  
  
 Значение 0 указывает, что изменение статьи не приводит к недействительности моментального снимка.  
  
 [ @force_reinit_subscription = ] *force_reinit_subscription*  
 Включает или отключает возможность повторной инициализации подписки. *force_reinit_subscription* является битом со значением по умолчанию 0.  
  
 Значение 0 указывает, что изменения в статье не вызывают повторной инициализации подписки.  
  
 Значение 1 указывает, что изменения в статье могут привести к необходимости повторной инициализации подписки. В этом случае значение 1 дает разрешение на повторную инициализацию подписки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения хранимой процедуры sp_repldropcolumn необходимо быть членом предопределенной роли сервера sysadmin на издателе либо членом предопределенной роли db_ddladmin или db_ddladmin базы данных публикации.  
  
## <a name="see-also"></a>См. также:  
 [Устаревшие функции в Репликация SQL Server](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
