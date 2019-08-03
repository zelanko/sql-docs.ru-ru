---
title: sp_helptracertokenhistory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helptracertokenhistory_TSQL
- sp_helptracertokenhistory
helpviewer_keywords:
- sp_helptracertokenhistory
ms.assetid: 96910d1c-be76-43eb-9c93-4477e6761749
author: stevestein
ms.author: sstein
ms.openlocfilehash: b8755bea5e318d1ded2631a2253134fd8721a421
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771151"
---
# <a name="sphelptracertokenhistory-transact-sql"></a>sp_helptracertokenhistory (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает подробные сведения о задержке для указанных трассировочных токенов, причем для каждого подписчика возвращается одна строка. Эта хранимая процедура выполняется на издателе в базе данных публикации или на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helptracertokenhistory [ @publication = ] 'publication'   
        , [ @tracer_id = ] tracer_id  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации, в которую был вставлен трассировочный токен. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @tracer_id = ] tracer_id`Идентификатор трассировочного токена в таблице [Transact-SQL &#40;&#41; MStracer_tokens](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) , для которой возвращаются данные журнала. *tracer_id* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @publisher = ] 'publisher'`Имя издателя. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]
>  Этот параметр следует указывать только для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, не являющихся.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных публикации. *publisher_db* имеет тип **sysname**и значение по умолчанию NULL. Этот параметр не учитывается, если хранимая процедура выполняется на издателе.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**distributor_latency**|**bigint**|Количество секунд между фиксированием записи трассировочного токена у издателя и фиксированием записи у распространителя.|  
|**подписчик**|**sysname**|Имя подписчика, получившего трассировочный токен.|  
|**subscriber_db**|**sysname**|Имя базы данных подписки, в которую была вставлена запись трассировочного токена.|  
|**subscriber_latency**|**bigint**|Количество секунд между фиксированием записи трассировочного токена у распространителя и фиксированием записи у подписчика.|  
|**overall_latency**|**bigint**|Количество секунд между фиксированием записи трассировочного токена у издателя и фиксированием записи трассировочного токена у подписчика.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_helptracertokenhistory** используется в репликации транзакций.  
  
 Выполните [sp_helptracertokens &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) , чтобы получить список трассировочных токенов для публикации.  
  
 Значение NULL в результирующем наборе означает, что статистика задержек не может быть определена. Причина этого в том, что трассировочный токен не был получен распространителем или одним из подписчиков.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-helptracertokenhistor_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , предопределенной роли базы данных **db_owner** в базе данных публикации или роли предопределенной базы данных **db_owner** или **replmonitor** в базе данных распространителя могут выполнять **sp_ хелптрацертокенхистори**.  
  
## <a name="see-also"></a>См. также  
 [Измерение задержки и проверка правильности соединений для репликации транзакций](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_deletetracertokenhistory &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)  
  
  
