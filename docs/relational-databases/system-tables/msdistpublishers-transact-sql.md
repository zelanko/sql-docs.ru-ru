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
ms.openlocfilehash: 2c19f2d8e75a3c9744318d65683b29d1d84857ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907423"
---
# <a name="msdistpublishers-transact-sql"></a>MSdistpublishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Таблица **MSdistpublishers** содержит по одной строке для каждого удаленного издателя, поддерживаемого локальным распространителем. Эта таблица хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**имеет sysname**|Имя распространителя издателя.|  
|**distribution_db**|**имеет sysname**|Имя базы данных распространителя.|  
|**working_directory**|**nvarchar(255)**|Имя рабочего каталога, используемого для хранения файлов данных и схем для публикации.|  
|**security_mode**|**int**|Режим безопасности, реализованный на распространителе:<br /><br /> **** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности.<br /><br /> **1** = проверка подлинности Windows.|  
|**пользователей**|**имеет sysname**|Идентификатор входа для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**пароль**|**nvarchar (524)**|Пароль (зашифрованный) для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Active**|**bit**|Показывает, используется ли локальный распространитель удаленным издателем.|  
|**trusted**|**bit**|Показывает, использует ли удаленный издатель такой же пароль, что и локальный распространитель:<br /><br /> **0** = для подключения к распространителю на удаленном издателе требуется пароль.<br /><br /> **1** = пароль не требуется.|  
|**third_party**|**bit**|Является ли издатель установкой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> **Установка равна 0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . **1** = разнородный источник данных.|  
|**publisher_type**|**имеет sysname**|Тип издателя:<br /><br /> **Издатель MSSQLSERVER**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> **Oracle** = стандартный издатель Oracle.<br /><br /> **Oracle Gateway** = издатель шлюза Oracle.|  
|**storage_connection_string**|**nvarchar (779)**|Значение строки подключения к хранилищу базы данных SQL Azure.|  

  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
