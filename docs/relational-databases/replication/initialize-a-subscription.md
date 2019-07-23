---
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a1fed3d0aca0a80fb0ecc267337693a1936e3d29
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68127902"
---
# <a name="initialize-a-subscription"></a>Инициализация подписки
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Подписчики в топологии репликации должны инициализироваться, чтобы иметь по копии схемы каждой статьи в публикации, на которую они подписались, и все необходимые объекты репликации, например хранимые процедуры, триггеры и таблицы метаданных. Кроме того, подписчик, как правило, получает первоначальный набор данных. Метод инициализации, который используется по умолчанию, применяет полный моментальный снимок, включающий схему, объекты репликации и данные, но публикации могут также инициализироваться без полного моментального снимка.  
  
 Дополнительные сведения см. в разделах [Initialize a Subscription with a Snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) и [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
  
