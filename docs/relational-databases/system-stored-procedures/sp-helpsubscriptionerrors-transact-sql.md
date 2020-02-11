---
title: sp_helpsubscriptionerrors (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpsubscriptionerrors_TSQL
- sp_helpsubscriptionerrors
helpviewer_keywords:
- sp_helpsubscriptionerrors
ms.assetid: 01c8bc21-939e-490d-8cc8-219c068be31e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fe01c857d8a9e27de56538d0e595f3ad89f4d96
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771524"
---
# <a name="sp_helpsubscriptionerrors-transact-sql"></a>sp_helpsubscriptionerrors (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает все ошибки репликации транзакций для заданной подписки. Эта хранимая процедура выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpsubscriptionerrors [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'   
        , [ @publication = ] 'publication'   
        , [ @subscriber = ] 'subscriber'   
        , [ @subscriber_db = ] 'subscriber_db'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'`Имя издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных публикации. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @subscriber = ] 'subscriber'`Имя подписчика. Аргумент *Subscriber* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @subscriber_db = ] 'subscriber_db'`Имя базы данных подписки. Аргумент *subscriber_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**удостоверения**|**int**|Идентификатор ошибки.|  
|**time**|**datetime**|Время появления ошибки.|  
|**error_type_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**source_type_id**|**int**|Идентификатор типа источника ошибки.|  
|**source_name**|**nvarchar (100)**|Имя источника ошибки.|  
|**error_code**|**имеет sysname**|Код ошибки.|  
|**error_text**|**ntext**|Сообщение об ошибке.|  
|**xact_seqno**|**varbinary (16)**|Регистрационный номер транзакции в журнале, запущенной во время ошибки выполнения пакета. Это последовательный номер журнала транзакций, содержащего первую транзакцию в пакете, выполненном с ошибкой. Он используется только агентами распространителя.|  
|**command_id**|**int**|Идентификатор команды пакета, выполненного с ошибкой. Это идентификатор первой команды в пакете, завершенном с ошибкой, используемый только агентами распространителя.|  
|**session_id**|**int**|Идентификатор сеанса агента, во время которого произошла ошибка.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpsubscriptionerrors** используется с репликацией моментальных снимков и репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_helpsubscriptionerrors**.  
  
## <a name="see-also"></a>См. также:  
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
