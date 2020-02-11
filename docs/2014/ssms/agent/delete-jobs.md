---
title: Удаление заданий | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- delete jobs
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bf22e5cdac4d178fe41d3040afe7056f28375603
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62523335"
---
# <a name="delete-jobs"></a>удаление заданий
  Задание — это определенная последовательность действий, выполняемых агентом SQL Server. По умолчанию после завершения выполнения задания не удаляются. Можно удалить одно или несколько заданий агента [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , независимо от успешности завершения задания. В агенте [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также можно настроить автоматическое удаление заданий в случае их успешного выполнения, сбоя или завершения.  
  
 По умолчанию члены предопределенной роли сервера **sysadmin** могут выполнять [sp_delete_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql) системную хранимую процедуру для удаления задания. Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](sql-server-agent-fixed-database-roles.md).  
  
 Члены предопределенной роли сервера **sysadmin** с помощью процедуры **sp_delete_job** могут удалить любое задание. Пользователь, который не является членом предопределенной роли сервера **sysadmin** , может удалять только задания, принадлежащие этому пользователю.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|||  
|-|-|  
|**Описание**|**Раздел**|  
|Описывает, как удалить одно или несколько заданий агента [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Удаление одного или нескольких заданий](delete-one-or-more-jobs.md)|  
|Описывает, как настроить автоматическое удаление заданий агента [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в случае их успешного выполнения, сбоя или завершения.|[Автоматическое удаление задания](automatically-delete-a-job.md)|  
  
  
