---
title: Защита агента чтения журнала | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.LRA.f1
helpviewer_keywords:
- Log Reader Agent Security dialog box
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: adecb551ab312f307489927225974e6679dc6f74
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163586"
---
# <a name="log-reader-agent-security"></a>Безопасность агента чтения журнала
  С помощью диалогового окна **Безопасность агента чтения журнала** можно указать следующее.  
  
-   Учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой запускается на распространителе агент чтения журнала. На учетную запись Windows можно также ссылаться как на *учетную запись процесса*, потому что процесс агента работает под этой учетной записью.  
  
-   Контекст, в котором агент чтения журнала устанавливает соединения с издателем [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Соединение может создаваться с помощью олицетворения учетной записи Windows или в контексте указанной учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    > [!NOTE]  
    >  Агент чтения журнала устанавливает соединения с издателем, даже если издатель и распространитель находятся на одном и том же компьютере. Агент чтения журнала также устанавливает соединения с распространителем, причем эти соединения всегда выполняются с помощью олицетворения учетной записи Windows, под которой работает агент.  
  
     Для издателей Oracle укажите контекст, в котором агент чтения журнала подключается к издателю, в диалоговом окне **Свойства издателя** (доступном из диалогового окна **Свойства распространителя** ). Дополнительные сведения см. в статье [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).  
  
 Все учетные записи должны быть допустимыми, а для каждой учетной записи должен быть указан правильный пароль. Учетные записи и пароли могут быть проверены только после запуска агента.  
  
## <a name="options"></a>Параметры  
 **Учетная запись процесса**  
 Введите учетную запись Windows, под которой запускается на распространителе агент чтения журнала. Указанная учетная запись Windows должна быть, по меньшей мере, членом предопределенной роли базы данных **db_owner** в базе данных распространителя.  
  
 **Пароль** и **Подтверждение пароля**  
 Введите пароль для учетной записи Windows.  
  
 **Соединиться с издателем**  
 Укажите, должен ли агент чтения журнала устанавливать соединения с издателем с помощью олицетворения учетной записи, указанной в текстовом поле **Учетная запись процесса** , или с помощью учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если выбрано использование учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пароль.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует выбирать олицетворение учетной записи Windows, а не учетную запись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Учетная запись Windows или учетная запись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используемая для соединения, должна быть, как минимум, членом предопределенной роли базы данных **db_owner** в базе данных публикации.  
  
## <a name="see-also"></a>См. также  
 [Управление именами для входа и паролями при репликации](security/manage-logins-and-passwords-in-replication.md)   
 [Replication Agent Security Model](security/replication-agent-security-model.md)  (Модель безопасности агента репликации)  
 [Обзор агентов репликации](agents/replication-agents-overview.md)   
 [Рекомендации по защите репликации](security/replication-security-best-practices.md)  
  
  
