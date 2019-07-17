---
title: sp_deletetracertokenhistory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletetracertokenhistory
- sp_deletetracertokenhistory_TSQL
helpviewer_keywords:
- sp_deletetracertokenhistory
ms.assetid: 9ae1be14-0d2f-40b1-9d6e-22d79726abf4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a7f70f5cd56867add98150d471d61cbc70faad0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111922"
---
# <a name="spdeletetracertokenhistory-transact-sql"></a>sp_deletetracertokenhistory (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Удаляет записи о трассировочных токенах из [MStracer_tokens &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) и [MStracer_history &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-history-transact-sql.md) системных таблиц. Эта хранимая процедура выполняется на издателе в базе данных публикации или на распространителе в базе данных распространителя.

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Синтаксис

```
sp_deletetracertokenhistory [ @publication = ] 'publication'
    [ , [ @tracer_id = ] tracer_id ]
    [ , [ @cutoff_date = ] cutoff_date ]
    [ , [ @publisher = ] 'publisher' ]
    [ , [ @publisher_db = ] 'publisher_db' ]
```

## <a name="arguments"></a>Аргументы

`@publication= 'publication'`  
Имя публикации, в которую была вставлена запись трассировочного токена. Тип данных является **sysname**. Этот параметр является обязательным.

`[ @tracer_id= ] tracer_id`  
Идентификатор трассировочного токена, который требуется удалить. Тип данных является **int**. Значение по умолчанию — *NULL*. Если *null*, все трассировочные токены публикации удаляются.

`[ @cutoff_date= ] cutoff_date`  
Трассировочных токенах, вставленных в публикацию, перед удалением этой даты. Тип данных является **datetime**. Значение по умолчанию — *NULL*.

`[ @publisher= ] 'publisher'`  
Имя издателя. Тип данных является **sysname**. Значение по умолчанию — *NULL*.

> [!NOTE]
> Этот параметр должен быть указан только для не - [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей или при выполнении хранимой процедуры из распространителя.

`[ @publisher_db= ] 'publisher_db'`  
Имя базы данных публикации. Тип данных является **sysname**. Значение по умолчанию — NULL. Этот параметр не учитывается, если хранимая процедура выполняется на издателе.

> [!NOTE]
> Этот параметр должен быть указан при выполнении хранимой процедуры из распространителя.

## <a name="return-code-values"></a>Значения кода возврата

**0** (успешное завершение) или **1** (неуспешное завершение)

## <a name="remarks"></a>Примечания

**sp_deletetracertokenhistory** используется в репликации транзакций.  

Если указать оба параметра, возникает ошибка *tracer_id* и *cutoff_date*.

Если вы не выполняйте **sp_deletetracertokenhistory** для удаления метаданных по трассировочным токенам, данные будут удалены при выполнении плановой очистки журнала.

Идентификаторы трассировочных токенов, которые можно определить, выполнив [sp_helptracertokens &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) или запросив [MStracer_tokens &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) системная таблица.

## <a name="permissions"></a>Разрешения

Только для следующих сотрудники имеют право выполнять **sp_deletetracertokenhistory**:

- Членами **replmonitor** роли в базе данных распространителя
- Членами **sysadmin** предопределенной роли сервера.
- Членами **db_owner** предопределенной роли базы данных, в базе данных публикации.
- **Db_owner** предопределенной базы данных.

## <a name="see-also"></a>См. также

[Измерение задержки и проверка правильности соединений для репликации транзакций](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)

[sp_helptracertokenhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)
