---
title: sp_gettopologyinfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_gettopologyinfo_TSQL
- sp_gettopologyinfo
helpviewer_keywords:
- sp_gettopologyinfo
ms.assetid: 8bbe8a06-a4aa-4219-8402-12db6a4682c6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4b5532a5c9dfba03a0e2b9b2fe649912cd0535cc
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52764556"
---
# <a name="spgettopologyinfo-transact-sql"></a>sp_gettopologyinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о топологии одноранговой репликации транзакций. Выполнение [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) для сбора сведений, перед выполнением этой процедуры.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_gettopologyinfo [ @request_id = ] request_id  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @request_id=] *request_id*  
 Идентификатор запроса состояния топологии. *Идентификатор request_id* — **int**, значение по умолчанию NULL. Чтобы получить идентификатор, используйте @request_id из выходного параметра [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) или запросить [MSpeer_topologyrequest](../../relational-databases/system-tables/mspeer-topologyrequest-transact-sql.md) системная таблица.  
  
## <a name="result-sets"></a>Результирующие наборы  
 sp_gettopologyinfo возвращает результирующий набор, имеющий один XML-столбец. Данные в XML-столбца является таким же, как данные в [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) системная таблица.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_gettopologyinfo используется в одноранговой репликации транзакций. Выполнение [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) перед выполнением процедуры sp_gettopologyinfo выполните. Эти процедуры используются мастером настройки одноранговой топологии, однако ими можно также воспользоваться напрямую, если необходимо получить сведения о топологии в формате XML. При желании табличные результаты запроса [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) системная таблица.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner.  
  
## <a name="see-also"></a>См. также  
 [Одноранговая репликация транзакций](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
