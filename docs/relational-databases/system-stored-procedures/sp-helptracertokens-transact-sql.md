---
title: sp_helptracertokens (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helptracertokens
- sp_helptracertokens_TSQL
helpviewer_keywords:
- sp_helptracertokens
ms.assetid: 61f27234-531d-4b37-8fa3-fe4c32e6f521
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83d5789fed1ee9ff8d92d549feeb1ae47a8ed38c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68048232"
---
# <a name="sphelptracertokens-transact-sql"></a>sp_helptracertokens (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку для каждого трассировочного токена, вставленного в публикацию для определения задержки. Эта хранимая процедура выполняется на издателе в базе данных публикации или на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helptracertokens [ @publication = ] 'publication'   
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации, в которую маркеры были вставлены трассировочные. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publisher = ] 'publisher'` Имя издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]
>  Этот параметр должен быть указан только для не - [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей.  
  
`[ @publisher_db = ] 'publisher_db'` Имя базы данных публикации. *publisher_db* — **sysname**, со значением по умолчанию NULL. Этот параметр не учитывается, если хранимая процедура выполняется на издателе.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|Идентифицирует запись трассировочного токена.|  
|**publisher_commit**|**datetime**|Дата и время, когда была зафиксирована запись токена у издателя в базе данных публикации.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helptracertokens** используется в репликации транзакций.  
  
 **sp_helptracertokens** используется для получения идентификаторов трассировочных токенов при выполнении [sp_helptracertokenhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md).  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-helptracertokens-tran_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных в базе данных публикации или **db_owner** базы данных или  **replmonitor** ролей в базе данных распространителя могут выполнять процедуру **sp_helptracertokenhistory**.  
  
## <a name="see-also"></a>См. также  
 [Измерение задержки и проверка правильности соединений для репликации транзакций](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_deletetracertokenhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)  
  
  
