---
title: sp_dbmmonitoraddmonitoring (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitoraddmonitoring
- sp_dbmmonitoraddmonitoring_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], monitoring
- sp_dbmmonitoraddmonitoring
ms.assetid: 9489dc30-af29-4363-a172-4645947fc95e
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 089c8f089eac7256cff1b084cbee5fe669bbd3ff
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spdbmmonitoraddmonitoring-transact-sql"></a>sp_dbmmonitoraddmonitoring (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает задание монитора зеркального отображения баз данных, которое периодически обновляет состояние каждой из баз данных на экземпляре сервера, подвергнутых зеркальному отображению.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbmmonitoraddmonitoring [ update_period ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *update_period*  
 Указывает интервал между обновлениями в минутах. Это значение должно быть в диапазоне от 1 до 120 минут. Значение по умолчанию — 1 минута.  
  
> [!NOTE]  
>  Если установлен слишком короткий интервал, время ответа клиентам может возрасти.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Для этой процедуры требуется разрешение на выполнение агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на экземпляре сервера, а для выполнения задания монитора зеркального отображения баз данных требуется, чтобы агент был запущен.  
  
 Если зеркальное отображение базы данных запускается из [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **sp_dbmmonitoraddmonitoring** процедура выполняется автоматически. При запуске зеркального отображения вручную с помощью инструкции ALTER DATABASE, чтобы отслеживать зеркальную базу данных на экземпляре сервера, необходимо запустить **sp_dbmmonitoraddmonitoring** вручную.  
  
> [!NOTE]  
>  При запуске **sp_dbmmonitoraddmonitoring** перед настройкой зеркального отображения базы данных, задание монитора будет выполняться, но без обновления таблицы состояния в базу данных, которая будет храниться журнал монитора зеркального отображения.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере запускается слежение с интервалом обновления `3` минуты.  
  
```  
EXEC sp_dbmmonitoraddmonitoring 3;  
```  
  
## <a name="see-also"></a>См. также  
 [Мониторинг зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
