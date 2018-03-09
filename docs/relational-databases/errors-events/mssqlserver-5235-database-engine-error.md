---
title: "MSSQLSERVER_5235 | Документация Майкрософт"
ms.custom: 
ms.date: 09/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 5235 (Database Engine error)
ms.assetid: 1aa7e6a5-7ccb-43c8-a1fd-d50e92e0a798
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8b786414c1fdd53d21148ff7b682f0b030362afe
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver5235"></a>MSSQLSERVER_5235
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|5235|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION|  
|Текст сообщения|Аварийное завершение инструкции [EMERGENCY] DBCC DBCC_COMMAND_DETAILS, выполненной пользователем USER_NAME, в результате ошибки с состоянием ERROR_STATE. Затраченное время: HOURS часы MINUTES минуты SECONDS секунды.|  
  
## <a name="explanation"></a>Объяснение  
Это сообщение сводки, которое DBCC распечатывает в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при аварийном завершении во время выполнения команды. Состояние ошибки в сообщении определяет тип аварийного завершения.  
  
В следующей ниже таблице приведены состояния ошибок и их определения.  
  
|Состояние ошибки|Определение|  
|---------------|--------------|  
|Состояние 1|Инструкция завершена из-за неустранимого повреждения метаданных. Это сообщение сопровождается одним или несколькими экземплярами ошибки 8930.|  
|Состояние 2|Инструкция завершена из-за сбоя выполнения внутренней проверки. Это сообщение сопровождается одним или несколькими экземплярами ошибки 8967.|  
|Состояние 3|Основной системной таблице не удалось выполнить проверку базовых системных таблиц подсистемы хранилища. Это сообщение сопровождается одним или несколькими экземплярами ошибок [7984](../../relational-databases/errors-events/mssqlserver-7984-database-engine-error.md), 7985, [7986](~/relational-databases/errors-events/mssqlserver-7986-database-engine-error.md), [7987](~/relational-databases/errors-events/mssqlserver-7987-database-engine-error.md) или [7988](~/relational-databases/errors-events/mssqlserver-7988-database-engine-error.md).|  
|Состояние 4|Произошел сбой при аварийном восстановлении DBCC, поскольку базу данных не удалось запустить после перестроения журнала транзакций. Это сообщение сопровождается ошибкой 7909.|  
|Состояние 5|Во время выполнения команды произошло нарушение предположения или нарушение доступа.|  
|Состояние 6|Возникла неизвестная ошибка, которая привела к непредвиденному завершению команды DBCC.|  
|Состояние 7|Аварийное завершение из-за ошибки в реплике (AlwaysOn).|  
  
## <a name="user-action"></a>Действие пользователя  
В следующей таблице приведены действия пользователя, соответствующие указанному состоянию ошибки.  
  
|Состояние ошибки|Действие пользователя|  
|---------------|---------------|  
|Состояние 1|Выполните восстановление из резервной копии.|  
|Состояние 2|Обратитесь в службу поддержки пользователей [!INCLUDE[msCoName](../../includes/msconame-md.md)] (CSS).|  
|Состояние 3|Выполните восстановление из резервной копии.|  
|Состояние 4|Выполните восстановление из резервной копии.|  
|Состояние 4|Обратитесь в службу поддержки пользователей.|  
|Состояние 6|Запустите команду еще раз: если устранить неполадку не удается, обратитесь в службу поддержки пользователей.|  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](~/t-sql/database-console-commands/dbcc-transact-sql.md)  
  
