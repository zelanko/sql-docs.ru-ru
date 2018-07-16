---
title: Создать профиль агента | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.newperfprofile.f1
helpviewer_keywords:
- New Agent Profile dialog box
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b879f333ce4d3ae038819a736579bbf3195fff1b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256393"
---
# <a name="new-agent-profile"></a>Создать профиль агента
  Диалоговое окно **Создать профиль агента** позволяет создать новый профиль. Новые профили всегда основываются на существующих, но их можно изменить для соответствия требованиям приложения. После создания профиля его можно применить к текущим и будущим заданиям агента в диалоговом окне **Профили агента** . Значения параметров агента можно изменить в диалоговом окне \<Свойства **имя_профиля_агента>**.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Введите имя профиля.  
  
 **Описание**  
 Введите описание профиля.  
  
 **Параметр**  
 Параметры агента, включенные в профиль. Профиль, на котором основан новый профиль, не обязательно указывает значения всех параметров. Для просмотра всех допустимых для данного агента параметров снимите флажок **Показывать только параметры, используемые в этом профиле** . Описание каждого параметра см. в разделах:  
  
-   [Replication Snapshot Agent](agents/replication-snapshot-agent.md)  
  
-   [Агент чтения журнала репликации](agents/replication-log-reader-agent.md)  
  
-   [Replication Distribution Agent](agents/replication-distribution-agent.md)  
  
-   [Агент слияния репликации](agents/replication-merge-agent.md)  
  
-   [Replication Queue Reader Agent](agents/replication-queue-reader-agent.md)  
  
 **Значение по умолчанию**  
 Значение по умолчанию для каждого параметра агента.  
  
 **Значение**  
 Значение, указанное для параметра в профиле, на котором основан новый профиль. Измените это поле, чтобы внести изменения в значения параметров.  
  
 **Показывать только параметры, используемые в этом профиле**  
 Снимите флажок, чтобы отобразить все корректные параметры для данного агента.  
  
## <a name="see-also"></a>См. также  
 [Работа с профилями агента репликации](agents/work-with-replication-agent-profiles.md)   
 [Обзор агентов репликации](agents/replication-agents-overview.md)   
 [Профили агента репликации](agents/replication-agent-profiles.md)  
  
  
