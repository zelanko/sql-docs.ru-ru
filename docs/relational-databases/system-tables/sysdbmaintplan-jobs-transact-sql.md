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
manager: craigg
ms.openlocfilehash: 0e54355cf0c7806c70f6bb80ee0463744b4c869b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47794954"
---
# <a name="sysdbmaintplanjobs-transact-sql"></a>sysdbmaintplan_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта таблица включена в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы сохранить существующие сведения по экземплярам, обновленным с предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не изменяет содержимое этой таблицы. Эта таблица хранится в **msdb** базы данных.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|Идентификатор плана обслуживания базы данных.|  
|**job_id**|**uniqueidentifier**|Идентификатор задания, связанного с планом обслуживания базы данных.|  
  
  
