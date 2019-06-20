---
title: MSdistpublishers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistpublishers
- MSdistpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistpublishers system table
ms.assetid: 31844099-4b33-4dc9-84b4-bac70aa82598
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b867e4ffe4b23ee1a7195bb3c201ae05c2b6d075
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62817070"
---
# <a name="msdistpublishers-transact-sql"></a>MSdistpublishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  **MSdistpublishers** таблица содержит по одной строке для каждого удаленного издателя, поддерживаемого локальным распространителем. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя распространителя издателя.|  
|**distribution_db**|**sysname**|Имя базы данных распространителя.|  
|**working_directory**|**nvarchar(255)**|Имя рабочего каталога, используемого для хранения файлов данных и схем для публикации.|  
|**security_mode**|**int**|Режим безопасности, реализованный на распространителе:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности.<br /><br /> **1** = проверка подлинности Windows.|  
|**Имя входа**|**sysname**|Идентификатор входа для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar(524)**|Пароль (зашифрованный) для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Active**|**bit**|Показывает, используется ли локальный распространитель удаленным издателем.|  
|**доверенные**|**bit**|Показывает, использует ли удаленный издатель такой же пароль, что и локальный распространитель:<br /><br /> **0** = A удаленного издателя для соединения с распространителем необходим пароль.<br /><br /> **1** = нет необходимости вводить пароль.|  
|**third_party**|**bit**|Является ли издатель установкой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установки.** 1** = разнородный источник данных.|  
|**publisher_type**|**sysname**|Тип издателя:<br /><br /> **MSSQLSERVER**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.<br /><br /> **ORACLE** = стандартный издатель Oracle.<br /><br /> **ORACLE GATEWAY** = издатель Oracle Gateway.|  
|**storage_connection_string**|**nvarchar(779)**|Значение строки подключения хранилища базы данных SQL Azure.|  

  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
