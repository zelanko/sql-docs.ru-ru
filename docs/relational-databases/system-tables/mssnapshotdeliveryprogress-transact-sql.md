---
title: MSsnapshotdeliveryprogress (Transact-SQL) | Документы Microsoft
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
- MSsnapshotdeliveryprogress_TSQL
- MSsnapshotdeliveryprogress
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshotdeliveryprogress system table
ms.assetid: 9164bfe2-6fc4-4b52-946a-09ea3cf67041
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 0989999080b57bf2f78b6a297df29a0ee8a32f35
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mssnapshotdeliveryprogress-transact-sql"></a>MSsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsnapshotdeliveryprogress** таблица используется для отслеживания файлов, успешно доставленные подписчику при применении моментального снимка. Эти данные используются для возобновления доставки файлов в случае, если во время сеанса агент слияния не смог успешно доставить все файлы, чтобы те же самые файлы не доставлялись повторно при следующем запуске агента слияния. Эта таблица хранится на подписчике в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_token**|**nvarchar(260)**|Определяет путь к папке моментального снимка, откуда файл был успешно доставлен. Для публикаций, использующих параметризованные фильтры, строка **dynsnap** будет присоединена к значению.|  
|**progress_token_hash**|**int**|Значение хэша, созданное на основе значения *progress_token* , используемый для увеличения эффективности данного *progress_token* значение.|  
|**progress_token**|**nvarchar(500)**|Определяет успешно доставленный файл; значение является сочетанием имени файла и пути.|  
|**progress_timestamp**|**datetime**|**Datetime** значение, указывающее, когда файл моментального снимка был успешно доставлен.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
