---
title: sp_repldropcolumn (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_repldropcolumn_TSQL
- sp_repldropcolumn
helpviewer_keywords:
- sp_repldropcolumn
ms.assetid: fdc1ec5f-f108-42b4-a2d8-f06a71913ab8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1b15bcd0b5a24c464799d1bb8150be59600a85ed
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47652892"
---
# <a name="sprepldropcolumn-transact-sql"></a>sp_repldropcolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет столбец из существующей статьи таблицы, которая была опубликована. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Данная хранимая процедура устарела и поддерживается в основном для обеспечения обратной совместимости. Он должен использоваться только с [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] издателей и [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] переиздающих подписчиков. Эта процедура не должна использоваться в столбцах с типами данных, которые были представлены в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии.  
  
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
 Имя статьи таблицы, которая содержит столбец, подлежащий удалению. *source_object* является значение типа nvarchar(258), не имеет значения по умолчанию.  
  
 [ @column =] '*столбец*"  
 Имя удаляемого столбца таблицы. *столбец* имеет тип sysname и значение по умолчанию.  
  
 [ @from_agent =] *from_agent*  
 Выполняется ли хранимая процедура агентом репликации. *from_agent* — целое число, значение по умолчанию 0, где используется значение 1, если эта хранимая процедура выполняется агентом репликации, и во всех остальных случаях должно использоваться значение по умолчанию 0.  
  
 [ @schema_change_script =] '*сценарий schema_change_script*"  
 Указывает имя и путь к скрипту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используемому для изменения пользовательских хранимых процедур, сформированных системой. *сценарий schema_change_script* имеет тип nvarchar(4000) и значение по умолчанию NULL. При репликации транзакций допустимо заменять одну или несколько хранимых процедур по умолчанию пользовательскими. *сценарий schema_change_script* выполняется после изменения схемы реплицируемой статьи таблицы с помощью sp_repldropcolumn вносится и может использоваться для выполните одно из следующих:  
  
-   Если пользовательские хранимые процедуры автоматически восстанавливаются, *сценарий schema_change_script* может использоваться для удаления этих пользовательских хранимых процедур и замените их пользовательские пользовательские хранимые процедуры, которые поддерживают новую схему.  
  
-   Если пользовательские хранимые процедуры не восстанавливаются автоматически, *сценарий schema_change_script*может использоваться для повторного создания этих хранимых процедур или для создания пользовательских хранимых процедур.  
  
 [ @force_invalidate_snapshot =] *подписки потребуют*  
 Определяет возможность недействительности моментального снимка. *подписки потребуют* является bit и значение по умолчанию 1.  
  
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
 [Устаревшие функции репликации в SQL Server](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
