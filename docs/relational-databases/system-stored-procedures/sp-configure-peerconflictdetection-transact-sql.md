---
title: sp_configure_peerconflictdetection (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_configure_peerconflictdetection_TSQL
- sp_configure_peerconflictdetection
helpviewer_keywords:
- sp_configure_peerconflictdetection
ms.assetid: 45117cb2-3247-433f-ba3d-7fa19514b1c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8a8cc9930ddf85dea60999e3b63dbcebaaf42d8f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68215946"
---
# <a name="spconfigurepeerconflictdetection-transact-sql"></a>sp_configure_peerconflictdetection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Настраивает обнаружение конфликта для публикации, которая участвует в топологии одноранговой репликации транзакций. Дополнительные сведения см. в разделе [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md). Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_configure_peerconflictdetection [ @publication = ] 'publication'  
    [ , [ @action = ] 'action']  
    [ , [ @originator_id = ] originator_id ]  
    [ , [ @conflict_retention = ] conflict_retention ]  
    [ , [ @continue_onconflict = ] 'continue_onconflict']  
    [ , [ @local = ] 'local']  
    [ , [ @timeout = ] timeout ]  
  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @publication=] '*публикации*"  
 Имя публикации, для которой должна быть выполнена настройка обнаружения конфликтов. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ @action=] '*действие*"  
 Указывает, должно ли быть включено или отключено обнаружение конфликтов применительно к публикации. *Действие* — **nvarchar(5)** , и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**enable**|Включает обнаружение конфликтов применительно к публикации.|  
|**Отключить**|Отключает обнаружение конфликтов применительно к публикации.|  
|NULL (по умолчанию)||  
  
 [ @originator_id=] *originator_id*  
 Указывает идентификатор в одноранговой топологии. *originator_id* — **int**, значение по умолчанию NULL. Этот идентификатор используется для обнаружения конфликтов, если *действие* присваивается **включить**. Задайте положительное, ненулевое значение идентификатора, которое никогда не использовалось в топологии. Список использованных идентификаторов запросите в системной таблице [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) .  
  
 [ @conflict_retention=] *conflict_retention*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @continue_onconflict=] '*continue_onconflict*"]  
 Определяет, продолжает ли агент распространителя обрабатывать изменения после обнаружения конфликта. *continue_onconflict* — **nvarchar(5)** со значением по умолчанию FALSE.  
  
> [!CAUTION]  
>  Рекомендуется использовать значение по умолчанию FALSE. Если присвоить этому аргументу значение TRUE, агент распространителя будет пытаться обеспечить конвергентность данных в топологии, применяя конфликтующую строку из узла с наибольшим значением идентификатора инициатора. Этот метод не гарантирует конвергенции. После обнаружения конфликта следует убедиться, что топология остается согласованной. Дополнительные сведения см. в подразделе «Обработка конфликтов» раздела [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
 [ @local=] '*локального*"  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @timeout=] *время ожидания*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Хранимая процедура sp_configure_peerconflictdetection используется для одноранговой репликации транзакций. Для использования обнаружения конфликтов, все узлы должны работать под управлением [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или более поздней версии; и обнаружения необходимо включить для всех узлов.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner.  
  
## <a name="see-also"></a>См. также  
 [Обнаружение конфликтов в одноранговой репликации](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Одноранговая репликация транзакций](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
