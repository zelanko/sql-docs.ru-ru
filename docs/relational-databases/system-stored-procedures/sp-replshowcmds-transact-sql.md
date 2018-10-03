---
title: sp_replshowcmds (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_replshowcmds
- sp_replshowcmds_TSQL
helpviewer_keywords:
- sp_replshowcmds
ms.assetid: 199f5a74-e08e-4d02-a33c-b8ab0db20f44
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40faa94a8d2e43d3a3cab1f20c1a621924b6871e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811372"
---
# <a name="spreplshowcmds-transact-sql"></a>sp_replshowcmds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает команды для транзакций, отмеченных для репликации, в удобочитаемом формате. **sp_replshowcmds** можно выполнять только когда клиентские подключения (а также текущее подключение) не считывают реплицированные транзакции из журнала. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replshowcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@maxtrans** =] *maxtrans*  
 Число транзакций, сведения о которых необходимо возвратить. *maxtrans* — **int**, значение по умолчанию **1**, который указывает максимальное количество транзакций, ожидающих репликации, для которого **sp_replshowcmds** Возвращает сведения.  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_replshowcmds** — это диагностическая процедура, которая возвращает сведения о базе данных публикации, из которого выполняется.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**binary(10)**|Последовательный номер команды.|  
|**originator_id**|**int**|Идентификатор инициатора команды всегда **0**.|  
|**publisher_database_id**|**int**|Идентификатор базы данных издателя, всегда **0**.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**type**|**int**|Тип команды.|  
|**команда**|**nvarchar(1024)**|Команда языка [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
  
## <a name="remarks"></a>Примечания  
 **sp_replshowcmds** используется в репликации транзакций.  
  
 С помощью **sp_replshowcmds**, можно просмотреть транзакции, которые в настоящее время не распространяется (транзакции, остающиеся в журнале транзакций, которые не были отправлены распространителю).  
  
 Клиенты, использующие **sp_replshowcmds** и **sp_replcmds** в той же базе данных получают ошибку 18752.  
  
 Чтобы избежать этой ошибки, необходимо отключить первый клиент или роль клиента как агент чтения журнала необходимо освободить с помощью процедуры **sp_replflush**. После отключения всех клиентов из средства чтения журнала, **sp_replshowcmds** для успешного выполнения.  
  
> [!NOTE]  
>  **sp_replshowcmds** следует запускать только в целях устранения неполадок с репликацией.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_replshowcmds**.  
  
## <a name="see-also"></a>См. также  
 [Сообщения об ошибках](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_replcmds (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
