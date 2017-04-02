---
title: "MSSQL_ENG020596 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG020596, ошибка"
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG020596
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|20596|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Только '%s' или члены роли db_owner могут удалить анонимный агент.|  
  
## Объяснение  
 У вас нет необходимых разрешений на удаление агента для анонимной подписки. Имя входа, используемое при вызове [sp_dropanonymousagent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql.md) необходимо быть членом группы **sysadmin** фиксированной серверной роли на распространителе или **db_owner** фиксированной роли базы данных в базе данных распространителя или пользователь должен быть тем, кто инициировал первый запуск агента.  
  
## Действие пользователя  
 Войдите в систему с соответствующими учетными данными и выполните **sp_dropanonymousagent**.  
  
## См. также:  
 [Ошибки и события ссылку & #40; Репликация & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  