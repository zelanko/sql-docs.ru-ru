---
title: Функции FileTable, хранимые процедуры и представления | Документация Майкрософт
descriptions: Learn which Transact-SQL statements and which SQL Server functions, stored procedures, and views have been added or changed to support the FileTable feature.
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], database objects
ms.assetid: 7e2e0f7f-94a8-4178-8bc7-d2e14ac8528c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 548bb412a8fc5d7a3ccae46ea42575b8a8dcaf46
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85744316"
---
# <a name="filetable-ddl-functions-stored-procedures-and-views"></a>Инструкции FileTable языка DDL, функции, хранимые процедуры и представления

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Приводятся инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и объекты базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые добавлены или изменены для поддержки компонента FileTable в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 В следующих таблицах столбец «Состояние» показывает, является он новым в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]или присутствовал в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , но изменен в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] для поддержки семантического поиска.  
  
 Список инструкций и объектов базы данных, которые поддерживают FILESTREAM, см. в разделе [FILESTREAM DDL, Functions, Stored Procedures, and Views](../../relational-databases/blob/filestream-ddl-functions-stored-procedures-and-views.md).  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> Инструкции языка описания данных (DDL) Transact-SQL  
  
|Объект|Состояние|Дополнительные сведения|  
|------------|------------|----------------------|  
|[ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)<br /><br /> [Параметры ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)|Изменено|[Включение необходимых компонентов для таблицы FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)<br /><br /> [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)|  
|[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)|Изменено|[Создание, изменение и удаление таблиц FileTable](../../relational-databases/blob/create-alter-and-drop-filetables.md)<br /><br /> [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)|  
|[CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)|Изменено|[Включение необходимых компонентов для таблицы FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)|  
|[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)|Изменено|[Создание, изменение и удаление таблиц FileTable](../../relational-databases/blob/create-alter-and-drop-filetables.md)|  
|[RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)<br /><br /> [Аргументы инструкции RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-arguments-transact-sql.md)|Изменено||  
  
##  <a name="functions"></a><a name="func"></a> Функции  
  
|Объект|Состояние|Дополнительные сведения|  
|------------|------------|----------------------|  
|[FileTableRootPath (Transact-SQL)](../../relational-databases/system-functions/filetablerootpath-transact-sql.md)|**Добавлено**|[Работа с каталогами и путями в таблицах FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)|  
|[GetFileNamespacePath (Transact-SQL)](../../relational-databases/system-functions/getfilenamespacepath-transact-sql.md)|**Добавлено**|[Работа с каталогами и путями в таблицах FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)|  
|[GetPathLocator (Transact-SQL)](../../relational-databases/system-functions/getpathlocator-transact-sql.md)|**Добавлено**|[Работа с каталогами и путями в таблицах FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)|  
  
##  <a name="stored-procedures"></a><a name="sproc"></a> Хранимые процедуры  
  
|Объект|Состояние|Дополнительные сведения|  
|------------|------------|----------------------|  
|[sp_kill_filestream_non_transacted_handles (Transact-SQL)](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)|**Добавлено**|[Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)|  
  
##  <a name="catalog-views"></a><a name="cv"></a> Представления каталога  
  
|Объект|Состояние|Дополнительные сведения|  
|------------|------------|----------------------|  
|[sys.database_filestream_options (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md)|**Добавлено**|[Включение необходимых компонентов для таблицы FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)|  
|[sys.filetable_system_defined_objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql.md)|**Добавлено**|[Создание, изменение и удаление таблиц FileTable](../../relational-databases/blob/create-alter-and-drop-filetables.md)<br /><br /> [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)|  
|[sys.filetables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filetables-transact-sql.md)|**Добавлено**|[Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)|  
|[sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)|Изменено|[Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)|  
  
##  <a name="dynamic-management-views"></a><a name="dmv"></a> Динамические административные представления  
  
|Объект|Состояние|Дополнительные сведения|  
|------------|------------|----------------------|  
|[sys.dm_filestream_non_transacted_handles (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md)|**Добавлено**|[Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)|  
  
## <a name="see-also"></a>См. также:  
 [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)  
  
  
