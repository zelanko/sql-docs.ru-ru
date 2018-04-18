---
title: sp_repldropcolumn (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_repldropcolumn_TSQL
- sp_repldropcolumn
helpviewer_keywords:
- sp_repldropcolumn
ms.assetid: fdc1ec5f-f108-42b4-a2d8-f06a71913ab8
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d367aa2fa9f0eceee26b51d218f93d759286fdb1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sprepldropcolumn-transact-sql"></a>sp_repldropcolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет столбец из существующей статьи таблицы, которая была опубликована. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Данная хранимая процедура устарела и поддерживается в основном для обеспечения обратной совместимости. Должен использоваться только с [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] издателей и [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] переиздающих подписчиков. Эта процедура не должна использоваться в столбцах с типами данных, которые были представлены в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии.  
  
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
 [ @source_object =] '*source_object*"  
 Имя статьи таблицы, которая содержит столбец, подлежащий удалению. *source_object* имеет тип nvarchar(258) и не имеет значения по умолчанию.  
  
 [ @column =] '*столбца*"  
 Имя удаляемого столбца таблицы. *столбец* имеет тип sysname и значение по умолчанию.  
  
 [ @from_agent =] *from_agent*  
 Выполняется ли хранимая процедура агентом репликации. *from_agent* имеет тип int и значение по умолчанию 0, где используется значение 1, если эта хранимая процедура выполняется агентом репликации, и во всех остальных случаях должно использоваться значение по умолчанию 0.  
  
 [ @schema_change_script =] '*сценарий schema_change_script*"  
 Указывает имя и путь к скрипту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используемому для изменения пользовательских хранимых процедур, сформированных системой. *сценарий schema_change_script* имеет тип nvarchar(4000) и значение по умолчанию NULL. При репликации транзакций допустимо заменять одну или несколько хранимых процедур по умолчанию пользовательскими. *сценарий schema_change_script* выполняется после изменения схемы реплицируемой таблицы статьи, используя sp_repldropcolumn и может использоваться одно из следующих действий:  
  
-   Если пользовательские хранимые процедуры автоматически восстанавливаются, *сценарий schema_change_script* может использоваться для удаления этих пользовательских хранимых процедур и замените их определяемых пользователем пользовательских хранимых процедур, которые поддерживают новую схему.  
  
-   Если пользовательские хранимые процедуры не восстанавливаются автоматически, *сценарий schema_change_script*может использоваться для повторного создания этих хранимых процедур или для создания пользовательских хранимых процедур.  
  
 [ @force_invalidate_snapshot =] *подписки потребуют*  
 Определяет возможность недействительности моментального снимка. *подписки потребуют* имеет тип bit и значение по умолчанию 1.  
  
 Значение 1 указывает, что изменения в статье могут сделать моментальный снимок недействительным. В этом случае значение 1 дает разрешение на создание нового моментального снимка.  
  
 Значение 0 указывает, что изменение статьи не приводит к недействительности моментального снимка.  
  
 [ @force_reinit_subscription =] *этот*  
 Включает или отключает возможность повторной инициализации подписки. *Этот* имеет тип bit и значение по умолчанию 0.  
  
 Значение 0 указывает, что изменения в статье не вызывают повторной инициализации подписки.  
  
 Значение 1 указывает, что изменения в статье могут привести к необходимости повторной инициализации подписки. В этом случае значение 1 дает разрешение на повторную инициализацию подписки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения хранимой процедуры sp_repldropcolumn необходимо быть членом предопределенной роли сервера sysadmin на издателе либо членом предопределенной роли db_ddladmin или db_ddladmin базы данных публикации.  
  
## <a name="see-also"></a>См. также  
 [Устаревшие возможности репликации SQL Server](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
