---
title: MSsnapshotdeliveryprogress (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsnapshotdeliveryprogress_TSQL
- MSsnapshotdeliveryprogress
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshotdeliveryprogress system table
ms.assetid: 9164bfe2-6fc4-4b52-946a-09ea3cf67041
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 67b6a2c048f8e873d6daa447270e00c1eda86c3e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52751456"
---
# <a name="mssnapshotdeliveryprogress-transact-sql"></a>MSsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsnapshotdeliveryprogress** таблица используется для отслеживания файлов, успешно доставленные подписчику при применении моментального снимка. Эти данные используются для возобновления доставки файлов в случае, если во время сеанса агент слияния не смог успешно доставить все файлы, чтобы те же самые файлы не доставлялись повторно при следующем запуске агента слияния. Эта таблица хранится на подписчике в базе данных подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_token**|**nvarchar(260)**|Определяет путь к папке моментального снимка, откуда файл был успешно доставлен. Для публикаций, использующих параметризованные фильтры, строка **dynsnap** будут добавляться на значение.|  
|**progress_token_hash**|**int**|Значение хэша, созданное на основе значения из *progress_token* , используемый для увеличения эффективности заданного *progress_token* значение.|  
|**progress_token**|**nvarchar(500)**|Определяет успешно доставленный файл; значение является сочетанием имени файла и пути.|  
|**progress_timestamp**|**datetime**|**Datetime** значение, указывающее, когда файл моментального снимка был успешно доставлен.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
