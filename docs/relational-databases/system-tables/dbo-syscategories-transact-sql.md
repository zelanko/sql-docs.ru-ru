---
description: dbo.syscategories (Transact-SQL)
title: Категории dbo.sys(Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.syscategories_TSQL
- syscategories
- syscategories_TSQL
- dbo.syscategories
dev_langs:
- TSQL
helpviewer_keywords:
- syscategories system table
ms.assetid: eb2cb75c-dc58-4a5b-b329-664e9fe20ce0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 84d72b2ec08573b7c7aa72903eab1bc828d6f774
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89525346"
---
# <a name="dbosyscategories-transact-sql"></a>dbo.syscategories (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Содержит категории, используемые средой [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для организации заданий, предупреждений и операторов. Эта таблица хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|Идентификатор категории|  
|**category_class**|**int**|Тип элемента в категории:<br /><br /> **1** = задание<br /><br /> **2** = оповещение<br /><br /> **3** = оператор|  
|**category_type**|**tinyint**|Тип категории:<br /><br /> **1** = локальный<br /><br /> **2** = многосерверная<br /><br /> **3** = нет|  
|**name**|**sysname**|Имя категории|  
  
  
