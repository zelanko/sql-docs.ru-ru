---
description: Свойства &lt;AgentProfileName&gt;
title: Свойства &lt;AgentProfileName&gt; | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.profiles.perfprofileprops.f1
helpviewer_keywords:
- Agent Profile Properties dialog box
ms.assetid: 01a992d2-e4ff-417c-93f0-dc43ab2d1624
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: babf773a83101f73b0967ed3cdb94c93af5f6391
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475895"
---
# <a name="ltagentprofilenamegt-properties"></a>Свойства &lt;AgentProfileName&gt;
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
   Диалоговое окно **Свойства профиля агента** позволяет просматривать значения всех параметров агента, указанных в профиле, и изменять эти значения для пользовательских профилей.  
  
## <a name="options"></a>Параметры  
 **имя**;  
 Имя профиля.  
  
 **Описание**  
 Описание профиля.  
  
 **Параметр**  
 Параметры агента, включенные в профиль. Профили не должны задавать значения для каждого параметра. Для просмотра всех допустимых для данного агента параметров снимите флажок **Показывать только параметры, используемые в этом профиле** . Описание каждого параметра см. в разделах:  
  
-   [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
-   [Агент чтения журнала репликации](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
-   [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
-   [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md)  
  
-   [Replication Queue Reader Agent](../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
 **Значение по умолчанию**  
 Значение по умолчанию для каждого параметра агента.  
  
 **Значение**  
 Значение, заданное для данного параметра в профиле. Для пользовательских профилей это поле можно изменять.  
  
 **Показывать только параметры, используемые в этом профиле**  
 Снимите флажок, чтобы отобразить все корректные параметры для данного агента.  
  
## <a name="see-also"></a>См. также:  
 [Работа с профилями агента репликации](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Профили агента репликации](../../relational-databases/replication/agents/replication-agent-profiles.md)  
  
  
