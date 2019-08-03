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
ms.openlocfilehash: cf591964e5dfef0536c79b0b35e5918d4f46d972
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771144"
---
# <a name="spdeletetracertokenhistory-transact-sql"></a>sp_deletetracertokenhistory (Transact-SQL)

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Удаляет записи трассировочного токена из системных таблиц [Transact &#40;&#41; ](../../relational-databases/system-tables/mstracer-history-transact-sql.md) -SQL [MStracer_tokens &#40;&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) и MStracer_history. Эта хранимая процедура выполняется на издателе в базе данных публикации или на распространителе в базе данных распространителя.

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
Имя публикации, в которую была вставлена запись трассировочного токена. Тип данных — **sysname**. Этот параметр является обязательным.

`[ @tracer_id= ] tracer_id`  
Идентификатор трассировочного токена, который требуется удалить. Тип данных — **int**. Значение по умолчанию — *NULL*. Если *значение равно NULL*, все трассировочные токены, относящиеся к публикации, удаляются.

`[ @cutoff_date= ] cutoff_date`  
Трассировочные токены, вставленные в публикацию до этой даты, удаляются. Тип данных — **DateTime**. Значение по умолчанию — *NULL*.

`[ @publisher= ] 'publisher'`  
Имя издателя. Тип данных — **sysname**. Значение по умолчанию — *NULL*.

> [!NOTE]
> Этот параметр должен быть указан только для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, отличных от, или при выполнении хранимой процедуры от распространителя.

`[ @publisher_db= ] 'publisher_db'`  
Имя базы данных публикации. Тип данных — **sysname**. Значение по умолчанию — NULL. Этот параметр не учитывается, если хранимая процедура выполняется на издателе.

> [!NOTE]
> Этот параметр должен быть указан при выполнении хранимой процедуры от распространителя.

## <a name="return-code-values"></a>Значения кода возврата

**0** (успешное завершение) или **1** (сбой)

## <a name="remarks"></a>Примечания

**sp_deletetracertokenhistory** используется в репликации транзакций.  

При указании обоих параметров *tracer_id* и *cutoff_date*возникает ошибка.

Если не выполнить **sp_deletetracertokenhistory** для удаления метаданных трассировочного токена, информация будет удалена при регулярном запланированном очистке журнала.

Идентификаторы трассировочных токенов можно определить, выполнив [инструкцию sp_helptracertokens &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) или выполнив запрос к системной таблице [Transact-SQL &#40;&#41; MStracer_tokens](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) .

## <a name="permissions"></a>Разрешения

Только следующие сотрудники имеют право на выполнение **sp_deletetracertokenhistory**:

- Члены ролей **replmonitor** в базе данных распространителя
- Члены предопределенной роли сервера **sysadmin** .
- Члены предопределенной роли базы данных **db_owner** в базе данных публикации.
- **Db_owner** предопределенной базы данных.

## <a name="see-also"></a>См. также

[Измерение задержки и проверка правильности соединений для репликации транзакций](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)

[sp_helptracertokenhistory &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)
