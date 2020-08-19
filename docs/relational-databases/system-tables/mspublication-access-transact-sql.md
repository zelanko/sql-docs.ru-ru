---
description: MSpublication_access (Transact-SQL)
title: MSpublication_access (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpublication_access_TSQL
- MSpublication_access
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublication_access system table
ms.assetid: 7bebe47e-3153-4579-8092-5723667a24c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4f438a10c7840cbc9f2db2b4e5e4e50ee63197be
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423308"
---
# <a name="mspublication_access-transact-sql"></a>MSpublication_access (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSpublication_access** содержит по одной строке для каждого [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа, имеющего доступ к конкретной публикации или издателю. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**пользователей**|**sysname**|Учетные записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, существующие как на издателе, так и на распространителе.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
