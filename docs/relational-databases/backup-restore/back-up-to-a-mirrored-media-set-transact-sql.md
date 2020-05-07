---
title: Создание резервной копии на зеркальном наборе носителей (Transact-SQL) | Документация Майкрософт
description: В этой статье описано, как использовать инструкцию Transact-SQL BACKUP, чтобы указать зеркальный набор носителей при резервном копировании базы данных SQL Server.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dc903b8d999c370304b177fa195ab9aa116498da
ms.sourcegitcommit: 9afb612c5303d24b514cb8dba941d05c88f0ca90
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2020
ms.locfileid: "82220589"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>Создание резервной копии на зеркальном наборе носителей (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этой статье описано, как использовать инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](../../t-sql/statements/backup-transact-sql.md), чтобы указать зеркальный набор носителей при резервном копировании базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для определения зеркального набора носителей в инструкции BACKUP укажите первое зеркало в предложении TO. Затем определите каждое зеркало в своем собственном предложении TO. Предложения TO и MIRROR TO должны определять одинаковое количество и одинаковый тип устройств резервного копирования.  
  
## <a name="example"></a>Пример  
 В следующем примере создается зеркальный набор носителей, показанный на предыдущем рисунке, и производится резервное копирование базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на оба зеркала.  
  
```sql  
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
  
-   [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [Зеркальные наборы носителей резервных копий (SQL Server)](../../relational-databases/backup-restore/mirrored-backup-media-sets-sql-server.md)  
  
  
