---
title: sp_replmonitorhelpmergesessiondetail (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- sp_replmonitorhelpmergesessiondetail
- sp_replmonitorhelpmergesessiondetail_TSQL
helpviewer_keywords:
- sp_replmonitorhelpmergesessiondetail
ms.assetid: 805c92fc-3169-410c-984d-f37e063b791d
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 44bb40f02a7e8f537141f34db3bf4cc38c8b093f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
 [ **@session_id** =] *session_id*  
 Задает сеанс агента. *session_id* — **int** без значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**PhaseID**|**int**|Фаза сеанса синхронизации может принимать одно из следующих значений:<br /><br /> **0** = Строка инициализации или итоговая строка<br /><br /> **1** = выгрузка<br /><br /> **2** = загрузка|  
|**Столбец ArticleName**|**sysname**|Название синхронизируемой статьи. **Столбец ArticleName** также содержит сводные данные для строк в результирующем наборе, которые не отражают подробности о статье.|  
|**PercentComplete**|**decimal**|Отображает процент общих изменений, сделанных в заданной строке детализации статьи, для выполняемого в данный момент или неудачного сеанса.|  
|**RelativeCost**|**decimal**|Отображает время, потраченное на синхронизацию статьи, в виде процента от общего времени синхронизации для сеанса.|  
|**Длительность**|**int**|Продолжительность сеанса агента.|  
|**Вставки**|**int**|Число вставок за сеанс.|  
|**Updates**|**int**|Число обновлений за сеанс.|  
|**Deletes**|**int**|Число удалений за сеанс.|  
|**Конфликты**|**int**|Число возникших за сеанс конфликтов.|  
|**Идентификатор ошибки**|**int**|Идентификатор ошибки сеанса.|  
|**Seqno не**|**int**|Порядок сеансов в результирующем наборе.|  
|**Язык**|**int**|Указывает, какой тип сведений отражен в каждой строке результирующего набора:<br /><br /> **0** = инициализация<br /><br /> **1** = итоги передачи<br /><br /> **2** = подробности передачи статьи<br /><br /> **3** = итоги загрузки<br /><br /> **4** = подробности загрузки статьи|  
|**Изменений схемы**|**int**|Число изменений схемы за сеанс.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_replmonitorhelpmergesessiondetail** используется для наблюдения за репликацией слиянием.  
  
 При выполнении на подписчике, **sp_replmonitorhelpmergesessiondetail** только возвращает подробные сведения о последних 5 сеансов агента слияния.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **db_owner** или **replmonitor** предопределенной роли базы данных на базу данных распространителя на распространителе или на базе данных подписки на подписчике могут выполнять **sp_ replmonitorhelpmergesessiondetail**.  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
