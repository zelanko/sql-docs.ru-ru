---
title: Защита агента чтения очереди | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.QRA.f1
helpviewer_keywords:
- Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8b0780016cce58223ebe2e5b14726e535a440f41
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48160334"
---
# <a name="queue-reader-agent-security"></a>Безопасность агента чтения очереди
  Диалоговое окно **Безопасность агента чтения очереди** позволяет указать учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которой агент чтения очереди запускается и создает локальные соединения с распространителем. Агент устанавливает соединение с издателем, используя учетную запись, указанную в диалоговом окне **Свойства издателя** (доступном из диалогового окна **Свойства распространителя** ). Агент устанавливает соединение с подписчиком, используя тот же контекст, что и агент распространителя для подписки. Дополнительные сведения см. в статье [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).  
  
 Учетная запись должна быть действительной, а указанный для нее пароль — верным. Учетные записи и пароли могут быть проверены только после запуска агента.  
  
## <a name="options"></a>Параметры  
 **Учетная запись процесса**  
 Введите учетную запись Windows, с которой агент чтения очереди работает на распространителе. Указанная учетная запись Windows должна быть, по меньшей мере, членом предопределенной роли базы данных **db_owner** в базе данных распространителя.  
  
 **Пароль** и **Подтверждение пароля**  
 Введите пароль для учетной записи Windows.  
  
## <a name="see-also"></a>См. также  
 [Управление именами для входа и паролями при репликации](security/manage-logins-and-passwords-in-replication.md)   
 [Replication Agent Security Model](security/replication-agent-security-model.md)  (Модель безопасности агента репликации)  
 [Обзор агентов репликации](agents/replication-agents-overview.md)   
 [Рекомендации по защите репликации](security/replication-security-best-practices.md)  
  
  
