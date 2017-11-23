---
title: "dbo.syscategories (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- dbo.syscategories_TSQL
- syscategories
- syscategories_TSQL
- dbo.syscategories
dev_langs: TSQL
helpviewer_keywords: syscategories system table
ms.assetid: eb2cb75c-dc58-4a5b-b329-664e9fe20ce0
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c61063d79e64cbd5350caad5eb374b12f028fa5c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbosyscategories-transact-sql"></a>dbo.syscategories (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит категории, используемые средой [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для организации заданий, предупреждений и операторов. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|Идентификатор категории|  
|**category_class**|**int**|Тип элемента в категории:<br /><br /> **1** = задание<br /><br /> **2** = предупреждение<br /><br /> **3** =-оператор|  
|**category_type**|**tinyint**|Тип категории:<br /><br /> **1** = локальная<br /><br /> **2** = Многосерверная<br /><br /> **3** = нет|  
|**name**|**sysname**|Имя категории|  
  
  
