---
title: "MSSQL_ENG021286 | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG021286 error
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a604f0e14e831ccec27f56fcca446301ef985ed1
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="mssqleng021286"></a>MSSQL_ENG021286
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21286|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Таблица конфликтов "%s" не существует.|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка возникает, если для статьи, указанной в [sysmergearticles (Transact-SQL)](../../relational-databases/system-tables/sysmergearticles-transact-sql.md), не существует таблица конфликтов. Эта ошибка может возникнуть при попытке добавить или удалить столбец в таблице, опубликованной для репликации слиянием.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполните инструкцию [DBCC CHECKDB (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) в базе данных с отсутствующей таблицей конфликтов, чтобы убедиться в отсутствии проблем согласованности данных.  
  
 Если таблица конфликтов отсутствует на подписчике, удалите подписку и создайте ее заново. Если таблица конфликтов отсутствует на издателе, удалите все подписки, удалите публикацию, а затем заново создайте публикацию и все подписки. Дополнительные сведения см. в статьях [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md) и [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
