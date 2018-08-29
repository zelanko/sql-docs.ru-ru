---
title: sp_repldone (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_repldone
- sp_repldone_TSQL
helpviewer_keywords:
- sp_repldone
ms.assetid: 045d3cd1-712b-44b7-a56a-c9438d4077b9
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eda5dc47a5fa841b29bc01634395acd7fff53ace
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024511"
---
# <a name="sprepldone-transact-sql"></a>sp_repldone (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обновляет запись, которая идентифицирует последнюю распределенную транзакцию сервера. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!CAUTION]  
>  При выполнении **sp_repldone** вручную можно нарушить порядок и согласованность доставленных транзакций. **sp_repldone** следует использовать только для устранения неполадок репликации под руководством опытного специалиста по репликации.  
  
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
 [  **@xactid=**] *xactid*  
 Имеет порядковый номер транзакции в журнале (LSN) первую запись последней распределенной транзакции сервера. *XactID* — **binary(10)**, не имеет значения по умолчанию.  
  
 [  **@xact_seqno=**] *xact_seqno*  
 — Это номер LSN последней записи последней распределенной транзакции сервера. *xact_seqno* — **binary(10)**, не имеет значения по умолчанию.  
  
 [  **@numtrans=**] *numtrans*  
 — Это количество распределенных транзакций. *numtrans* — **int**, не имеет значения по умолчанию.  
  
 [  **@time=**] *времени*  
 Количество миллисекунд, необходимых для распределения последнего пакета транзакций. *время* — **int**, не имеет значения по умолчанию.  
  
 [  **@reset=**] *сброса*  
 Состояние переустановки. *Сброс* — **int**, не имеет значения по умолчанию. Если **1**, то все реплицированные транзакции в журнале отмечаются как распределенные. Если **0**, журнал транзакций устанавливается на первую реплицированную транзакцию и никакие реплицированные транзакции не отмечаются как распределенные. *Сброс* доступен, только если оба *xactid* и *xact_seqno* равны NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_repldone** используется в репликации транзакций.  
  
 **sp_repldone** используется процессом чтения журнала для отслеживания, какие операции были распространены.  
  
 С помощью **sp_repldone**, вы можете вручную сообщить серверу, что транзакция была реплицирована (отправлена распространителю). Кроме того, эта процедура позволяет изменить транзакцию, отмеченную в качестве следующей транзакции, подлежащей репликации. По списку реплицированных транзакций можно перемещаться вперед и назад. (Все транзакции, номера которых не превышают номера этой транзакции, отмечаются как распределенные.)  
  
 Обязательные параметры *xactid* и *xact_seqno* можно получить с помощью **sp_repltrans** или **sp_replcmds**.  
  
## <a name="permissions"></a>Разрешения  
 Членами **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_repldone**.  
  
## <a name="examples"></a>Примеры  
 Когда *xactid* имеет значение NULL, *xact_seqno* имеет значение NULL, и *Сброс* — **1**, то все реплицированные транзакции в журнале отмечаются как распределенные. Это полезно, если в журнале транзакций имеются реплицированные транзакции, ставшие недействительными, и нужно усечь журнал, например:  
  
```  
EXEC sp_repldone @xactid = NULL, @xact_segno = NULL, @numtrans = 0,     @time = 0, @reset = 1  
```  
  
> [!CAUTION]  
>  Данную процедуру можно использовать в аварийных случаях для усечения журнала транзакций при наличии транзакций, ожидающих репликации.  
  
## <a name="see-also"></a>См. также  
 [sp_replcmds (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
