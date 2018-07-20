---
title: MSreplmonthresholdmetrics (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- msreplmonthresholdmetrics_TSQL
- msreplmonthresholdmetrics
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplmonthresholdmetrics system table
ms.assetid: 0cc9b40a-36ce-485b-9bc2-d4abd5aa6727
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c72fccdc6c23e65bd94d3ae7ab5a5b0ab0e4eaa9
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101372"
---
# <a name="msreplmonthresholdmetrics-transact-sql"></a>MSreplmonthresholdmetrics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplmonthresholdmetrics** таблицы определяет метрики для наблюдения за репликацией. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|Определяет метрику производительности репликации и может принимать одно из следующих значений.<br /><br /> **1** = истечения срока действия<br /><br /> **2** = latency<br /><br /> **4** = mergeexpiration<br /><br /> **5** = mergeslowrunduration<br /><br /> **6** = mergefastrunduration<br /><br /> **7** = mergefastrunspeed<br /><br /> **8** = mergefastrunspeed|  
|**title**|**sysname**|Имя метрики производительности репликации.|  
|**warningbitstatus**|**int**|Битовый идентификатор, используемый для предупреждения о нарушении порога одной из следующих метрик.<br /><br /> **1** = expiration — подписка на публикацию транзакций превысил срок хранения превышает допустимый порог, в процентах от срока хранения.<br /><br /> **2** = latency — время, необходимое для репликации данных транзакционного издателя на подписчик, превысило пороговое значение, в секундах.<br /><br /> **4** = mergeexpiration — подписка на публикацию слиянием превысил срок хранения превышает допустимый порог, в процентах от срока хранения.<br /><br /> **8** = mergefastrunduration — время, затраченное на завершение синхронизации подписки слиянием, превысило пороговое значение, в секундах, быстрое сетевое подключение.<br /><br /> **16** = mergeslowrunduration — время, затраченное на завершение синхронизации подписки слиянием через медленное или коммутируемое сетевое подключение превышает пороговое значение, в секундах.<br /><br /> **32** = mergefastrunspeed — скорость доставки строк во время синхронизации подписки слиянием не пороговой, в строках в секунду, через быстрое сетевое подключение.<br /><br /> **64** = mergefastrunspeed — скорость доставки строк во время синхронизации подписки слиянием не поддерживать пороговой, в строках в секунду, через медленное или коммутируемое сетевое подключение.|  
|**alertmessageid**|**int**|Идентификатор сообщения об ошибке, отображаемого при появлении условий предупреждения о нарушении порогового значения.|  
|**Описание**|**nvarchar(3000)**|Описание метрики производительности репликации.|  
|**default_value**|**sql_variant**|Значение по умолчанию метрики производительности репликации.|  
|**MIN_VALUE**|**sql_variant**|Минимальное значение связанной метрики производительности репликации.|  
|**MAX_VALUE**|**sql_variant**|Максимальное значение связанной метрики производительности репликации.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
