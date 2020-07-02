---
title: Мсреплмонсрешолдметрикс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- msreplmonthresholdmetrics_TSQL
- msreplmonthresholdmetrics
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplmonthresholdmetrics system table
ms.assetid: 0cc9b40a-36ce-485b-9bc2-d4abd5aa6727
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4ffce4df9f6e5dbc366401d5a9d2e6112429deb6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85757807"
---
# <a name="msreplmonthresholdmetrics-transact-sql"></a>MSreplmonthresholdmetrics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  В таблице **мсреплмонсрешолдметрикс** определены метрики, предоставляемые для наблюдения за репликацией. Эта таблица хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|Определяет метрику производительности репликации и может принимать одно из следующих значений.<br /><br /> **1** = истечение срока действия<br /><br /> **2** = задержка<br /><br /> **4** = mergeexpiration<br /><br /> **5** = mergeslowrunduration<br /><br /> **6** = mergefastrunduration<br /><br /> **7** = mergefastrunspeed<br /><br /> **8** = mergefastrunspeed|  
|**title**|**sysname**|Имя метрики производительности репликации.|  
|**warningbitstatus**|**int**|Битовый идентификатор, используемый для предупреждения о нарушении порога одной из следующих метрик.<br /><br /> **1** = истечение срока действия — подписка на публикацию транзакций превысила срок хранения более допустимого порога в процентах от срока хранения.<br /><br /> **2** = задержка — время, затраченное на репликацию данных от издателя транзакций подписчику, превышает пороговое значение в секундах.<br /><br /> **4** = mergeexpiration — подписка на публикацию слиянием превысила срок хранения, превышающий допустимый порог, в процентах от срока хранения.<br /><br /> **8** = mergefastrunduration — время, затраченное на выполнение синхронизации подписки на публикацию слиянием, превышает пороговое значение (в секундах) при быстром сетевом подключении.<br /><br /> **16** = mergeslowrunduration — время, затраченное на выполнение синхронизации подписки на публикацию слиянием, превышает пороговое значение (в секундах) при низком или коммутируемом сетевом подключении.<br /><br /> **32** = mergefastrunspeed — скорость доставки строк во время синхронизации подписки на публикацию слиянием не смогла поддерживать пороговое значение скорости (в строках в секунду) при быстром сетевом подключении.<br /><br /> **64** = mergefastrunspeed — скорость доставки строк во время синхронизации подписки на публикацию слиянием не смогла поддерживать пороговое значение скорости (в строках в секунду) по отношению к низкому или коммутируемому сетевому соединению.|  
|**alertmessageid**|**int**|Идентификатор сообщения об ошибке, отображаемого при появлении условий предупреждения о нарушении порогового значения.|  
|**nописание**|**nvarchar (3000)**|Описание метрики производительности репликации.|  
|**default_value**|**sql_variant**|Значение по умолчанию метрики производительности репликации.|  
|**min_value**|**sql_variant**|Минимальное значение связанной метрики производительности репликации.|  
|**max_value**|**sql_variant**|Максимальное значение связанной метрики производительности репликации.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
