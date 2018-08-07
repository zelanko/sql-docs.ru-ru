---
title: Командлет PowerShell для оценки миграции | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 117250d3-9982-47fe-94fd-6f29f6159940
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: beeef1c3bb5b27c8505d683985100ff0683b1a8e
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39538934"
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
  
|Параметры|Описание|  
|----------------|-----------------|  
|MigrationType|Тип сценария миграции для командлета. В настоящее время единственным является значение по умолчанию — OLTP. Необязательный параметр.|  
|Сервер|Имя целевого экземпляра SQL Server. Обязателен в среде Windows PowerShell, если не указан параметр -InputObject. Необязателен в sqlps.|  
|База данных|Имя целевой базы данных SQL Server. Обязателен в среде Windows PowerShell, если не указан параметр -InputObject. Необязателен в sqlps.|  
|Объект|Имя целевого объекта базы данных. Это может быть таблица или хранимая процедура.|  
|InputObject|Целевой объект SMO для командлета. Обязателен в среде Windows PowerShell, если не указаны параметры -Server и -Database. Необязателен в sqlps.|  
|FolderPath|Папка, в которую командлету следует поместить созданные отчеты. Обязательный.|  
  
## <a name="results"></a>Результаты  
 В папке, указанной в параметре - FolderPath, будет две папки: Tables и Stored Procedures. Если целевым объектом является таблица, отчет о ней будет расположен в папке Tables. В противном случае он будет находиться в папке Stored Procedures.  
  
  
