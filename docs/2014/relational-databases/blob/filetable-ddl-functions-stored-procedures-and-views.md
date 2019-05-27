---
title: Инструкции DDL, функции, хранимые процедуры и представления для | Документация Майкрософт | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], database objects
ms.assetid: 7e2e0f7f-94a8-4178-8bc7-d2e14ac8528c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 85e0c761f5dc784698b3aed361ce50488a93e366
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66010103"
---
# <a name="filetable-ddl-functions-stored-procedures-and-views"></a>Инструкции FileTable языка DDL, функции, хранимые процедуры и представления
  Приводятся инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и объекты базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые добавлены или изменены для поддержки компонента FileTable в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 В следующих таблицах столбец «Состояние» показывает, является он новым в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]или присутствовал в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , но изменен в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] для поддержки семантического поиска.  
  
 Список инструкций и объектов базы данных, которые поддерживают FILESTREAM, см. в разделе [FILESTREAM DDL, Functions, Stored Procedures, and Views](../views/views.md).  
  
##  <a name="ddl"></a> Инструкции языка описания данных (DDL) Transact-SQL  
  
|Object|Состояние|Дополнительные сведения|  
|------------|------------|----------------------|  
|[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)<br /><br /> [Параметры ALTER DATABASE SET (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options)|Изменено|[Включение необходимых компонентов для таблицы FileTable](enable-the-prerequisites-for-filetable.md)<br /><br /> [Управление таблицами FileTable](manage-filetables.md)|  
|[ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)|Изменено|[Создание, изменение и удаление таблиц FileTables](create-alter-and-drop-filetables.md)<br /><br /> [Управление таблицами FileTable](manage-filetables.md)|  
|[CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)|Изменено|[Включение необходимых компонентов для таблицы FileTable](enable-the-prerequisites-for-filetable.md)|  
|[CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql)|Изменено|[Создание, изменение и удаление таблиц FileTable](create-alter-and-drop-filetables.md)|  
|[RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)<br /><br /> [Аргументы инструкции RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql)|Изменено||  
  
##  <a name="func"></a> Функции  
  
|Object|Состояние|Дополнительные сведения|  
|------------|------------|----------------------|  
|[FileTableRootPath (Transact-SQL)](/sql/relational-databases/system-functions/filetablerootpath-transact-sql)|**Добавлено**|[Работа с каталогами и путями в таблицах FileTable](work-with-directories-and-paths-in-filetables.md)|  
|[GetFileNamespacePath (Transact-SQL)](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)|**Добавлено**|[Работа с каталогами и путями в таблицах FileTable](work-with-directories-and-paths-in-filetables.md)|  
|[GetPathLocator (Transact-SQL)](/sql/relational-databases/system-functions/getpathlocator-transact-sql)|**Добавлено**|[Работа с каталогами и путями в таблицах FileTable](work-with-directories-and-paths-in-filetables.md)|  
  
##  <a name="sproc"></a> Хранимые процедуры  
  
|Object|Состояние|Дополнительные сведения|  
|------------|------------|----------------------|  
|[sp_kill_filestream_non_transacted_handles (Transact-SQL)](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles)|**Добавлено**|[Управление таблицами FileTable](manage-filetables.md)|  
  
##  <a name="cv"></a> Представления каталога  
  
|Object|Состояние|Дополнительные сведения|  
|------------|------------|----------------------|  
|[sys.database_filestream_options (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)|**Добавлено**|[Включение необходимых компонентов для таблицы FileTable](enable-the-prerequisites-for-filetable.md)|  
|[sys.filetable_system_defined_objects (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql)|**Добавлено**|[Создание, изменение и удаление таблиц FileTables](create-alter-and-drop-filetables.md)<br /><br /> [Управление таблицами FileTable](manage-filetables.md)|  
|[sys.filetables (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-filetables-transact-sql)|**Добавлено**|[Управление таблицами FileTable](manage-filetables.md)|  
|[sys.tables (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)|Изменено|[Управление таблицами FileTable](manage-filetables.md)|  
  
##  <a name="dmv"></a> Динамические административные представления  
  
|Object|Состояние|Дополнительные сведения|  
|------------|------------|----------------------|  
|[sys.dm_filestream_non_transacted_handles (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql)|**Добавлено**|[Управление таблицами FileTable](manage-filetables.md)|  
  
## <a name="see-also"></a>См. также  
 [Управление таблицами FileTable](manage-filetables.md)  
  
  
