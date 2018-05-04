---
title: sysdbmaintplan_databases (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_databases
- sysdbmaintplan_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_databases system table
ms.assetid: f8413a44-8fcc-4899-84f2-b4afe0f8ec08
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4edf4ff45c4b610e04ffa5174a74252dc8df6cbf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdbmaintplandatabases-transact-sql"></a>sysdbmaintplan_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта таблица включена, чтобы сохранить существующие сведения по экземплярам, обновленным с предыдущей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии не изменяют содержимое этой таблицы. Эта таблица хранится в **msdb** базы данных.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|Идентификатор плана обслуживания.|  
|**database_name**|**sysname**|Имя базы данных, связанной с планом обслуживания базы данных.|  
  
  
