---
title: sp_droparticle (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_droparticle_TSQL
- sp_droparticle
helpviewer_keywords:
- sp_droparticle
ms.assetid: 09fec594-53f4-48a5-8edb-c50731c7adb2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 882c57c552d9666ec3ef308f63a6c5058c21e8e2
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768935"
---
# <a name="sp_droparticle-transact-sql"></a>sp_droparticle (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Удаляет статью из моментального снимка или публикации транзакций. Статья не может быть удалена, если на нее есть подписка. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_droparticle [ @publication= ] 'publication'  
        , [ @article= ] 'article'  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @from_drop_publication = ] from_drop_publication ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации, содержащей статью для удаления. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @article = ] 'article'`Имя статьи, которую необходимо удалить. Аргумент *article* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @ignore_distributor = ] ignore_distributor` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Подтверждает, что действие, выполняемое этой хранимой процедурой, может сделать существующий моментальный снимок недействительным. параметр *force_invalidate_snapshot* имеет значение **bit**и значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не приводят к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, возникает ошибка и изменения не выполняются.  
  
 значение **1** указывает, что изменения в статье могут привести к недействительности моментального снимка, и если существуют подписки, требующие создания нового моментального снимка, предоставляет разрешение на пометку существующего моментального снимка как устаревшего и создание нового моментального снимка.  
  
`[ @publisher = ] 'publisher'`Указывает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  при изменении свойств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] статьи издателя не следует использовать издатель.  
  
`[ @from_drop_publication = ] from_drop_publication` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_droparticle** используется в моментальных снимках и репликации транзакций.  
  
 Для статей с горизонтальной фильтрацией **sp_droparticle** проверяет столбец **типа** статьи в таблице [Transact-SQL &#40;&#41; sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md) , чтобы определить, следует ли также удалить представление или фильтр. Если представление или фильтр были созданы автоматически, они удаляются вместе со статьей. Если они были созданы вручную, они не удаляются.  
  
 При запуске **sp_droparticle** для удаления статьи из публикации не удаляется объект из базы данных публикации или соответствующий объект из базы данных подписки. При необходимости используйте инструкцию `DROP <object>` для удаления этих объектов вручную.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_droparticle](../../relational-databases/replication/codesnippet/tsql/sp-droparticle-transact-_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_droparticle**.  
  
## <a name="see-also"></a>См. также  
 [Удаление статьи](../../relational-databases/replication/publish/delete-an-article.md)   
 [Добавление и удаление статей в существующих публикациях](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [хранимая процедуры sp_addarticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
