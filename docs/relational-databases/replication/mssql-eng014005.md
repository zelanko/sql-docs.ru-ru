---
title: MSSQL_ENG014005 | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 2331221ea8a15935b91a7ba8cc6691dd27cec4e3
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770498"
---
# <a name="mssqleng014005"></a>MSSQL_ENG014005
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
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
  
  
