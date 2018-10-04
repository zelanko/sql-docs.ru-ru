---
title: Инициализация подписки | Документация Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b2a10e2cfcaf476a50c0c75696d8c0b6ada0481f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228824"
---
# <a name="initialize-a-subscription"></a>Инициализация подписки
  Подписчики в топологии репликации должны инициализироваться, чтобы иметь по копии схемы каждой статьи в публикации, на которую они подписались, и все необходимые объекты репликации, например хранимые процедуры, триггеры и таблицы метаданных. Кроме того, подписчик, как правило, получает первоначальный набор данных. Метод инициализации, который используется по умолчанию, применяет полный моментальный снимок, включающий схему, объекты репликации и данные, но публикации могут также инициализироваться без полного моментального снимка.  
  
 Дополнительные сведения см. в разделах [Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) и [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).  
  
  
