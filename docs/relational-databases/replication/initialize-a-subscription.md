---
description: Инициализация подписки
title: Инициализация подписки | Документация Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 562a0cf16f677c9306df82b9e2618a793752ed93
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423598"
---
# <a name="initialize-a-subscription"></a>Инициализация подписки
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Подписчики в топологии репликации должны инициализироваться, чтобы иметь по копии схемы каждой статьи в публикации, на которую они подписались, и все необходимые объекты репликации, например хранимые процедуры, триггеры и таблицы метаданных. Кроме того, подписчик, как правило, получает первоначальный набор данных. Метод инициализации, который используется по умолчанию, применяет полный моментальный снимок, включающий схему, объекты репликации и данные, но публикации могут также инициализироваться без полного моментального снимка.  
  
 Дополнительные сведения см. в разделах [Initialize a Subscription with a Snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) и [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
  
