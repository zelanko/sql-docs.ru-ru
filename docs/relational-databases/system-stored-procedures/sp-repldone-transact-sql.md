---
title: sp_repldone (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repldone
- sp_repldone_TSQL
helpviewer_keywords:
- sp_repldone
ms.assetid: 045d3cd1-712b-44b7-a56a-c9438d4077b9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4e504a1fd074f198a62c94ffa773a08026d1e9c0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834332"
---
# <a name="sp_repldone-transact-sql"></a>sp_repldone (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Обновляет запись, которая идентифицирует последнюю распределенную транзакцию сервера. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!CAUTION]  
>  В случае ручного выполнения процедуры **sp_repldone** можно нарушить порядок и согласованность доставленных транзакций. **sp_repldone** следует использовать только для устранения неполадок репликации, направленных опытным специалистом службы поддержки репликации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```
sp_repldone [ @xactid= ] xactid   
        , [ @xact_seqno= ] xact_seqno   
    [ , [ @numtrans= ] numtrans ]   
    [ , [ @time= ] time   
    [ , [ @reset= ] reset ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @xactid = ] xactid`Регистрационный номер транзакции в журнале (LSN) первой записи для последней распределенной транзакции сервера. *xactid* является **двоичным (10)** и не имеет значения по умолчанию.  
  
`[ @xact_seqno = ] xact_seqno`Номер LSN последней записи для последней распределенной транзакции сервера. *xact_seqno* является **двоичным (10)** и не имеет значения по умолчанию.  
  
`[ @numtrans = ] numtrans`Число распределенных транзакций. *numtrans* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @time = ] time`Число миллисекунд, необходимых для распределения последнего пакета транзакций. *time* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @reset = ] reset`Состояние сброса. *Reset* имеет **тип int**и не имеет значения по умолчанию. Если значение равно **1**, то все реплицированные транзакции в журнале помечаются как распределенные. Если значение **равно 0**, то журнал транзакций сбрасывается до первой реплицированной транзакции, а реплицированные транзакции не помечаются как распределенные. *Сброс* допустим только в том случае, если оба *xactid* и *xact_seqno* имеют значение null.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_repldone** используется в репликации транзакций.  
  
 **sp_repldone** используется процессом чтения журнала для контроля за распределенными транзакциями.  
  
 С помощью **sp_repldone**можно вручную сообщить серверу, что транзакция была реплицирована (отправлена распространителю). Кроме того, эта процедура позволяет изменить транзакцию, отмеченную в качестве следующей транзакции, подлежащей репликации. По списку реплицированных транзакций можно перемещаться вперед и назад. (Все транзакции, номера которых не превышают номера этой транзакции, отмечаются как распределенные.)  
  
 Обязательные параметры *xactid* и *xact_seqno* можно получить с помощью **sp_repltrans** или **sp_replcmds**.  
  
## <a name="permissions"></a>Разрешения  
 Члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_repldone**.  
  
## <a name="examples"></a>Примеры  
 Если *xactid* имеет значение null, *xact_seqno* имеет значение null, а *Сброс* равен **1**, все реплицированные транзакции в журнале помечаются как распределенные. Это полезно, если в журнале транзакций имеются реплицированные транзакции, ставшие недействительными, и нужно усечь журнал, например:  
  
```sql
EXEC sp_repldone @xactid = NULL, @xact_seqno = NULL, @numtrans = 0, @time = 0, @reset = 1  
```  
  
> [!CAUTION]  
>  Данную процедуру можно использовать в аварийных случаях для усечения журнала транзакций при наличии транзакций, ожидающих репликации.  
  
## <a name="see-also"></a>См. также  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
