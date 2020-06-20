---
title: Создание резервной копии на зеркальном наборе носителей (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 255a3c190139c029f5211dcab9780b6d07d975a4
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84959514"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>Создание резервной копии на зеркальном наборе носителей (Transact-SQL)
  В этом разделе описывается использование [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции [BACKUP](/sql/t-sql/statements/backup-transact-sql) для указания зеркального набора носителей при резервном копировании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных. Для определения зеркального набора носителей в инструкции BACKUP укажите первое зеркало в предложении TO. Затем определите каждое зеркало в своем собственном предложении TO. Предложения TO и MIRROR TO должны определять одинаковое количество и одинаковый тип устройств резервного копирования.  
  
## <a name="example"></a>Пример  
 В следующем примере создается зеркальный набор носителей, показанный на предыдущем рисунке, и производится резервное копирование базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на оба зеркала.  
  
```  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## <a name="related-tasks"></a>Связанные задачи  
 **Восстановление из зеркально отображенной резервной копии**  
  
-   [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)  
  
## <a name="see-also"></a>См. также:  
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [Зеркальные наборы носителей резервных копий (SQL Server)](mirrored-backup-media-sets-sql-server.md)  
  
  
