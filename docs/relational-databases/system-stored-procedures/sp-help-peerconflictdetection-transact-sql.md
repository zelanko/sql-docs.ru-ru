---
description: sp_help_peerconflictdetection (Transact-SQL)
title: sp_help_peerconflictdetection (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_help_peerconflictdetection
- sp_help_peerconflictdetection_TSQL
helpviewer_keywords:
- sp_help_peerconflictdetection
ms.assetid: 59e04107-5eaa-44a1-beb6-ac4f2dbbcb28
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 03dc129a50e9bffdf7052dd0bed2e9d58fb20310
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481190"
---
# <a name="sp_help_peerconflictdetection-transact-sql"></a>sp_help_peerconflictdetection (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает сведения о настройках обнаружения конфликта для публикации, участвующей в топологии одноранговой репликации транзакций.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_peerconflictdetection [ @publication = ] 'publication'  
    [ ,[ @timeout = ] timeout ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @publication =] "*Публикация*"  
 Имя публикации, для которой возвращаются данные. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 [ @timeout =] *время ожидания*  
 Указывает время (в секундах), в течение которого процедура ожидает ответа от каждого из узлов топологии. Если в топологии имеется подписчик, доступный только для чтения, указание значения времени ожидания недопустимо. Подписчик, доступный только для чтения, никогда не ответит на вызов из этой процедуры. *timeout* имеет **тип int**и значение по умолчанию 60.  
  
## <a name="result-sets"></a>Результирующие наборы  
 Процедура sp_help_peerconflictdetection возвращает три результирующих набора. Все они описаны в следующих разделах:  
  
-   [MSpeer_conflictdetectionconfigrequest](../../relational-databases/system-tables/mspeer-conflictdetectionconfigrequest-transact-sql.md)  
  
-   [MSpeer_conflictdetectionconfigresponse](../../relational-databases/system-tables/mspeer-conflictdetectionconfigresponse-transact-sql.md)  
  
-   [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md)  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 Процедура sp_help_peerconflictdetection применяется в одноранговой репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner.  
  
## <a name="see-also"></a>См. также  
 [Обнаружение конфликтов в одноранговой репликации](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Одноранговая репликация транзакций](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
