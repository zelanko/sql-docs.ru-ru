---
title: sp_replmonitorhelpmergesessiondetail (T-SQL)
description: Описывает sp_replmonitorhelpmergesessiondetail хранимую процедуру, которая возвращает подробные сведения об определенном сеансе репликации агент слияния.
ms.custom: seo-lt-2019
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8c09007256e5c336ecfa2ad62c45623fe2c0e5ff
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543242"
---
# <a name="sp_replmonitorhelpmergesessiondetail-transact-sql"></a>sp_replmonitorhelpmergesessiondetail (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Возвращает подробные сведения уровня статьи о заданном сеансе репликации агента слияния, который используется для отслеживания репликации слиянием. Результирующий набор включает строку детализации для каждой статьи, которая была синхронизирована во время сеанса. Он также включает строку, которая представляет инициализацию сеанса и итоговые строки по фазам передачи и загрузки сеанса. Эта хранимая процедура выполняется на распространителе, в базе данных распространителя или на подписчике, в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replmonitorhelpmergesessiondetail [ @session_id = ] session_id  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @session_id = ] session_id` Указывает сеанс агента. *session_id* имеет **тип int** и не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**PhaseID**|**int**|Фаза сеанса синхронизации может принимать одно из следующих значений:<br /><br /> **0** = строка инициализации или сводка<br /><br /> **1** = отправка<br /><br /> **2** = Загрузка|  
|**артикленаме**|**sysname**|Название синхронизируемой статьи. **Артикленаме** также содержит сводные данные для строк в результирующем наборе, которые не представляют сведения о статье.|  
|**PercentComplete**|**decimal**|Отображает процент общих изменений, сделанных в заданной строке детализации статьи, для выполняемого в данный момент или неудачного сеанса.|  
|**RelativeCost**|**decimal**|Отображает время, потраченное на синхронизацию статьи, в виде процента от общего времени синхронизации для сеанса.|  
|**Длительность**|**int**|Продолжительность сеанса агента.|  
|**Вставки**|**int**|Число вставок за сеанс.|  
|**Обновления**|**int**|Число обновлений за сеанс.|  
|**Deletes**|**int**|Число удалений за сеанс.|  
|**Конфликты**|**int**|Число возникших за сеанс конфликтов.|  
|**Код ошибки**|**int**|Идентификатор ошибки сеанса.|  
|**SeqNo**|**int**|Порядок сеансов в результирующем наборе.|  
|**RowType**|**int**|Указывает, какой тип сведений отражен в каждой строке результирующего набора:<br /><br /> **0** = инициализация<br /><br /> **1** = сводка по отправке<br /><br /> **2** = сведения о передаче статьи<br /><br /> **3** = сводка по загрузке<br /><br /> **4** = сведения о скачивании статьи|  
|**SchemaChanges**|**int**|Число изменений схемы за сеанс.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_replmonitorhelpmergesessiondetail** используется для наблюдения за репликацией слиянием.  
  
 При выполнении на подписчике **sp_replmonitorhelpmergesessiondetail** возвращает только подробные сведения о последних 5 сеансах агент слияния.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли базы данных **db_owner** или **replmonitor** в базе данных распространителя на распространителе или в базе данных подписки на подписчике могут выполнять **sp_replmonitorhelpmergesessiondetail**.  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
