---
title: sysssispackagefolders (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtspackagefolders90
- sysdtspackagefolders90_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackagefolders system table
ms.assetid: ddc4833f-27bf-4610-b739-d257961d17ac
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 7c1a5e117ee1c79b918f9785310b9b7c97671729
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56025825"
---
# <a name="sysssispackagefolders-transact-sql"></a>sysssispackagefolders (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой папки в иерархии папок, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] использует. Эти папки перечислены в обозревателе объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] при подключении к службам [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В папке перечисляются пакеты, сохраненные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или в файловой системе.  
  
 **Parentfolderid** столбец описывает иерархию папок. Папка в верхней части иерархии папок содержит значение null в **parentfolderid**.  
  
 **Foldername** столбец содержит имя папки, которые появляются в обозревателе объектов.  
  
 Эта таблица хранится в **msdb** базы данных.  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**FolderId**|**uniqueidentifier**|Идентификатор GUID папки.|  
|**parentfolderid**|**uniqueidentifier**|Идентификатор GUID родительской папки.|  
|**Имя папки**|**sysname**|Имя папки. Это имя появляется в иерархии папок в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
  
  
