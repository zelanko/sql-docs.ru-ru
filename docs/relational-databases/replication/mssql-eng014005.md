---
title: MSSQL_ENG014005 | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 020815a26ca91ab53243b543a2d5cc66603d75a3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqleng014005"></a>MSSQL_ENG014005
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14005|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Не удалось удалить публикацию. На нее существует подписка.|  
  
## <a name="explanation"></a>Объяснение  
 Была предпринята попытка удалить публикацию, для которой существуют связанные с ней подписки. Публикация может быть удалена, только если нет подписок, связанных с нею.  
  
## <a name="user-action"></a>Действие пользователя  
 Прежде чем удалять публикацию, необходимо удалить подписки. Если для удаления публикации используется среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , то существует возможность автоматического удаления всех подписок, связанных с публикацией. При использовании хранимых процедур необходимо сначала удалить подписки явным образом. Дополнительные сведения см. в разделах [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md) и [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 Если для данной публикации нет подписок или если данная ошибка возникает на стадии создания публикации, это может свидетельствовать о существовании подписки, которая не была полностью очищена при ее удалении. Выполните хранимую процедуру [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) в базе данных, чтобы удалить все объекты и настройки, связанные с репликацией.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
