---
title: "sp_reinitsubscription (Transact-SQL) | Документы Microsoft"
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
- sp_reinitsubscription
- sp_reinitsubscription_TSQL
helpviewer_keywords:
- sp_reinitsubscription
ms.assetid: d56ae218-6128-4ff9-b06c-749914505c7b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 28ed672409e115b5b7980766ee7bf078d52b3bf1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spreinitsubscription-transact-sql"></a>sp_reinitsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Помечает подписку для повторной инициализации. Эта хранимая процедура выполняется на стороне издателя для принудительной подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_reinitsubscription [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
        , [ @subscriber = ] 'subscriber'  
    [ , [ @destination_db = ] 'destination_db']  
    [ , [ @for_schema_change = ] 'for_schema_change']  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @ignore_distributor_failure = ] ignore_distributor_failure ]   
    [ , [ @invalidate_snapshot = ] invalidate_snapshot ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, по умолчанию all.  
  
 [  **@article=**] **"***статьи***"**  
 Имя статьи. *статья* — **sysname**, по умолчанию all. Для публикации с немедленным обновлением *статьи* должно быть **все**; в противном случае хранимая процедура пропускает публикацию и сообщает об ошибке.  
  
 [  **@subscriber=**] **"***подписчика***"**  
 Имя подписчика. *подписчик* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@destination_db=**] **"***destination_db***"**  
 Имя целевой базы данных. *destination_db* — **sysname**, по умолчанию all.  
  
 [  **@for_schema_change=**] **"***for_schema_change***"**  
 Указывает, является ли повторная инициализация результатом изменения схемы в базе данных публикации. *for_schema_change* — **бит**, значение по умолчанию 0. Если **0**, активные подписки публикаций, которые допускают непосредственное обновление, повторно до тех пор, пока повторной инициализации всей публикации, а не только некоторые из его статей. Это означает, что повторная инициализация инициируется в результате изменения схемы. Если **1**, активные подписки не активируются повторно, пока не будет запущен агент моментальных снимков.  
  
 [  **@publisher=** ] **"***издатель***"**  
 Задает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не должны использоваться для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей.  
  
 [  **@ignore_distributor_failure=** ] *ignore_distributor_failure*  
 Разрешает повторную инициализацию, даже если распространитель не существует или находится в режиме «вне сети». *ignore_distributor_failure* — **бит**, значение по умолчанию 0. Если **0**, повторная инициализация завершится неудачей, если распространитель не существует или находится в автономном режиме.  
  
 [  **@invalidate_snapshot=** ] *invalidate_snapshot*  
 Делает существующий моментальный снимок публикации недействительным. *invalidate_snapshot* — **бит**, значение по умолчанию 0. Если **1**, нового моментального снимка для публикации.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_reinitsubscription** используется в репликации транзакций.  
  
 **sp_reinitsubscription** не поддерживается для-одноранговой репликации транзакций.  
  
 Для подписок, для которых исходный моментальный снимок применяется автоматически и публикации не допускают обновляемых подписок, агент моментальных снимков должен быть запущен после выполнения этой хранимой процедуры так, чтобы схема и программные файлы массового копирования были подготовлены, и агент распространителя был готов к повторной синхронизации подписок.  
  
 Для подписок, у которых исходный моментальный снимок применяется автоматически и публикация допускает обновляемые подписки, агент распространителя повторно синхронизирует подписку, используя последнюю схему и программные файлы массового копирования, предварительно созданные агентом моментальных снимков. Агент распространителя повторно синхронизирует подписку сразу после выполнения пользователем **sp_reinitsubscription**, если агент распространителя не занят, иначе синхронизация может быть выполнена после (интервал сообщения указанным параметром командной строки агента распространителя: **MessageInterval**).  
  
 **sp_reinitsubscription** никак не влияет на подписки, где исходный моментальный снимок применяется вручную.  
  
 Для повторной синхронизации анонимных подписок на публикацию, следует передать **все** или NULL в качестве *подписчика*.  
  
 Репликация транзакций поддерживает повторную инициализацию подписок на уровне статей. Моментальный снимок статьи повторно применяется на стороне подписчика во время следующей инициализации, после того как статья была помечена для повторной инициализации или синхронизации. Однако если существуют зависимые статьи, на которые подписан тот же подписчик, повторное применение к статье моментального снимка может завершиться неудачно, если только зависимые статьи в публикации также автоматически не инициализируются повторно при возникновении определенных обстоятельств:  
  
-   если командой перед созданием статьи является DROP, то статьи для привязанных к схеме представлений и хранимых процедур на основном объекте статьи также помечаются для повторной инициализации;  
  
-   если параметр схемы статьи включает создание сценария объявленной ссылочной целостности для первичных ключей, статьи, у которых есть основные таблицы с внешними ключами к основным таблицам повторно инициализируемой статьи, также помечаются для повторной инициализации.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_reinittranpushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitsubscription-tr_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера, члены **db_owner** предопределенной роли базы данных, или создатель подписки могут выполнять процедуру **sp_reinitsubscription** .  
  
## <a name="see-also"></a>См. также:  
 [Повторная инициализация подписки](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Повторная инициализация подписок](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
