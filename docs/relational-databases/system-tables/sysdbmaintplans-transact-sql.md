---
title: "sysdbmaintplans (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdbmaintplans_TSQL
- sysdbmaintplans
dev_langs: TSQL
helpviewer_keywords: sysdbmaintplans system table
ms.assetid: 0363296a-3082-48a9-9eb5-a1020b2f541a
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8c9e9dd779b6a84f76844d27cef19ae8ff7c7f9d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdbmaintplans-transact-sql"></a>sysdbmaintplans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта таблица включена в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохранить существующие сведения по экземплярам, обновленным с предыдущей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не изменяет содержимое этой таблицы. Эта таблица хранится в **msdb** базы данных.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  

  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|Идентификатор плана обслуживания базы данных.|  
|**plan_name**|**sysname**|Имя плана обслуживания базы данных.|  
|**date_created**|**datetime**|Дата создания плана обслуживания базы данных.|  
|**Владелец**|**sysname**|Владелец плана обслуживания базы данных.|  
|**max_history_rows**|**int**|Максимальное число строк, выделенных для записи журнала плана обслуживания базы данных в системной таблице.|  
|**remote_history_server**|**sysname**|Имя удаленного сервера, на котором может быть сохранен отчет журнала.|  
|**max_remote_history_rows**|**int**|Максимальное количество строк, выделенных в системной таблице на удаленном сервере, в которые может быть записан отчет журнала.|  
|**user_defined_1**|**int**|Значение по умолчанию — NULL.|  
|**user_defined_2**|**nvarchar(100)**|Значение по умолчанию — NULL.|  
|**user_defined_3**|**datetime**|Значение по умолчанию — NULL.|  
|**user_defined_4**|**uniqueidentifier**|Значение по умолчанию — NULL.|  
|**log_shipping**|**bit**|Статус доставки журналов:<br /><br /> **0** = отключено **1** = включено|  
  
  
