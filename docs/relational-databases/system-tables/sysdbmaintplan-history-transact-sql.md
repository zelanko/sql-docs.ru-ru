---
title: sysdbmaintplan_history (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_history_TSQL
- sysdbmaintplan_history
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_history system table
ms.assetid: 02d36f08-ac93-4463-bb59-284c5cd6ed04
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4470b6b5d1b30f5698bf588a04066c50bb4c7197
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68130454"
---
# <a name="sysdbmaintplan_history-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта таблица хранится в базе данных **msdb** .  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|Последовательность журнала, содержащая операции планов обслуживания базы данных.|  
|**plan_id**|**UNIQUEIDENTIFIER**|Идентификатор плана обслуживания базы данных.|  
|**plan_name**|**имеет sysname**|Имя плана обслуживания базы данных.|  
|**database_name**|**имеет sysname**|Имя базы данных, связанной с планом обслуживания базы данных.|  
|**server_name**|**имеет sysname**|Имя системы.|  
|**оборот**|**nvarchar(128**|Операции, выполненные планом обслуживания базы данных (например, «Резервное копирование журнала транзакций» и т. д.).|  
|**успешно**|**bit**|**0** = успех **1** = сбой|  
|**end_time**|**datetime**|Время завершения операции.|  
|**длитель**|**int**|Период времени, требуемый для завершения операции плана обслуживания базы данных.|  
|**start_time**|**datetime**|Время начала операции.|  
|**error_number**|**int**|Номер ошибки при сбое.|  
|**Сообщение**|**nvarchar(512)**|Сообщение, созданное с помощью **sqlmaint**.|  
  
  
