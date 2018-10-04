---
title: Перезапуск прерванной операции восстановления (язык Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- interrupted restore operation
- restoring databases [SQL Server], restarting interrupted operation
- resetting options changed after backup
- database restores [SQL Server], restarting interrupted operation
- restarting interrupted restore operation
- restoring interrupted operation [SQL Server]
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 22f5b597f7482c5a417633322f13776578e595e2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48143474"
---
# <a name="restart-an-interrupted-restore-operation-transact-sql"></a>Перезапуск прерванной операции восстановления (язык Transact-SQL)
  В этом разделе объясняется, как перезапустить прерванную операцию восстановления.  
  
### <a name="to-restart-an-interrupted-restore-operation"></a>Перезапуск прерванной операции восстановления  
  
1.  Инициируйте прерванную операцию RESTORE еще раз, указав следующую информацию.  
  
    -   Те же предложения, которые были использованы в первоначальной инструкции RESTORE.  
  
    -   Предложение RESTART.  
  
## <a name="example"></a>Пример  
 Следующий программный код перезапускает прерванную операцию восстановления:  
  
```tsql  
-- Restore a full database backup of the AdventureWorks database.  
RESTORE DATABASE AdventureWorks  
   FROM DISK = 'C:\AdventureWorks.bck'  
GO  
-- The restore operation halted prematurely.  
-- Repeat the original RESTORE statement specifying WITH RESTART.  
RESTORE DATABASE AdventureWorks   
   FROM DISK = 'C:\AdventureWorks.bck'  
   WITH RESTART  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Выполнение полного восстановления базы данных (модель полного восстановления)](complete-database-restores-full-recovery-model.md)   
 [Выполнение полного восстановления базы данных (простая модель восстановления)](complete-database-restores-simple-recovery-model.md)   
 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
