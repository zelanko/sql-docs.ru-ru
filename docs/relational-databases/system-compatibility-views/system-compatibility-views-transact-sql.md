---
title: Представления совместимости системы (Transact-SQL) | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68018033"
---
# <a name="system-compatibility-views-transact-sql"></a>Системные представления совместимости (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Многие системные таблицы из предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в настоящее время реализованы в виде набора представлений. Эти представления известны как представления совместимости, и они предназначены только для обратной совместимости. Представления совместимости содержат метаданные, которые были доступны в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Однако представления совместимости не содержат метаданных, связанных с функциями, появившимися в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях. Поэтому при использовании этих возможностей, таких как компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] или секционирование, следует применять представления каталогов.  
  
 Еще одной причиной добавления обновлений в представления каталога является тот факт, что столбцы представлений совместимости, хранящие идентификаторы пользователей и типов, могут возвращать значение NULL или арифметические переполнения триггера. Это происходит потому, что можно создавать более 32 767 пользователей, групп и ролей, а также 32 767 типов данных. Например, если необходимо создать 32 768 пользователей, а затем выполнить следующий запрос: `SELECT * FROM sys.sysusers`. При значении ARITHABORT, равном ON, запрос завершается ошибкой арифметического переполнения. Если параметр ARITHABORT имеет значение OFF, столбец **UID** возвращает значение null.  
  
 Чтобы избежать таких проблем, рекомендуется использовать новые представления каталогов, которые могут содержать увеличившееся число идентификаторов пользователей и типов. В следующей таблице перечислены столбцы, которые могут подвергнуться переполнению.  
  
|Имя столбца|Представление совместимости|Представление SQL Server 2005|  
|-----------------|------------------------|--------------------------|  
|**xusertype**|**syscolumns**|**sys.columns**|  
|**usertype**|**syscolumns**|**sys.columns**|  
|**memberuid**|**sysmembers**|**sys.database_role_members**|  
|**groupuid**|**sysmembers**|**sys.database_role_members**|  
|**uid**|**sysobjects**|**sys.objects**|  
|**uid**|**sysprotects**|**sys.database_permissions**<br /><br /> **sys.server_permissions**|  
|**GRANTOR**|**sysprotects**|**sys.database_permissions**<br /><br /> **sys.server_permissions**|  
|**xusertype**|**systypes**|**sys.types**|  
|**uid**|**systypes**|**sys.types**|  
|**uid**|**sysusers**|**sys.database_principals**|  
|**altuid**|**sysusers**|**sys.database_principals**|  
|**операционной**|**sysusers**|**sys.database_principals**|  
|**uid**|**syscacheobjects**|**sys.dm_exec_plan_attributes**|  
|**uid**|**sysprocesses**|**sys.dm_exec_requests**|  
  
 При указании ссылки в пользовательской базе данных системные таблицы, объявленные как устаревшие в SQL Server 2000 (например, **syslanguages** или **syscacheobjects**), теперь привязаны к представлению с обратной совместимостью в схеме **sys** . С тех пор как системные таблицы SQL Server 2000 устарели для многих версий, данное изменение не считается критическим изменением.  
  
 Пример. Если пользователь создает пользовательскую таблицу с именем **syslanguages** в пользовательской базе данных, в SQL Server 2008 инструкция `SELECT * from dbo.syslanguages;` в этой базе данных будет возвращать значения из пользовательской таблицы. Начиная с SQL Server 2012, эта практика вернет данные из системного представления **sys. syslanguages**.  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Сопоставление системных таблиц с системными представлениями &#40;&#41;Transact-SQL](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
