---
title: "MSSQL_ENG020596 | Документация Майкрософт"
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
- MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5eae24c46d8a92eb3906ba83ebac735c1ee563a9
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqleng020596"></a>MSSQL_ENG020596
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|20596|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Только '%s' или члены роли db_owner могут удалить анонимный агент.|  
  
## <a name="explanation"></a>Объяснение  
 У вас нет необходимых разрешений на удаление агента для анонимной подписки. Имя входа, используемое при вызове [sp_dropanonymousagent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql.md), должно принадлежать члену предопределенной роли сервера **sysadmin** на распространителе, или предопределенной роли базы данных **db_owner** в базе данных распространителя, или пользователю, который выполнял первый запуск этого агента.  
  
## <a name="user-action"></a>Действие пользователя  
 Войдите в систему с соответствующими учетными данными и выполните **sp_dropanonymousagent**.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  

