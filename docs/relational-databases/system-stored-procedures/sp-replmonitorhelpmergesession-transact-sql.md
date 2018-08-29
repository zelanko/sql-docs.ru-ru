---
title: sp_replmonitorhelpmergesession (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
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
- sp_replmonitorhelpmergesession_TSQL
- sp_replmonitorhelpmergesession
helpviewer_keywords:
- sp_replmonitorhelpmergesession
ms.assetid: a0400ba8-9609-4901-917e-925e119103a1
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 25bacdedf9ed9be6baa5e467cf81b809ff9cab1f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43037677"
---
# <a name="spreplmonitorhelpmergesession-transact-sql"></a>sp_replmonitorhelpmergesession (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о прошедших сеансах работы агента слияния для данной репликации. Возвращается по одной строке на каждый сеанс, который соответствует критерию фильтрации. Эта хранимая процедура, которая используется для наблюдения за репликацией слиянием, выполняется на базе данных распространителя или на базе данных подписки на стороне подписчика.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replmonitorhelpmergesession [ [ @agent_name = ] 'agent_name' ]  
    [ , [ @hours = ] hours ]  
    [ , [ @session_type = ] session_type ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@agent_name** =] **"***agent_name***"**  
 Имя агента. *agent_name* — **nvarchar(100)** не имеет значения по умолчанию.  
  
 [ **@hours** =] *часов*  
 Интервал времени в часах, в течение которого выполняется возврат сведений о сеансе агента истории. *часы* — **int**, который может принимать одно из следующих интервалов.  
  
|Значение|Описание|  
|-----------|-----------------|  
|< **0**|Возвращает сведения о последних запусках агента, максимум до 100 раз.|  
|**0** (по умолчанию)|Возвращает сведения обо всех последних запусках агента.|  
|> **0**|Возвращает сведения о агента запусков, произошедших за последние *часов* количество часов.|  
  
 [ **@session_type** =] *session_type*  
 Фильтрует результирующий набор на основе результата завершения сеанса. *session_type* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1** (по умолчанию)|Сеанс агента с успешным результатом или с требованием повторения.|  
|**0**|Сеанс агента с неудачным результатом.|  
  
 [ **@publisher** =] **"***издателя***"**  
 Имя издателя. *издатель* — **sysname**, значение по умолчанию NULL. Этот параметр используется при выполнении **sp_replmonitorhelpmergesession** на подписчике.  
  
 [ **@publisher_db** =] **"***publisher_db***"**  
 Имя базы данных публикации. *publisher_db* — **sysname**, значение по умолчанию NULL. Этот параметр используется при выполнении **sp_replmonitorhelpmergesession** на подписчике.  
  
 [  **@publication=** ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, значение по умолчанию NULL. Этот параметр используется при выполнении **sp_replmonitorhelpmergesession** на подписчике.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Session_id**|**int**|Идентификатор сеанса для задания агента.|  
|**Состояние**|**int**|Состояние запуска агента:<br /><br /> **1** = start<br /><br /> **2** = успешно<br /><br /> **3** = выполняется<br /><br /> **4** = бездействует<br /><br /> **5** = повторение<br /><br /> **6** = неуспешное завершение|  
|**StartTime**|**datetime**|Время начала сеанса для задания агента.|  
|**EndTime**|**datetime**|Время завершения сеанса для задания агента.|  
|**Длительность**|**int**|Совокупная продолжительность сеанса выполнения задания, в секундах.|  
|**UploadedCommands**|**int**|Количество команд, переданных за время сеанса работы агента.|  
|**DownloadedCommands**|**int**|Количество команд, принятых за время сеанса работы агента.|  
|**ErrorMessages**|**int**|Количество сообщений об ошибках, которые были сформированы во время сеанса работы агента.|  
|**Идентификатор ошибки**|**int**|Идентификатор возникшей ошибки.|  
|**PercentageDone**|**decimal**|Приближенный процент общих изменений, которые уже были переданы в активном сеансе.|  
|**TimeRemaining**|**int**|Приблизительное число секунд, оставшееся до завершения активного сеанса.|  
|**CurrentPhase**|**int**|Текущая фаза активного сеанса, которая может принимать одно из следующих значений:<br /><br /> **1** = выгрузка<br /><br /> **2** = загрузки|  
|**LastMessage**|**nvarchar(500)**|Последнее сообщение, которое было записано в журнал агентом слияния во время сеанса.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_replmonitorhelpmergesession** используется для наблюдения за репликацией слиянием.  
  
 При выполнении на подписчике, **sp_replmonitorhelpmergesession** возвращает только сведения о последних пяти сеансах агента слияния.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **db_owner** или **replmonitor** предопределенной роли базы данных в базе данных распространителя на распространителе или в базе данных подписки на подписчике могут выполнять процедуру **sp_ replmonitorhelpmergesession**.  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
