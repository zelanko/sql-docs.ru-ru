---
title: sp_replmonitorhelpmergesessiondetail (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpmergesessiondetail
- sp_replmonitorhelpmergesessiondetail_TSQL
helpviewer_keywords:
- sp_replmonitorhelpmergesessiondetail
ms.assetid: 805c92fc-3169-410c-984d-f37e063b791d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dbafa8dd407269fa23ca37574f18a12be519c448
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534638"
---
# <a name="spreplmonitorhelpmergesessiondetail-transact-sql"></a>sp_replmonitorhelpmergesessiondetail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает подробные сведения уровня статьи о заданном сеансе репликации агента слияния, который используется для отслеживания репликации слиянием. Результирующий набор включает строку детализации для каждой статьи, которая была синхронизирована во время сеанса. Он также включает строку, которая представляет инициализацию сеанса и итоговые строки по фазам передачи и загрузки сеанса. Эта хранимая процедура выполняется на распространителе, в базе данных распространителя или на подписчике, в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replmonitorhelpmergesessiondetail [ @session_id = ] session_id  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @session_id = ] session_id` Задает сеанс агента. *session_id* — **int** не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**PhaseID**|**int**|Фаза сеанса синхронизации может принимать одно из следующих значений:<br /><br /> **0** = Строка инициализации или итоговая строка<br /><br /> **1** = выгрузка<br /><br /> **2** = загрузки|  
|**Имя_статьи**|**sysname**|Название синхронизируемой статьи. **Имя_статьи** также содержит сводные данные для строк в результирующем наборе, которые не отражают подробности о статье.|  
|**PercentComplete**|**decimal**|Отображает процент общих изменений, сделанных в заданной строке детализации статьи, для выполняемого в данный момент или неудачного сеанса.|  
|**RelativeCost**|**decimal**|Отображает время, потраченное на синхронизацию статьи, в виде процента от общего времени синхронизации для сеанса.|  
|**Длительность**|**int**|Продолжительность сеанса агента.|  
|**Вставки**|**int**|Число вставок за сеанс.|  
|**Updates**|**int**|Число обновлений за сеанс.|  
|**Deletes**|**int**|Число удалений за сеанс.|  
|**Конфликты**|**int**|Число возникших за сеанс конфликтов.|  
|**Идентификатор ошибки**|**int**|Идентификатор ошибки сеанса.|  
|**SeqNo**|**int**|Порядок сеансов в результирующем наборе.|  
|**RowType**|**int**|Указывает, какой тип сведений отражен в каждой строке результирующего набора:<br /><br /> **0** = инициализация<br /><br /> **1** = Сводка передачи<br /><br /> **2** = подробности передачи статьи<br /><br /> **3** = Сводка загрузки<br /><br /> **4** = подробности загрузки статьи|  
|**Изменений схемы**|**int**|Число изменений схемы за сеанс.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_replmonitorhelpmergesessiondetail** используется для наблюдения за репликацией слиянием.  
  
 При выполнении на подписчике, **sp_replmonitorhelpmergesessiondetail** только возвращает подробные сведения о последних 5 сеансах агента слияния.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **db_owner** или **replmonitor** предопределенной роли базы данных в базе данных распространителя на распространителе или в базе данных подписки на подписчике могут выполнять процедуру **sp_ replmonitorhelpmergesessiondetail**.  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
