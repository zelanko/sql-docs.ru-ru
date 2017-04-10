---
title: "Безопасность агента чтения журнала | Microsoft Docs"
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
  - "sql13.rep.security.LRA.f1"
helpviewer_keywords: 
  - "диалоговое окно «Безопасность агента чтения журнала»"
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Безопасность агента чтения журнала
  С помощью диалогового окна **Безопасность агента чтения журнала** можно указать следующее.  
  
-   Учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой запускается на распространителе агент чтения журнала. На учетную запись Windows можно также ссылаться как на *учетную запись процесса*, потому что процесс агента работает под этой учетной записью.  
  
-   Контекст, в котором агент чтения журнала устанавливает соединения с издателем [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Соединение может создаваться с помощью олицетворения учетной записи Windows или в контексте указанной учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    > [!NOTE]  
    >  Агент чтения журнала устанавливает соединения с издателем, даже если издатель и распространитель находятся на одном и том же компьютере. Агент чтения журнала также устанавливает соединения с распространителем, причем эти соединения всегда выполняются с помощью олицетворения учетной записи Windows, под которой работает агент.  
  
     Для издателей Oracle укажите контекст, под которым агент чтения журнала подключается к издателю в **Свойства издателя** диалоговое окно (доступные из **Свойства распространителя** диалоговое окно). Дополнительные сведения см. в статье [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Все учетные записи должны быть допустимыми, а для каждой учетной записи должен быть указан правильный пароль. Учетные записи и пароли могут быть проверены только после запуска агента.  
  
## Параметры  
 **Учетная запись процесса**  
 Введите учетную запись Windows, под которой запускается на распространителе агент чтения журнала. Учетная запись Windows должна как минимум быть членом **db_owner** фиксированной роли базы данных в базе данных распространителя.  
  
 **Пароль** и **Подтверждение пароля**  
 Введите пароль для учетной записи Windows.  
  
 **Соединиться с издателем**  
 Выберите, будет ли агент чтения журнала должен подключаться к издателю путем олицетворения учетной записи, указанной в **учетную запись процесса** текстовое поле или с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи. Если выбрано использование учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пароль.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует выбирать олицетворение учетной записи Windows, а не с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи.  
  
 Учетная запись Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись, используемая для соединения необходимо как минимум быть членом **db_owner** фиксированной роли базы данных в базе данных публикации.  
  
## См. также:  
 [Управление именами входа и паролями в репликации](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  