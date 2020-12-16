---
description: Создать профиль агента
title: Создать профиль агента | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.profiles.newperfprofile.f1
helpviewer_keywords:
- New Agent Profile dialog box
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: 5abca0ca89a446939f21b1501b22d14e4f7cef64
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97469045"
---
# <a name="new-agent-profile"></a>Создать профиль агента
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Диалоговое окно **Создать профиль агента** позволяет создать новый профиль. Новые профили всегда основываются на существующих, но их можно изменить для соответствия требованиям приложения. После создания профиля его можно применить к текущим и будущим заданиям агента в диалоговом окне **Профили агента** . Значения параметров агента можно изменить в диалоговом окне \<**AgentProfileName>Свойства**.  
  
## <a name="options"></a>Параметры  
 **имя**;  
 Введите имя профиля.  
  
 **Описание**  
 Введите описание профиля.  
  
 **Параметр**  
 Параметры агента, включенные в профиль. Профиль, на котором основан новый профиль, не обязательно указывает значения всех параметров. Для просмотра всех допустимых для данного агента параметров снимите флажок **Показывать только параметры, используемые в этом профиле** . Описание каждого параметра см. в разделах:  
  
-   [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
-   [Агент чтения журнала репликации](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
-   [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
-   [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md)  
  
-   [Replication Queue Reader Agent](../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
 **Значение по умолчанию**  
 Значение по умолчанию для каждого параметра агента.  
  
 **Значение**  
 Значение, указанное для параметра в профиле, на котором основан новый профиль. Измените это поле, чтобы внести изменения в значения параметров.  
  
 **Показывать только параметры, используемые в этом профиле**  
 Снимите флажок, чтобы отобразить все корректные параметры для данного агента.  
  
## <a name="see-also"></a>См. также:  
 [Работа с профилями агента репликации](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Профили агента репликации](../../relational-databases/replication/agents/replication-agent-profiles.md)  
  
  
