---
title: Защита агента чтения журнала | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.LRA.f1
helpviewer_keywords:
- Log Reader Agent Security dialog box
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c55292aff126d1955c438c9417ce0651cc6afc94
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63162231"
---
# <a name="log-reader-agent-security"></a>Безопасность агента чтения журнала
  С помощью диалогового окна **Безопасность агента чтения журнала** можно указать следующее.  
  
-   Учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой запускается на распространителе агент чтения журнала. Учетная запись Windows также называется *учетной записью процесса*, так как процесс агента выполняется под этой учетной записью.  
  
-   Контекст, в котором агент чтения журнала устанавливает соединения с [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателем. Соединение может создаваться с помощью олицетворения учетной записи Windows или в контексте указанной учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    > [!NOTE]  
    >  Агент чтения журнала устанавливает соединения с издателем, даже если издатель и распространитель находятся на одном и том же компьютере. Агент чтения журнала также устанавливает соединения с распространителем, причем эти соединения всегда выполняются с помощью олицетворения учетной записи Windows, под которой работает агент.  
  
     Для издателей Oracle укажите контекст, в котором агент чтения журнала подключается к издателю, в диалоговом окне **Свойства издателя** (доступном из диалогового окна **Свойства распространителя** ). Дополнительные сведения см. в разделе [Просмотр и изменение параметров безопасности репликации](security/view-and-modify-replication-security-settings.md).  
  
 Все учетные записи должны быть допустимыми, а для каждой учетной записи должен быть указан правильный пароль. Учетные записи и пароли могут быть проверены только после запуска агента.  
  
## <a name="options"></a>Параметры  
 **Учетная запись процесса**  
 Введите учетную запись Windows, под которой запускается на распространителе агент чтения журнала. Указанная учетная запись Windows должна быть, по меньшей мере, членом предопределенной роли базы данных **db_owner** в базе данных распространителя.  
  
 **Пароль** и **Подтверждение пароля**  
 Введите пароль для учетной записи Windows.  
  
 **Соединение с издателем**  
 Укажите, должен ли агент чтения журнала устанавливать соединения с издателем с помощью олицетворения учетной записи, указанной в текстовом поле **Учетная запись процесса** , или с помощью учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если выбрано использование учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пароль.  
  
> [!NOTE]  
>  
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует выбирать олицетворение учетной записи Windows, а не учетную запись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Учетная запись Windows или учетная запись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используемая для соединения, должна быть, как минимум, членом предопределенной роли базы данных **db_owner** в базе данных публикации.  
  
## <a name="see-also"></a>См. также:  
 [Управление именами входа и паролями в репликации](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Модель безопасности агента репликации](security/replication-agent-security-model.md)   
 [Обзор агентов репликации](agents/replication-agents-overview.md)   
 [Рекомендации по обеспечению безопасности репликации](security/replication-security-best-practices.md)  
  
  
