---
title: dbo.systargetservergroupmembers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.systargetservergroupmembers_TSQL
- dbo.systargetservergroupmembers
- systargetservergroupmembers
- systargetservergroupmembers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systargetservergroupmembers system table
ms.assetid: ee1b2ebd-03cb-4b91-a5d2-98d4d38f82ec
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2585f8b21fad9d831acd2bc8b58f1d58a3592218
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38063652"
---
# <a name="dbosystargetservergroupmembers-transact-sql"></a>dbo.systargetservergroupmembers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Записывает, какие целевые серверы связаны в настоящее время с данной многосерверной группой.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**servergroup_id**|**int**|Идентификатор серверной группы|  
|**server_id**|**int**|Идентификатор сервера|  
  
  
