---
title: "Защита агента моментальных снимков | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.security.SSA.f1
helpviewer_keywords: Snapshot Agent Security dialog box
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 185e46ee83adfa24767f23e0857009e40c5c1645
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="snapshot-agent-security"></a>Безопасность агента моментальных снимков
  Диалоговое окно **Безопасность агента моментальных снимков** позволяет указать следующее:  
  
-   Учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой агент моментальных снимков работает в качестве распространителя. На учетную запись Windows можно также ссылаться как на *учетную запись процесса*, потому что процесс агента работает под этой учетной записью.  
  
-   Контекст, в котором агент моментальных снимков устанавливает соединения с издателем [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Соединение может создаваться с помощью олицетворения учетной записи Windows или в контексте указанной учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    > [!NOTE]  
    >  Агент моментальных снимков устанавливает соединение с издателем, даже если издатель и распространитель находятся на одном компьютере. Кроме того, агент моментальных снимков подключается к распространителю. Эти соединения всегда устанавливаются путем олицетворения учетной записи Windows, под которой запущен агент.  
  
     Для издателей Oracle укажите в диалоговом окне **Свойства издателя** контекст, в котором агент моментальных снимков подключается к издателю (это окно находится в окне **Свойства распространителя** ). Дополнительные сведения см. в статье [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Все учетные записи должны быть допустимыми, а для каждой учетной записи должен быть указан правильный пароль. Учетные записи и пароли могут быть проверены только после запуска агента.  
  
## <a name="options"></a>Параметры  
 **Process account**  
 Введите учетную запись Windows, под которой агент моментальных снимков работает в качестве распространителя. Необходимо, чтобы эта учетная запись Windows удовлетворяла следующим условиям:  
  
-   Она должна быть как минимум членом предопределенной роли базы данных **db_owner** в базе данных распространителя.  
  
-   Она должна обладать разрешениями на запись в хранилище моментальных снимков.  
  
 **Пароль** и **Подтверждение пароля**  
 Введите пароль для учетной записи Windows.  
  
 **Соединиться с издателем**  
 Укажите, следует ли агенту моментальных снимков подключаться к издателю путем олицетворения учетной записи, указанной в текстовом поле **Учетная запись процесса** , либо через учетную запись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если выбрано использование учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пароль.  
  
> [!NOTE]  
>  Рекомендуется использовать олицетворение учетной записи Windows вместо учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Учетная запись Windows или учетная запись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используемая для соединения, должна быть, как минимум, членом предопределенной роли базы данных **db_owner** в базе данных публикации.  
  
## <a name="see-also"></a>См. также:  
 [Управление именами для входа и паролями при репликации](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
