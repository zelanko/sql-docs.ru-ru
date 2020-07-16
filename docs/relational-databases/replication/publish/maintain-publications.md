---
title: Обслуживание публикаций | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- maintaining publications [SQL Server replication]
- publications [SQL Server replication], maintaining
- administering replication, publications
ms.assetid: d5bf7340-2b0b-4593-965c-de04ae628344
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 92e24c3ac193c3229cd61b098ff7c3287c7de998
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86159902"
---
# <a name="maintain-publications"></a>Обслуживание публикаций
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/applies-to-version/sql-asdbmi.md)]
  После создания публикации может возникнуть необходимость в добавлении или исключении статей либо в изменении свойств публикации или статьи. После создания публикации разрешается большинство изменений, но в некоторых случаях необходимо создать для публикации новый моментальный снимок и/или повторно инициализировать подписки на эту публикацию.
