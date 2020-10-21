---
description: Перемещение файлов базы данных
title: Перемещение файлов баз данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
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
ms.openlocfilehash: fa8fe0e721bbe571cf1f47d95bfdd79029059846
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92194316"
---
# <a name="move-database-files"></a>Перемещение файлов базы данных
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно перемещать системные и пользовательские базы данных, задав в предложении FILENAME инструкции [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) новое расположение файла. Таким образом могут быть перемещены файлы данных, журналов и полнотекстовых каталогов. Это может быть полезно в следующих ситуациях.  
  
-   Восстановление после сбоя. Например, база данных находится в подозрительном режиме, или ее работа была прекращена из-за сбоя оборудования.  
  
-   Плановое перемещение.  
  
-   Перемещение для запланированного обслуживания дисков.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Перемещение пользовательских баз данных](../../relational-databases/databases/move-user-databases.md)|Описывает процедуры перемещения файлов пользовательской базы данных и файлов полнотекстовых каталогов в другое местоположение.|  
|[Перемещение системных баз данных](../../relational-databases/databases/move-system-databases.md)|Описывает процедуры перемещения файлов системной базы данных в другое местоположение.|  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-transact-sql.md)   
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
