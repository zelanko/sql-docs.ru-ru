---
title: Перемещение файлов баз данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f851fd637ef1781bb1446219e284109e96c306fa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193384"
---
# <a name="move-database-files"></a>Перемещение файлов базы данных
  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно перемещать системные и пользовательские базы данных, задав в предложении FILENAME инструкции [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) новое местоположение файла. Таким образом могут быть перемещены файлы данных, журналов и полнотекстовых каталогов. Это может быть полезно в следующих ситуациях.  
  
-   Восстановление после сбоя. Например, база данных находится в подозрительном режиме, или ее работа была прекращена из-за сбоя оборудования.  
  
-   Плановое перемещение.  
  
-   Перемещение для запланированного обслуживания дисков.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Перемещение пользовательских баз данных](move-user-databases.md)|Описывает процедуры перемещения файлов пользовательской базы данных и файлов полнотекстовых каталогов в другое местоположение.|  
|[Перемещение системных баз данных](system-databases.md)|Описывает процедуры перемещения файлов системной базы данных в другое местоположение.|  
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)   
 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Присоединение и отсоединение базы данных (SQL Server)](database-detach-and-attach-sql-server.md)  
  
  
