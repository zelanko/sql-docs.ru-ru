---
title: Базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- data warehouse [SQL Server]
- OLTP databases [SQL Server]
- databases [SQL Server], about databases
ms.assetid: 316eea58-81b8-4bf3-a1fc-801946740e94
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea3da64ce6da8cbcb32b5854f14e8d24349c0c25
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970087"
---
# <a name="databases"></a>Базы данных
  База данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] состоит из коллекции таблиц, в которой хранится особый набор структурированных данных. Таблица содержит коллекцию строк, также называемых записями или кортежами, и столбцов, также называемых атрибутами. Каждый столбец в таблице предназначен для хранения конкретного типа данных, например дат, имен, денежных сумм или чисел.  
  
## <a name="basic-information-about-databases"></a>Основные сведения о базах данных  
 На компьютере можно установить один или несколько экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Каждый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может содержать одну или несколько баз данных.  В базе данных может содержаться одна или несколько групп объектов владения, которые называются схемами. В каждой схеме присутствуют объекты базы данных, такие как таблицы, представления и хранимые процедуры. Некоторые объекты, например сертификаты и асимметричные ключи, могут содержаться в базе данных, но при этом не находиться внутри схемы. Дополнительные сведения о создании таблиц см. в разделе [Tables](../tables/tables.md).  
  
 Базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранятся в файловой системе в виде файлов. Файлы могут быть объединены в группы файлов. Дополнительные сведения о файлах и файловых группах см. в разделе [Database Files and Filegroups](database-files-and-filegroups.md).  
  
 При получении доступа к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователи идентифицируются согласно имени входа. При получении доступа к базе данных пользователи идентифицируются как пользователи базы данных. Имя пользователя базы данных может быть основано на имени входа. Если автономные базы данных включены, то пользователь базы данных может быть создан не на основе имени входа. Дополнительные сведения о пользователях см. в статье [CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql).  
  
 Пользователь, имеющий доступ к базе данных, может получить разрешения на доступ к объектам этой базы данных. Хотя разрешения и могут быть предоставлены отдельным пользователям, рекомендуется создавать роли базы данных, добавляя при этом пользователей базы данных к соответствующим ролям, а затем предоставлять разрешения ролям. Предоставление разрешений ролям, а не пользователям позволяет легко и понятно управлять процессом распределения разрешений, несмотря на постоянное изменение и рост числа пользователей. Дополнительные сведения о ролях и разрешениях см. в разделах [CREATE ROLE (Transact-SQL)](/sql/t-sql/statements/create-role-transact-sql) и [Субъекты (ядро СУБД)](../security/authentication-access/principals-database-engine.md).  
  
## <a name="working-with-databases"></a>Работа с базами данных  
 Большинство пользователей, работающих с базами данных, используют средство [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Средство [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] предоставляет графический пользовательский интерфейс для создания баз данных и их объектов. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] также содержит редактор запросов, позволяющий взаимодействовать с базами данных при написании инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)]. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] можно установить с установочного диска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или загрузить с MSDN.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|||  
|-|-|  
|[Системные базы данных](system-databases.md)|[Удаление файлов данных или журнала из базы данных](delete-data-or-log-files-from-a-database.md)|  
|[Автономные базы данных](contained-databases.md)|[Отображение данных и сведений о пространстве журнала для базы данных](display-data-and-log-space-information-for-a-database.md)|  
|[Файлы данных SQL Server в Azure](sql-server-data-files-in-microsoft-azure.md)|[Увеличение размера базы данных](increase-the-size-of-a-database.md)|  
|[Файлы и файловые группы базы данных](database-files-and-filegroups.md)|[Переименование базы данных](rename-a-database.md)|  
|[Состояния базы данных](database-states.md)|[Установка однопользовательского режима базы данных](set-a-database-to-single-user-mode.md)|  
|[Состояния файлов](file-states.md)|[Сжатие базы данных](shrink-a-database.md)|  
|[Оценка размера базы данных](estimate-the-size-of-a-database.md)|[Сжатие файла](shrink-a-file.md)|  
|[Копирование баз данных на другие серверы](copy-databases-to-other-servers.md)|[Просмотр или изменение свойств базы данных](view-or-change-the-properties-of-a-database.md)|  
|[Присоединение и отсоединение базы данных (SQL Server)](database-detach-and-attach-sql-server.md)|[Просмотр списка баз данных в экземпляре SQL Server](view-a-list-of-databases-on-an-instance-of-sql-server.md)|  
|[Добавление файлов данных или журналов в базу данных](add-data-or-log-files-to-a-database.md)|[Просмотр или изменение уровня совместимости базы данных](view-or-change-the-compatibility-level-of-a-database.md)|  
|[Изменение настроек конфигурации базы данных](change-the-configuration-settings-for-a-database.md)|[Использование мастера планов обслуживания](../maintenance-plans/use-the-maintenance-plan-wizard.md)|  
|[Создание базы данных](create-a-database.md)|[Создание псевдонима определяемого пользователем типа данных](create-a-user-defined-data-type-alias.md)|  
|[Удаление базы данных](delete-a-database.md)|[Моментальные снимки базы данных (SQL Server)](database-snapshots-sql-server.md)|  
  
## <a name="related-content"></a>См. также  
 [Индексы](../indexes/indexes.md)  
  
 [Представления](../views/views.md)  
  
 [Хранимые процедуры (компонент Database Engine)](../stored-procedures/stored-procedures-database-engine.md)  
  
  
