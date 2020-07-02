---
title: Сеансы dbo.sys(Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 12/30/2019
ms.prod: sql
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 91da4b73125c61f23d027bf99d2550a1d449a7a1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750259"
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

При каждом запуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается новый сеанс. С помощью сеансов агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет состояние заданий при непредвиденном перезапуске или остановке службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждая строка таблицы **таблице syssessions** содержит сведения об одном сеансе. Используйте таблицу **sysjobactivity** для просмотра состояния задания в конце каждого сеанса.  
  
 Эта таблица хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификатор сеанса агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот session_id не является идентификатором SPID для сеанса, а значением идентификатора в этой системной таблице.|  
|**agent_start_date**|**datetime**|Дата и время запуска службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для этого сеанса.|  
  
## <a name="remarks"></a>Примечания  
 Только пользователи, являющиеся членами предопределенной роли сервера **sysadmin** , могут получить доступ к этой таблице.  
  
## <a name="see-also"></a>См. также  
 [dbo.sysжобактивити &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
