---
title: Защита агента моментальных снимков | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.security.SSA.f1
helpviewer_keywords:
- Snapshot Agent Security dialog box
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2eeaa27bc549be57503bfa13ec1de5807b9c7e35
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767648"
---
# <a name="snapshot-agent-security"></a>Безопасность агента моментальных снимков
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Диалоговое окно **Безопасность агента моментальных снимков** позволяет указать следующее:  
  
-   Учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой агент моментальных снимков работает в качестве распространителя. На учетную запись Windows можно также ссылаться как на *учетную запись процесса*, потому что процесс агента работает под этой учетной записью.  
  
-   Контекст, в котором агент моментальных снимков устанавливает соединения с издателем [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Соединение может создаваться с помощью олицетворения учетной записи Windows или в контексте указанной учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    > [!NOTE]  
    >  Агент моментальных снимков устанавливает соединение с издателем, даже если издатель и распространитель находятся на одном компьютере. Кроме того, агент моментальных снимков подключается к распространителю. Эти соединения всегда устанавливаются путем олицетворения учетной записи Windows, под которой запущен агент.  
  
     Для издателей Oracle укажите в диалоговом окне **Свойства издателя** контекст, в котором агент моментальных снимков подключается к издателю (это окно находится в окне **Свойства распространителя** ). Дополнительные сведения см. в статье [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Все учетные записи должны быть допустимыми, а для каждой учетной записи должен быть указан правильный пароль. Учетные записи и пароли могут быть проверены только после запуска агента.  
  
## <a name="options"></a>Параметры  
 **Учетная запись процесса**  
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
 [Идентификатор и управление доступом для репликации](../../relational-databases/replication/security/identity-and-access-control-replication.md)   
 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)  (Модель безопасности агента репликации)  
 [Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
