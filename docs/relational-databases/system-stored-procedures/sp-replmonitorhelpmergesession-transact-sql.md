---
title: sp_replmonitorhelpmergesession (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpmergesession_TSQL
- sp_replmonitorhelpmergesession
helpviewer_keywords:
- sp_replmonitorhelpmergesession
ms.assetid: a0400ba8-9609-4901-917e-925e119103a1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1781e22e97870e7b9c26e7de397d77600ecbe1ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771241"
---
# <a name="sp_replmonitorhelpmergesession-transact-sql"></a>sp_replmonitorhelpmergesession (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
`[ @agent_name = ] 'agent_name'`Имя агента. *agent_name* имеет тип **nvarchar (100)** и не имеет значения по умолчанию.  
  
`[ @hours = ] hours`Интервал времени (в часах), в течение которого возвращаются данные сеанса агента с предысторией. *часы* — это **int**, который может быть одним из следующих диапазонов.  
  
|Значение|Description|  
|-----------|-----------------|  
|< **0,0**|Возвращает сведения о последних запусках агента, максимум до 100 раз.|  
|**0** (по умолчанию)|Возвращает сведения обо всех последних запусках агента.|  
|> **0,0**|Возвращает сведения о запусках агента, произошедших за последние *часы* (в часах).|  
  
`[ @session_type = ] session_type`Фильтрует результирующий набор на основе конечного результата сеанса. *session_type* имеет **тип int**и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**1** (по умолчанию)|Сеанс агента с успешным результатом или с требованием повторения.|  
|**0**|Сеанс агента с неудачным результатом.|  
  
`[ @publisher = ] 'publisher'`Имя издателя. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL. Этот параметр используется при выполнении **sp_replmonitorhelpmergesession** на подписчике.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных публикации. Аргумент *publisher_db* имеет тип **sysname**и значение по умолчанию NULL. Этот параметр используется при выполнении **sp_replmonitorhelpmergesession** на подписчике.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и значение по умолчанию NULL. Этот параметр используется при выполнении **sp_replmonitorhelpmergesession** на подписчике.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**Session_id**|**int**|Идентификатор сеанса для задания агента.|  
|**Состояние**|**int**|Состояние запуска агента:<br /><br /> **1** = запуск<br /><br /> **2** = выполнена<br /><br /> **3** = выполняется<br /><br /> **4** = бездействие<br /><br /> **5** = повторная попытка<br /><br /> **6** = сбой|  
|**StartTime**|**datetime**|Время начала сеанса для задания агента.|  
|**EndTime**|**datetime**|Время завершения сеанса для задания агента.|  
|**Длительность**|**int**|Совокупная продолжительность сеанса выполнения задания, в секундах.|  
|**UploadedCommands**|**int**|Количество команд, переданных за время сеанса работы агента.|  
|**DownloadedCommands**|**int**|Количество команд, принятых за время сеанса работы агента.|  
|**еррормессажес**|**int**|Количество сообщений об ошибках, которые были сформированы во время сеанса работы агента.|  
|**ErrorID**|**int**|Идентификатор возникшей ошибки.|  
|**PercentageDone**|**Decimal**|Приближенный процент общих изменений, которые уже были переданы в активном сеансе.|  
|**TimeRemaining**|**int**|Приблизительное число секунд, оставшееся до завершения активного сеанса.|  
|**CurrentPhase**|**int**|Текущая фаза активного сеанса, которая может принимать одно из следующих значений:<br /><br /> **1** = отправка<br /><br /> **2** = Загрузка|  
|**ластмессаже**|**nvarchar (500)**|Последнее сообщение, которое было записано в журнал агентом слияния во время сеанса.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_replmonitorhelpmergesession** используется для наблюдения за репликацией слиянием.  
  
 При выполнении на подписчике **sp_replmonitorhelpmergesession** возвращает сведения только о последних пяти сеансах агент слияния.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли базы данных **db_owner** или **replmonitor** в базе данных распространителя на распространителе или в базе данных подписки на подписчике могут выполнять **sp_replmonitorhelpmergesession**.  
  
## <a name="see-also"></a>См. также:  
 [Программный мониторинг репликации](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
