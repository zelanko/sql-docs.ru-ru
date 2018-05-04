---
title: sp_requestpeertopologyinfo (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sp_requestpeertopologyinfo
- sp_requestpeertopologyinfo_TSQL
helpviewer_keywords:
- sp_requestpeertopologyinfo
ms.assetid: 15cd28bd-5a72-41fb-ae1b-726baaa6fad5
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6e12a3085fc23e24656bcf7e583039ce15ecddeb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sprequestpeertopologyinfo-transact-sql"></a>sp_requestpeertopologyinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Заполняет [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) системная таблица со сведениями о топологии репликации транзакций для коллег. Выполнение [sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md) для получения сведений из таблицы в формате XML.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_requestpeertopologyinfo [ @publication = ] 'publication'  
        [ ,[ @requestid=] request_id OUTPUT  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @publication=] '*публикации*"  
 Имя публикации, для которой должен быть выполнен запрос состояния всей топологии. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ @request_id=] *идентификатор_запроса*  
 Идентификатор, назначенный запросу состояния топологии. *идентификатор_запроса* — **int**, значение по умолчанию NULL. Этот идентификатор может использоваться [sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Процедура sp_requestpeertopologyinfo используется в одноранговой репликации транзакций. Выполните процедуру sp_requestpeertopologyinfo перед выполнением [sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md). Эти процедуры используются мастером настройки одноранговой топологии, однако ими можно также воспользоваться напрямую, если необходимо получить сведения о топологии в формате XML. При желании табличные результаты запроса [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) системной таблицы.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner.  
  
## <a name="see-also"></a>См. также  
 [Одноранговая репликация транзакций](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
