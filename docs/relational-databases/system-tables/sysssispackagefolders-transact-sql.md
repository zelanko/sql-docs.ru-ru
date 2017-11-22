---
title: "sysssispackagefolders (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdtspackagefolders90
- sysdtspackagefolders90_TSQL
dev_langs: TSQL
helpviewer_keywords: sysssispackagefolders system table
ms.assetid: ddc4833f-27bf-4610-b739-d257961d17ac
caps.latest.revision: "22"
author: spelluru
ms.author: spelluru
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ec206dc0111235044ff7ea742548463db556ea23
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysssispackagefolders-transact-sql"></a>sysssispackagefolders (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой папки в иерархии папок, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] использует. Эти папки перечислены в обозревателе объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] при подключении к службам [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В папке перечисляются пакеты, сохраненные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или в файловой системе.  
  
 **Parentfolderid** столбец описывает иерархию папок. Папка, в верхней части иерархии папок содержит значение null в **parentfolderid**.  
  
 **Foldername** столбец содержит имя папки, которые появляются в обозревателе объектов.  
  
 Эта таблица хранится в **msdb** базы данных.  

  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**FolderId**|**uniqueidentifier**|Идентификатор GUID папки.|  
|**parentfolderid**|**uniqueidentifier**|Идентификатор GUID родительской папки.|  
|**Имя папки**|**sysname**|Имя папки. Это имя появляется в иерархии папок в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
  
  
