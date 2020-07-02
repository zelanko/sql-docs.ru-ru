---
title: MSpeer_conflictdetectionconfigrequest (T-SQL)
description: Описывает MSPeer_conflictdetectionconfigurerequest хранимую процедуру, используемую для мониторинга запросов конфигурации на уровне топологии для одноранговой публикации.
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_conflictdetectionconfigrequest_TSQL
- MSpeer_conflictdetectionconfigrequest
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_conflictdetectionconfigurerequest
ms.assetid: 83afa0ca-707e-4468-a888-228268ed4e10
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 17872cfae8da4d8f28b6031be168aa60a063d54b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730803"
---
# <a name="mspeer_conflictdetectionconfigrequest-transact-sql"></a>MSpeer_conflictdetectionconfigrequest (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Используется в одноранговой репликации для отслеживания запросов настройки на уровне топологии для публикации. Эта таблица хранится в базе данных публикации.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|идентификатор|**int**|Идентифицирует запрос настройки конфликта. Столбец request_id в [MSpeer_conflictdetectionconfigresponse](../../relational-databases/system-tables/mspeer-conflictdetectionconfigresponse-transact-sql.md) использует это значение.|  
|публикация|**sysname**|Имя публикации, из которой был сформирован запрос настройки конфликта.|  
|sent_date|**datetime**|Дата и время выдачи запроса настройки конфликта.|  
|timeout|**int**|Время, в течение которого процедура должна ожидать, пока все одноранговые узлы вернут сведения о конфликте.|  
|modified_date|**datetime**|Дата и время завершения стадии.|  
|progress_phase|**nvarchar(32)**|Определяет текущую стадию обработки как одно из следующих значений:<br /><br /> Запуск<br /><br /> Exploring topology (исследование топологии)<br /><br /> Exploring topology (сбор данных о состоянии)<br /><br /> Собранные данные о состоянии|  
|phase_timed_out|**bit**|Указывает, что время ожидания текущей стадии истекло.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
