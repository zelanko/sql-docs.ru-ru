---
title: "CREATE FULLTEXT CATALOG (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CATALOG_TSQL
- CREATE_FULLTEXT_TSQL
- FULLTEXT_TSQL
- FULLTEXT CATALOG
- CREATE FULLTEXT CATALOG
- CREATE_FULLTEXT_CATALOG_TSQL
- CATALOG
- FULLTEXT_CATALOG_TSQL
- CREATE FULLTEXT
- FULLTEXT
dev_langs: TSQL
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- CREATE FULLTEXT CATALOG statement
ms.assetid: d7a8bd93-e2d7-4a40-82ef-39069e65523b
caps.latest.revision: "60"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 65872ec24d605e61bf284446c976c51b053e999c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="create-fulltext-catalog-transact-sql"></a>CREATE FULLTEXT CATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает полнотекстовый каталог в базе данных. Один полнотекстовый каталог может содержать несколько полнотекстовых индексов, но любой полнотекстовый индекс может быть частью только одного полнотекстового каталога. Каждая база данных может содержать ноль или более полнотекстовых каталогов.  
  
 Не удается создать полнотекстовые каталоги в **master**, **модель**, или **tempdb** баз данных.  
  
> [!IMPORTANT]  
>  Начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], полнотекстовый каталог является виртуальным объектом и не входит в файловую группу. Полнотекстовый каталог — это логическое понятие, обозначающее группу полнотекстовых индексов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE FULLTEXT CATALOG catalog_name  
     [ON FILEGROUP filegroup ]  
     [IN PATH 'rootpath']  
     [WITH <catalog_option>]  
     [AS DEFAULT]  
     [AUTHORIZATION owner_name ]  
  
<catalog_option>::=  
     ACCENT_SENSITIVITY = {ON|OFF}  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_каталога*  
 Имя нового каталога. Имя каталога должно быть уникальным среди других имен каталогов в текущей базе данных. Также имя файла, который соответствует полнотекстовому каталогу (см. ON FILEGROUP), должно быть уникальным среди всех файлов базы данных. Если имя каталога уже используется для другого каталога в базе данных, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает ошибку.  
  
 Длина имени каталога не может превышать 120 символов.  
  
 ON FILEGROUP *filegroup*  
 Начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], это предложение не оказывает влияние на работу системы.  
  
 В пути **"***rootpath***"**  
 > [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], это предложение не оказывает влияние на работу системы.  
  
 ACCENT_SENSITIVITY = {ON|OFF}  
 Указывает, будет ли каталог учитывать диакритические знаки для полнотекстового индексирования. Если это свойство меняется, индекс перестраивается. По умолчанию в параметрах сортировки базы данных установлено учитывать диакритические знаки. Чтобы отобразить параметры сортировки базы данных, используйте **sys.databases** представления каталога.  
  
 Чтобы определить текущую настройку свойства учета диакритических знаков полнотекстового каталога, используйте функцию FULLTEXTCATALOGPROPERTY со **accentsensitivity** значение свойства от *имя_каталога*. Если возвращенное значение равно 1, полнотекстовый каталог учитывает диакритические знаки; если значение равно 0, каталог не учитывает диакритические знаки.  
  
 AS DEFAULT  
 Указывает, что каталог является каталогом по умолчанию. При создании полнотекстовых индексов без явного указания полнотекстового каталога используется каталог по умолчанию. Если существующий полнотекстовый каталог уже помечен как AS DEFAULT, установка этого нового каталога AS DEFAULT сделает этот каталог полнотекстовым каталогом по умолчанию.  
  
 АВТОРИЗАЦИЯ *owner_name*  
 Устанавливает владельцем полнотекстового каталога пользователя или роль базы данных. Если *owner_name* — это роль, роль должна быть именем роли, текущий пользователь является членом или пользователь, выполняющий инструкцию необходимо быть владельцем базы данных или системному администратору.  
  
 Если *owner_name* — имя пользователя, имя пользователя должно быть одним из следующих:  
  
-   имя пользователя, выполняющего инструкцию;  
  
-   имя пользователя, для которого пользователь, выполняющий инструкцию, имеет разрешение на IMPERSONATE;  
  
-   или пользователь, выполняющий команду, должен быть владельцем базы данных или системным администратором.  
  
 *owner_name* также необходимо предоставить разрешение TAKE OWNERSHIP на указанный полнотекстовый каталог.  
  
## <a name="remarks"></a>Замечания  
 Идентификаторы полнотекстовых каталогов начинаются с 00005 и увеличиваются на единицу для каждого вновь создаваемого каталога.  
  
## <a name="permissions"></a>Permissions  
 Пользователь должен иметь разрешение CREATE FULLTEXT CATALOG в базе данных или быть членом **db_owner**, или **db_ddladmin** предопределенных ролей базы данных.  
  
## <a name="examples"></a>Примеры  
 Следующий пример создает полнотекстовый каталог, а также полнотекстовый индекс.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE FULLTEXT CATALOG ftCatalog AS DEFAULT;  
GO  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate(Resume) KEY INDEX PK_JobCandidate_JobCandidateID;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.fulltext_catalogs &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [ALTER FULLTEXT CATALOG (Transact-SQL)](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [DROP FULLTEXT CATALOG &#40; Transact-SQL &#41;](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)   
 [Полнотекстовый поиск](../../relational-databases/search/full-text-search.md)   
 
  
  
