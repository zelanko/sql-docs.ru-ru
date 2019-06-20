---
title: dbo.syssessions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.syssessions_TSQL
- dbo.syssessions
- syssessions_TSQL
- syssessions
dev_langs:
- TSQL
helpviewer_keywords:
- syssessions system table
ms.assetid: 187819b6-c7f4-4a26-b74c-0a89e96695cf
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2ad2ccc2505c3bb72b8d2efc02afbc5ef5aebaf0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470563"
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  При каждом запуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается новый сеанс. С помощью сеансов агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет состояние заданий при непредвиденном перезапуске или остановке службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждая строка **syssessions** таблица содержит сведения об одном сеансе. Используйте **sysjobactivity** таблицу, чтобы просмотреть состояние задания в конце каждого сеанса.  
  
 Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификатор сеанса агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**agent_start_date**|**datetime**|Дата и время запуска службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для этого сеанса.|  
  
## <a name="remarks"></a>Примечания  
 Только пользователи, являющиеся членами из **sysadmin** предопределенной роли сервера можно получить доступ к этой таблице.  
  
## <a name="see-also"></a>См. также  
 [dbo.sysjobactivity &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
