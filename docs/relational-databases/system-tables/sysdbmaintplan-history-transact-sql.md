---
description: sysdbmaintplan_history (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 473e98da465aa9952261ae3c57d77ab9b5d2629e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89517819"
---
# <a name="sysdbmaintplan_history-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Эта таблица хранится в базе данных **msdb** .  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|Последовательность журнала, содержащая операции планов обслуживания базы данных.|  
|**plan_id**|**uniqueidentifier**|Идентификатор плана обслуживания базы данных.|  
|**plan_name**|**sysname**|Имя плана обслуживания базы данных.|  
|**database_name**|**sysname**|Имя базы данных, связанной с планом обслуживания базы данных.|  
|**server_name**|**sysname**|Имя системы.|  
|**activity**|**nvarchar(128)**|Операции, выполненные планом обслуживания базы данных (например, «Резервное копирование журнала транзакций» и т. д.).|  
|**succeeded**|**bit**|**0** = успех **1** = сбой|  
|**end_time**|**datetime**|Время завершения операции.|  
|**duration**|**int**|Период времени, требуемый для завершения операции плана обслуживания базы данных.|  
|**start_time**|**datetime**|Время начала операции.|  
|**error_number**|**int**|Номер ошибки при сбое.|  
|**message**|**nvarchar(512)**|Сообщение, созданное с помощью **sqlmaint**.|  
  
  
