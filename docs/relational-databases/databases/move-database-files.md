---
title: "Перемещение файлов баз данных | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disaster recovery [SQL Server], moving database files
- files [SQL Server], moving
- data files [SQL Server], moving
- file moving [SQL Server]
- moving full-text catalogs
- moving databases
- full-text catalogs [SQL Server], moving
- moving database files
- scheduled disk maintenance [SQL Server]
- moving files
- relocating database files
- planned database relocations [SQL Server]
- databases [SQL Server], moving
ms.assetid: 89f01b10-5fae-4ed8-b0fb-a4b9f540fd28
caps.latest.revision: "34"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 365f84c47734d1f55dff12d0f11119f1c3af9d65
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="move-database-files"></a>Перемещение файлов базы данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно перемещать системные и пользовательские базы данных, задав в предложении FILENAME инструкции [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) новое расположение файла. Таким образом могут быть перемещены файлы данных, журналов и полнотекстовых каталогов. Это может быть полезно в следующих ситуациях.  
  
-   Восстановление после сбоя. Например, база данных находится в подозрительном режиме, или ее работа была прекращена из-за сбоя оборудования.  
  
-   Плановое перемещение.  
  
-   Перемещение для запланированного обслуживания дисков.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Перемещение пользовательских баз данных](../../relational-databases/databases/move-user-databases.md)|Описывает процедуры перемещения файлов пользовательской базы данных и файлов полнотекстовых каталогов в другое местоположение.|  
|[Перемещение системных баз данных](../../relational-databases/databases/move-system-databases.md)|Описывает процедуры перемещения файлов системной базы данных в другое местоположение.|  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  
