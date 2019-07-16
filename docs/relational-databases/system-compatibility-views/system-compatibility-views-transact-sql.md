---
title: Системные представления совместимости (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- compatibility views [SQL Server]
- system tables [SQL Server], compatibility views
- type IDs [SQL Server]
- system views [SQL Server], compatibility
- metadata [SQL Server], views
- backward compatibility [SQL Server], compatibility views
- compatibility [SQL Server], compatibility views
- backward compatibility [SQL Server], system tables
- compatibility [SQL Server], system tables
- user IDs [SQL Server]
ms.assetid: 8e4624f5-9d36-4ce7-9c9e-1fe010fa2122
author: rothja
ms.author: jroth
ms.openlocfilehash: 466dc68da1c5cef56a7debe3953ba38956bb2993
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68018033"
---
# <a name="system-compatibility-views-transact-sql"></a>Системные представления совместимости (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Многие системные таблицы из предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в настоящее время реализованы в виде набора представлений. Эти представления известны как представления совместимости, и они предназначены только для обратной совместимости. Представления совместимости содержат метаданные, которые были доступны в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Однако представления совместимости не содержат метаданных, связанных с функциями, появившимися в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях. Поэтому при использовании этих возможностей, таких как компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] или секционирование, следует применять представления каталогов.  
  
 Еще одной причиной добавления обновлений в представления каталога является тот факт, что столбцы представлений совместимости, хранящие идентификаторы пользователей и типов, могут возвращать значение NULL или арифметические переполнения триггера. Это происходит потому, что можно создавать более 32 767 пользователей, групп и ролей, а также 32 767 типов данных. Например, если нужно создать 32 768 пользователей, а затем запустите следующий запрос: `SELECT * FROM sys.sysusers`. При значении ARITHABORT, равном ON, запрос завершается ошибкой арифметического переполнения. Если значение параметра ARITHABORT равно OFF, **uid** столбец возвращает значение NULL.  
  
 Чтобы избежать таких проблем, рекомендуется использовать новые представления каталогов, которые могут содержать увеличившееся число идентификаторов пользователей и типов. В следующей таблице перечислены столбцы, которые могут подвергнуться переполнению.  
  
|Имя столбца|Представление совместимости|Представление SQL Server 2005|  
|-----------------|------------------------|--------------------------|  
|**xusertype**|**syscolumns**|**sys.columns**|  
|**usertype**|**syscolumns**|**sys.columns**|  
|**memberuid**|**sysmembers**|**sys.database_role_members**|  
|**groupuid**|**sysmembers**|**sys.database_role_members**|  
|**UID**|**sysobjects**|**sys.objects**|  
|**UID**|**sysprotects**|**sys.database_permissions**<br /><br /> **sys.server_permissions**|  
|**Объект, предоставляющий разрешение**|**sysprotects**|**sys.database_permissions**<br /><br /> **sys.server_permissions**|  
|**xusertype**|**systypes**|**sys.types**|  
|**UID**|**systypes**|**sys.types**|  
|**UID**|**sysusers**|**sys.database_principals**|  
|**altuid**|**sysusers**|**sys.database_principals**|  
|**gid**|**sysusers**|**sys.database_principals**|  
|**UID**|**syscacheobjects**|**sys.dm_exec_plan_attributes**|  
|**UID**|**sysprocesses**|**sys.dm_exec_requests**|  
  
 При обращении к базе данных пользователя, системные таблицы, которые были объявлены как устаревшие в SQL Server 2000 (такие как **syslanguages** или **syscacheobjects**), теперь привязан к представлению обратной совместимости в **sys** схемы. С тех пор как системные таблицы SQL Server 2000 устарели для многих версий, данное изменение не считается критическим изменением.  
  
 Пример Если пользователь создает таблицу пользователя с именем **syslanguages** пользователя-базы данных в SQL Server 2008, инструкция `SELECT * from dbo.syslanguages;` в этой базе данных вернет значения из пользовательской таблицы. Начиная с SQL Server 2012, этот метод будет возвращать данные из системного представления **sys.syslanguages**.  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
