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
ms.openlocfilehash: 901ad9739966327102ceda6c7d26815daa867888
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68123924"
---
# <a name="sp_gettopologyinfo-transact-sql"></a>sp_gettopologyinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о топологии одноранговой репликации транзакций. Выполните [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) , чтобы получить сведения перед выполнением этой процедуры.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_gettopologyinfo [ @request_id = ] request_id  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @request_id= ] *request_id*  
 Идентификатор запроса состояния топологии. *request_id* имеет **тип int**и значение по умолчанию NULL. Чтобы получить идентификатор, используйте @request_id выходной параметр из [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) или выполните запрос к системной таблице [MSpeer_topologyrequest](../../relational-databases/system-tables/mspeer-topologyrequest-transact-sql.md) .  
  
## <a name="result-sets"></a>Результирующие наборы  
 sp_gettopologyinfo возвращает результирующий набор, имеющий один XML-столбец. Данные в XML-столбце совпадают с данными в [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) системной таблице.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Процедура sp_gettopologyinfo используется в одноранговой репликации транзакций. Перед выполнением sp_gettopologyinfo выполните [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) . Эти процедуры используются мастером настройки одноранговой топологии, однако ими можно также воспользоваться напрямую, если необходимо получить сведения о топологии в формате XML. Если вы предпочитаете табличные результаты, запросите системную таблицу [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) .  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner.  
  
## <a name="see-also"></a>См. также:  
 [Одноранговая репликация транзакций](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
