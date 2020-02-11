---
title: sysdbmaintplan_jobs (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_jobs
- sysdbmaintplan_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_jobs system table
ms.assetid: bc65cd70-6ef2-4c17-be11-877ecf4efe50
author: stevestein
ms.author: sstein
ms.openlocfilehash: f780199361d9e5741187dd4e5346abb2df98b9cb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68130436"
---
# <a name="sysdbmaintplan_jobs-transact-sql"></a>sysdbmaintplan_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта таблица включена в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы сохранить существующие сведения по экземплярам, обновленным с предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не изменяет содержимое этой таблицы. Эта таблица хранится в базе данных **msdb** .  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  

  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**plan_id**|**UNIQUEIDENTIFIER**|Идентификатор плана обслуживания базы данных.|  
|**job_id**|**UNIQUEIDENTIFIER**|Идентификатор задания, связанного с планом обслуживания базы данных.|  
  
  
