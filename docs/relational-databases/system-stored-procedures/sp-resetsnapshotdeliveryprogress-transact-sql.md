---
title: sp_resetsnapshotdeliveryprogress (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
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
- sp_resetsnapshotdeliveryprogress
- sp_resetsnapshotdeliveryprogress_TSQL
helpviewer_keywords:
- sp_resetsnapshotdeliveryprogress
ms.assetid: 5df7d86b-d343-4d9b-88b1-74429ed092e6
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ebe29fc0216e9da2875f259034679ca7479ae013
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spresetsnapshotdeliveryprogress-transact-sql"></a>sp_resetsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает в исходное состояние процесс доставки моментального снимка для подписки по запросу, чтобы доставку моментального снимка можно было начать заново. Выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_resetsnapshotdeliveryprogress [ [ @verbose_level = ] verbose_level ]  
    [ , [ @drop_table = ] 'drop_table' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@verbose_level**=] *verbose_level*  
 Указывает объем возвращаемых сведений. *verbose_level*— **int**, значение по умолчанию **1**. Значение **1** означает, что сообщение об ошибке, возвращаемое, если невозможно получить необходимые блокировки на **MSsnapshotdeliveryprogress** таблицы, и **0** означает, что никакие ошибки не возвращаются.  
  
 [ **@drop_table**=] **"***drop_table***"**  
 Это, следует ли удалить или усечь таблицу, содержащую сведения о ходе выполнения моментального снимка. *drop_table* — **nvarchar(5)**, значение по умолчанию **FALSE**. FALSE означает, что таблица усекается, а TRUE означает, что таблица удаляется.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_resetsnapshotdeliveryprogress** удаляет все строки в **MSsnapshotdeliveryprogress** таблицы. Благодаря этому удаляются все метаданные, оставленные в базе данных подписки предыдущим процессом в ходе доставки моментального снимка.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_resetsnapshotdeliveryprogress**.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
