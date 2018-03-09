---
title: "Командлет PowerShell для оценки миграции | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 117250d3-9982-47fe-94fd-6f29f6159940
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 63f5604c01bba64b75c51908840b8b9650ed03d2
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="powershell-cmdlet-for-migration-evaluation"></a>Командлет PowerShell для оценки миграции
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Командлет Save-SqlMigrationReport — это инструмент, который оценивает пригодность к миграции нескольких объектов в базе данных SQL Server. В настоящее время доступна оценка пригодности к миграции только для выполняющейся в памяти OLTP. Командлет можно запускать в среде Windows PowerShell с повышенными привилегиями и sqlps.  
  
## <a name="syntax"></a>Синтаксис  
  
```powershell  
Save-SqlMigrationReport [ -MigrationType OLTP ] [ -Server server -Database database [ -Object object_name ] ]  |  [ -InputObject smo_object ] -FolderPath path  
```  
  
#### <a name="parameters"></a>Параметры  
 В таблице ниже описаны параметры.  
  
|Параметры|Description|  
|----------------|-----------------|  
|MigrationType|Тип сценария миграции для командлета. В настоящее время единственным является значение по умолчанию — OLTP. Необязательный параметр.|  
|Сервер|Имя целевого экземпляра SQL Server. Обязателен в среде Windows PowerShell, если не указан параметр -InputObject. Необязателен в sqlps.|  
|база данных|Имя целевой базы данных SQL Server. Обязателен в среде Windows PowerShell, если не указан параметр -InputObject. Необязателен в sqlps.|  
|Object|Имя целевого объекта базы данных. Это может быть таблица или хранимая процедура.|  
|InputObject|Целевой объект SMO для командлета. Обязателен в среде Windows PowerShell, если не указаны параметры -Server и -Database. Необязателен в sqlps.|  
|FolderPath|Папка, в которую командлету следует поместить созданные отчеты. Обязательный.|  
  
## <a name="results"></a>Результаты  
 В папке, указанной в параметре - FolderPath, будет две папки: Tables и Stored Procedures. Если целевым объектом является таблица, отчет о ней будет расположен в папке Tables. В противном случае он будет находиться в папке Stored Procedures.  
  
  
