---
title: MSSQL_ENG014005 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 418628c33764c6e765e8ba855da20f0890f6191a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52800716"
---
# <a name="mssqleng014005"></a>MSSQL_ENG014005
    
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
 Прежде чем удалять публикацию, необходимо удалить подписки. Если для удаления публикации используется среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , то существует возможность автоматического удаления всех подписок, связанных с публикацией. При использовании хранимых процедур необходимо сначала удалить подписки явным образом. Дополнительные сведения см. в разделах [Delete a Push Subscription](delete-a-push-subscription.md) и [Delete a Pull Subscription](delete-a-pull-subscription.md).  
  
 Если для данной публикации нет подписок или если данная ошибка возникает на стадии создания публикации, это может свидетельствовать о существовании подписки, которая не была полностью очищена при ее удалении. Выполните хранимую процедуру [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) в базе данных, чтобы удалить все объекты и настройки, связанные с репликацией.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)  
  
  
