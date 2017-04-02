---
title: "Безопасность агента чтения очереди | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.security.QRA.f1"
helpviewer_keywords: 
  - "диалоговое окно «Безопасность агента чтения очереди»"
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Безопасность агента чтения очереди
  Диалоговое окно **Безопасность агента чтения очереди** позволяет указать учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которой агент чтения очереди запускается и создает локальные соединения с распространителем. Агент подключается к издателю с помощью учетной записи, указанной в **Свойства издателя** диалоговое окно (доступные из **Свойства распространителя** диалоговое окно); агент соединяется с подписчиком, используя тот же контекст как агент распространителя для подписки. Дополнительные сведения см. в статье [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Учетная запись должна быть действительной, а указанный для нее пароль — верным. Учетные записи и пароли могут быть проверены только после запуска агента.  
  
## Параметры  
 **Учетная запись процесса**  
 Введите учетную запись Windows, с которой агент чтения очереди работает на распространителе. Учетная запись Windows должна как минимум быть членом **db_owner** фиксированной роли базы данных в базе данных распространителя.  
  
 **Пароль** и **Подтверждение пароля**  
 Введите пароль для учетной записи Windows.  
  
## См. также:  
 [Управление именами входа и паролями в репликации](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  