---
title: MSdistpublishers (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdistpublishers
- MSdistpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistpublishers system table
ms.assetid: 31844099-4b33-4dc9-84b4-bac70aa82598
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dc2adcd101a2f974b441cef792668dcd61c25d4c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="msdistpublishers-transact-sql"></a>MSdistpublishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  **MSdistpublishers** содержит по одной строке для каждого удаленного издателя, поддерживаемого локальным распространителем. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя распространителя издателя.|  
|**distribution_db**|**sysname**|Имя базы данных распространителя.|  
|**working_directory**|**nvarchar(255)**|Имя рабочего каталога, используемого для хранения файлов данных и схем для публикации.|  
|**security_mode**|**int**|Режим безопасности, реализованный на распространителе:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности.<br /><br /> **1** = проверка подлинности Windows.|  
|**Имя входа**|**sysname**|Идентификатор входа для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar(524)**|Пароль (зашифрованный) для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Активный**|**бит**|Показывает, используется ли локальный распространитель удаленным издателем.|  
|**доверенные**|**бит**|Показывает, использует ли удаленный издатель такой же пароль, что и локальный распространитель:<br /><br /> **0** = A удаленного издателя для соединения с распространителем необходим пароль.<br /><br /> **1** = нет необходимости вводить пароль.|  
|**third_party**|**бит**|Является ли издатель установкой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установки. **1** = разнородный источник данных.|  
|**publisher_type**|**sysname**|Тип издателя:<br /><br /> **MSSQLSERVER**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.<br /><br /> **ORACLE** = стандартный издатель Oracle.<br /><br /> **ORACLE GATEWAY** = издатель Oracle Gateway.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
