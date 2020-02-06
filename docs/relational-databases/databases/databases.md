---
title: Базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2763a57a55a65d049be595d2286343eb5ba323ba
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68109710"
---
# <a name="databases"></a>Базы данных
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  База данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] состоит из коллекции таблиц, в которой хранится особый набор структурированных данных. Таблица содержит коллекцию строк, также называемых записями или кортежами, и столбцов, также называемых атрибутами. Каждый столбец в таблице предназначен для хранения конкретного типа данных, например дат, имен, денежных сумм или чисел.  
  
## <a name="basic-information-about-databases"></a>Основные сведения о базах данных  
 На компьютере можно установить один или несколько экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Каждый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может содержать одну или несколько баз данных.  В базе данных может содержаться одна или несколько групп объектов владения, которые называются схемами. В каждой схеме присутствуют объекты базы данных, такие как таблицы, представления и хранимые процедуры. Некоторые объекты, например сертификаты и асимметричные ключи, могут содержаться в базе данных, но при этом не находиться внутри схемы. Дополнительные сведения о создании таблиц см. в разделе [Tables](../../relational-databases/tables/tables.md).  
  
 Базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранятся в файловой системе в виде файлов. Файлы могут быть объединены в группы файлов. Дополнительные сведения о файлах и файловых группах см. в разделе [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md).  
  
 При получении доступа к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователи идентифицируются согласно имени входа. При получении доступа к базе данных пользователи идентифицируются как пользователи базы данных. Имя пользователя базы данных может быть основано на имени входа. Если автономные базы данных включены, то пользователь базы данных может быть создан не на основе имени входа. Дополнительные сведения о пользователях см. в статье [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md).  
  
 Пользователь, имеющий доступ к базе данных, может получить разрешения на доступ к объектам этой базы данных. Хотя разрешения и могут быть предоставлены отдельным пользователям, рекомендуется создавать роли базы данных, добавляя при этом пользователей базы данных к соответствующим ролям, а затем предоставлять разрешения ролям. Предоставление разрешений ролям, а не пользователям позволяет легко и понятно управлять процессом распределения разрешений, несмотря на постоянное изменение и рост числа пользователей. Дополнительные сведения о ролях и разрешениях см. в разделах [CREATE ROLE (Transact-SQL)](../../t-sql/statements/create-role-transact-sql.md) и [Субъекты (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md).  
  
## <a name="working-with-databases"></a>Работа с базами данных  
 Большинство пользователей, работающих с базами данных, используют средство [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Средство [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] предоставляет графический пользовательский интерфейс для создания баз данных и их объектов. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] также содержит редактор запросов, позволяющий взаимодействовать с базами данных при написании инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)]. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] можно установить с установочного диска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или загрузить с MSDN. Дополнительные сведения о [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] см. [здесь](../../ssms/sql-server-management-studio-ssms.md).
  
## <a name="in-this-section"></a>в этом разделе  
  
|||  
|-|-|  
|[Системные базы данных](../../relational-databases/databases/system-databases.md)|[Удаление файлов данных или журналов из базы данных](../../relational-databases/databases/delete-data-or-log-files-from-a-database.md)|  
|[Автономные базы данных](../../relational-databases/databases/contained-databases.md)|[Отображение сведений о месте на диске, занимаемом данными и журналами базы данных](../../relational-databases/databases/display-data-and-log-space-information-for-a-database.md)|  
|[Файлы данных SQL Server в Microsoft Azure](../../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md)|[Увеличение размера базы данных](../../relational-databases/databases/increase-the-size-of-a-database.md)|  
|[Файлы и файловые группы базы данных](../../relational-databases/databases/database-files-and-filegroups.md)|[Переименование базы данных](../../relational-databases/databases/rename-a-database.md)|  
|[Состояния базы данных](../../relational-databases/databases/database-states.md)|[Установка однопользовательского режима базы данных](../../relational-databases/databases/set-a-database-to-single-user-mode.md)|  
|[Состояния файлов](../../relational-databases/databases/file-states.md)|[Сжатие базы данных](../../relational-databases/databases/shrink-a-database.md)|  
|[Оценка размера базы данных](../../relational-databases/databases/estimate-the-size-of-a-database.md)|[Сжатие файла](../../relational-databases/databases/shrink-a-file.md)|  
|[Копирование баз данных на другие серверы](../../relational-databases/databases/copy-databases-to-other-servers.md)|[Просмотр или изменение свойств базы данных](../../relational-databases/databases/view-or-change-the-properties-of-a-database.md)|  
|[Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)|[Просмотр списка баз данных в экземпляре SQL Server](../../relational-databases/databases/view-a-list-of-databases-on-an-instance-of-sql-server.md)|  
|[Добавление файлов данных или журналов в базу данных](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)|[Просмотр или изменение уровня совместимости базы данных](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)|  
|[Изменение настроек конфигурации базы данных](../../relational-databases/databases/change-the-configuration-settings-for-a-database.md)|[Использование мастера планов обслуживания](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)|  
|[Создание базы данных](../../relational-databases/databases/create-a-database.md)|[Создание псевдонима для пользовательского типа данных](../../relational-databases/databases/create-a-user-defined-data-type-alias.md)|  
|[Удаление базы данных](../../relational-databases/databases/delete-a-database.md)|[Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md)|  
  
## <a name="related-content"></a>См. также  
 [Индексы](../../relational-databases/indexes/indexes.md)  
  
 [Представления](../../relational-databases/views/views.md)  
  
 [Хранимые процедуры (компонент Database Engine)](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)  
  
  
