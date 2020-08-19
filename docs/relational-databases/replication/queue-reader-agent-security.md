---
description: Безопасность агента чтения очереди
title: Защита агента чтения очереди | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.security.QRA.f1
helpviewer_keywords:
- Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dc5a8ff1f69f26fc7925a2314151e9437ffefc65
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88406250"
---
# <a name="queue-reader-agent-security"></a>Безопасность агента чтения очереди
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Диалоговое окно **Безопасность агента чтения очереди** позволяет указать учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которой агент чтения очереди запускается и создает локальные соединения с распространителем. Агент устанавливает соединение с издателем, используя учетную запись, указанную в диалоговом окне **Свойства издателя** (доступном из диалогового окна **Свойства распространителя** ). Агент устанавливает соединение с подписчиком, используя тот же контекст, что и агент распространителя для подписки. Дополнительные сведения см. в статье [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Учетная запись должна быть действительной, а указанный для нее пароль — верным. Учетные записи и пароли могут быть проверены только после запуска агента.  
  
## <a name="options"></a>Параметры  
 **Учетная запись процесса**  
 Введите учетную запись Windows, с которой агент чтения очереди работает на распространителе. Указанная учетная запись Windows должна быть, по меньшей мере, членом предопределенной роли базы данных **db_owner** в базе данных распространителя.  
  
 **Пароль** и **Подтверждение пароля**  
 Введите пароль для учетной записи Windows.  
  
## <a name="see-also"></a>См. также:  
 [Идентификатор и управление доступом для репликации](../../relational-databases/replication/security/identity-and-access-control-replication.md)   
 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)  (Модель безопасности агента репликации)  
 [Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
