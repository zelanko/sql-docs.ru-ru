---
description: IHextendedSubscriptionView (Transact-SQL)
title: Ихекстендедсубскриптионвиев (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHextendedSubscriptionView_TSQL
- IHextendedSubscriptionView
dev_langs:
- TSQL
helpviewer_keywords:
- IHextendedSubscriptionView view
ms.assetid: 124756a4-463a-4a81-bf5b-de7e8ffc7a62
author: stevestein
ms.author: sstein
ms.openlocfilehash: aca2ddea9625b5b2a40fea6ef27d6f218a71cda0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485446"
---
# <a name="ihextendedsubscriptionview-transact-sql"></a>IHextendedSubscriptionView (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Представление **ихекстендедсубскриптионвиев** предоставляет сведения о подписке на публикацию, отличную от SQL Server. Это представление хранится в базе данных **распространителя** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|Уникальный идентификатор статьи.|  
|**dest_db**|**sysname**|Имя целевой базы данных.|  
|**srvid**|**smallint**|Уникальный идентификатор подписчика.|  
|**login_name**|**sysname**|Имя входа, используемое для подключения к подписчику.|  
|**distribution_jobid**|**binary**|Идентифицирует задание агента распространителя.|  
|**publisher_database_id**|**int**|Определяет базу данных публикации.|  
|**subscription_type**|**int**|Тип подписки.<br /><br /> **0** = Push-агент распространителя запускается на подписчике.<br /><br /> **1** = по запросу — агент распространителя запускается на распространителе.|  
|**sync_type**|**tinyint**|Тип начальной синхронизации.<br /><br /> **1** = автоматический<br /><br /> **2** = нет|  
|**status**|**tinyint**|Состояние подписки.<br /><br /> **0** = неактивно<br /><br /> **1** = подписано<br /><br /> **2** = активно|  
|**snapshot_seqno_flag**|**bit**|Указывает, используется ли порядковый номер моментального снимка.|  
|**independent_agent**|**bit**|Показывает наличие изолированного агента распространителя для этой публикации.<br /><br /> **0** = публикация использует общий агент распространения, а каждая пара базы данных издателя или подписчика имеет один общий агент.<br /><br /> **1** = для этой публикации существует изолированный агент распространения.|  
|**subscription_time**|**datetime**|Только для внутреннего применения.|  
|**loopback_detection**|**bit**|Применяется к подпискам, которые являются частью двунаправленной топологии репликации транзакций. Механизм распознавания обратной связи определяет, отправляет ли агент распространителя транзакции, созданные в подписчике, обратно подписчику:<br /><br /> **1** = не отправляет обратно.<br /><br /> **0** = отправляет обратно.|  
|**agent_id**|**int**|Уникальный идентификатор агента распространителя.|  
|**update_mode**|**tinyint**|Указывает один из следующих типов режима обновления:<br /><br /> **0** = только для чтения.<br /><br /> **1** = немедленное обновление.<br /><br /> **2** = обновление в очереди с помощью очереди сообщений.<br /><br /> **3** = немедленное обновление с очередью обновлений как отработка отказа с помощью очереди сообщений.<br /><br /> **4** = обновление в очереди с использованием очереди SQL Server.<br /><br /> **5** = немедленное обновление с отработкой отказа обновления посредством очередей с помощью очереди SQL Server.|  
|**publisher_seqno**|**varbinary (16)**|Последовательный номер транзакции на издателе для этой подписки.|  
|**ss_cplt_seqno**|**varbinary (16)**|Последовательный номер, используемый для обозначения завершения одновременной обработки моментальных снимков.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
