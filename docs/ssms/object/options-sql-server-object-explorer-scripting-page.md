---
description: Параметры (обозреватель объектов SQL Server — страница "Скрипты")
title: Параметры (обозреватель объектов SQL Server — страница "Скрипты")
ms.custom: seo-lt-2019
ms.date: 08/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.ObjectExplorerScripting
- VS.ToolsOptionsPages.Sql_Server_Object_Explorer.ObjectExplorerScripting
ms.assetid: 6105aec9-1b72-4cb2-bd24-fc35f6d95240
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 35a255bb4df3779897ec40da29da9cc15f62ba1f
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037633"
---
# <a name="options-sql-server-object-explorer---scripting-page"></a>Параметры (обозреватель объектов SQL Server — страница "Скрипты")
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
 Эта страница используется для задания параметров скриптов, применяемых к следующим командам контекстных меню объектов в **обозревателе объектов**:  
  
-   Команды **Правка** для пользовательских таблиц и представлений.  
  
-   Команды **Сформировать скрипт <object> как** для объектов, созданных пользователем.  
  
-   Команда **Изменить** для объектов, созданных пользователем.  
  
-   На этой странице также задаются параметры скриптов по умолчанию для **мастера формирования скриптов SQL Server**.  
  
## <a name="remarks"></a>Remarks  
Результаты выполнения команд **Правка** и **Изменить** могут отличаться от результатов команды **Сформировать скрипт <object> как** при том же значении параметра. Команды **Правка** и **Изменить** предназначены для изменения объектов в текущей базе данных во время сеанса работы редактора запросов. Команда **Сформировать скрипт <object> как** предназначена для формирования скрипта, который можно использовать позже для создания объектов.  
  
## <a name="options"></a>Параметры  
Укажите параметры создания скриптов, выбрав нужные настройки из числа доступных в окне списка, расположенном справа от каждого параметра.

> [!NOTE]
> Указанные параметры по умолчанию применяются только к варианту **Внести в скрипт всю базу данных и все объекты базы данных** и могут отличаться при использовании варианта **Выбрать отдельные объекты базы данных**.
  
### <a name="general-scripting-options"></a>Общие параметры скрипта  
**Разделить отдельные инструкции**  
Разделяет отдельные инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью пакетного разделителя. Чтобы изменить пакетный разделитель по умолчанию для **редактора запросов**, выберите **Сервис**/**Параметры**/**Выполнение запроса**/**SQL Server**/**Общие**/**Разделитель пакетов**. Значение по умолчанию — False. Дополнительные сведения см. в разделе [GO (Transact-SQL)](../../t-sql/language-elements/sql-server-utilities-statements-go.md).  
  
**Включить описательные заголовки**  
Добавляет к скрипту описательные комментарии, разделяя его на разделы для каждого объекта. Значение по умолчанию — True. Дополнительные сведения см. в разделе [/ *...* / (Comment) (Transact-SQL)](../../t-sql/language-elements/slash-star-comment-transact-sql.md).  
  
**Включить сжатие vardecimal**  
Включает параметры хранения vardecimal. Значение по умолчанию — False. Дополнительные сведения см. в разделе [sp_db_vardecimal_storage_format (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md).  
  
**Создать скрипт для отслеживания изменений**  
Включает в скрипт сведения об отслеживании изменений.  
  
**Внести в скрипт полнотекстовые каталоги**  
Включает скрипт для полнотекстовых каталогов. Значение по умолчанию — False. Дополнительные сведения см. в разделе [CREATE FULLTEXT CATALOG (Transact-SQL)](../../t-sql/statements/create-fulltext-catalog-transact-sql.md).  
  
**Внести в скрипт инструкцию USE <database>**  
Добавляет в скрипт инструкцию USE DATABASE для создания объектов базы данных в контексте текущей базы данных в **обозревателе объектов** . Если предполагается выполнение скрипта в другой базе данных, присвойте этому параметру значение False, чтобы не включать инструкцию USE DATABASE. Значение по умолчанию — True. Дополнительные сведения см. в разделе [USE (Transact-SQL)](../../t-sql/language-elements/use-transact-sql.md).  
  
### <a name="object-scripting-options"></a>Параметры скрипта объекта  

**Проверьте наличие объекта**. Убедитесь в том, что объект с заданным именем существует, перед его изменением или удалением. Перед созданием объекта убедитесь в том, что объект с заданным именем отсутствует. Дополнительные сведения см. в разделах [IF...ELSE (Transact-SQL)](../../t-sql/language-elements/if-else-transact-sql.md) и [EXISTS (Transact-SQL)](../../t-sql/language-elements/exists-transact-sql.md).

**Сформировать скрипт для зависимых объектов**  
Формирует скрипт для дополнительных объектов, необходимых при выполнении скрипта для выбранного объекта. Значение по умолчанию — False.  
  
**Имена объектов квалификаторов схемы**  
Квалифицирует имена объектов по схеме объектов. Значение по умолчанию — False. Дополнительные сведения см. в разделе [Создание схемы базы данных](../../relational-databases/security/authentication-access/create-a-database-schema.md).  

**Создать скрипт с параметрами сжатия данных**. Включает в скрипт параметры сжатия данных. Значение по умолчанию — False.

**Внести в скрипт расширенные свойства**  
Включает в скрипт расширенные свойства, если они имеются у объекта. Значение по умолчанию — False. Дополнительные сведения см. в разделе [sp_addextendedproperty (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md).  
  
**Владелец скрипта**  
Включает владельца в созданный скрипт. Значение по умолчанию — False.  
  
**Внести в скрипт разрешения**  
Включает в скрипт разрешения для объектов базы данных. Значение по умолчанию — True. Дополнительные сведения см. в разделе [Разрешения](../../relational-databases/security/permissions-database-engine.md).  
  
### <a name="tableview-options"></a>Параметры таблицы или представления  
Следующие параметры применяются только к скриптам таблиц и представлений.  
  
**Преобразовать определяемые пользователем типы данных в базовые типы**  
Преобразует определяемые пользователем типы данных в базовые типы, из которых они были созданы. Используйте значение True, если в базе данных, в которой будет выполняться скрипт, отсутствуют определяемые пользователем типы данных базы данных-источника. Используйте значение False для сохранения определяемых пользователем типов данных. Значение по умолчанию — False. Дополнительные сведения см. в разделе [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md).  
  
**Создать команды SET ANSI PADDING**  
Добавляет инструкцию SET ANSI_PADDING до и после каждой инструкции CREATE TABLE. Значение по умолчанию — True. Дополнительные сведения см. в разделе [SET ANSI_PADDING (Transact-SQL)](../../t-sql/statements/set-ansi-padding-transact-sql.md).  
  
**Включить сортировку**  
Включить параметры сортировки в определение столбца. Значение по умолчанию — True. Дополнительные сведения см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
**Включить свойство IDENTITY**  
Включает определения для начального значения свойства IDENTITY и шага приращения значения свойства IDENTITY. Значение по умолчанию — True. Дополнительные сведения см. в разделе [IDENTITY (Property) (Transact-SQL)](../../t-sql/statements/create-table-transact-sql-identity-property.md).  
  
**Ссылки на внешние ключи квалификаторов схемы**  
Добавляет имя схемы к ссылкам на таблицы для ограничений FOREIGN KEY. Значение по умолчанию — True.  
  
**Внести в скрипт связанные значения по умолчанию и правила**  
Включает вызовы хранимых процедур привязки **sp_bindefault** и **sp_bindrule** . Значение по умолчанию — True. Дополнительные сведения см. в разделах [sp_bindefault (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md) и [sp_bindrule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md).  
  
**Внести в скрипт ограничения CHECK**  
Добавляет в скрипт [ограничения CHECK](../../relational-databases/tables/unique-constraints-and-check-constraints.md) . Значение по умолчанию — True.  
  
**Внести в скрипт значения по умолчанию**  
Включает в скрипт значения по умолчанию для столбца. Значение по умолчанию — False. Дополнительные сведения см. в статье [CREATE DEFAULT (Transact-SQL)](../../t-sql/statements/create-default-transact-sql.md).  
  
**Внести в скрипт файловые группы**  
Указывает файловую группу в предложении ON для определений таблиц. Значение по умолчанию — False. Дополнительные сведения см. в статье [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).  
  
**Внести в скрипт внешние ключи**  
Включает в скрипт [ограничения FOREIGN KEY](../../relational-databases/tables/primary-and-foreign-key-constraints.md) . Значение по умолчанию — False.  
  
**Внести в скрипт полнотекстовые индексы**  
Включает в скрипт полнотекстовые индексы. Значение по умолчанию — False. Дополнительные сведения см. в статье [CREATE FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
**Внести в скрипт индексы**  
Включает в скрипт кластеризованные, некластеризованные индексы и XML-индексы. Значение по умолчанию — True. Дополнительные сведения см. в статье [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md).  
  
**Внести в скрипт схемы секционирования**  
Включить в скрипт схемы секционирования таблиц. Значение по умолчанию — False. Дополнительные сведения см. в статье [CREATE PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/create-partition-scheme-transact-sql.md).  
  
**Внести в скрипт первичные ключи**  
Включает в скрипт [ограничения первичных и внешних ключей](../../relational-databases/tables/primary-and-foreign-key-constraints.md) . Значение по умолчанию — True.  
  
**Внести в скрипт команды сбора статистики**  
Включает в скрипт определяемые пользователем команды сбора статистики. Значение по умолчанию — False. Дополнительные сведения см. в разделе [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md).  
  
**Внести в скрипт триггеры**  
Включает в скрипт триггеры. Значение по умолчанию — False. Дополнительные сведения см. в разделе [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md).  
  
**Внести в скрипт уникальные ключи**  
Включает в скрипт [ограничения уникальности и ограничения проверки](../../relational-databases/tables/unique-constraints-and-check-constraints.md) . Значение по умолчанию — False.  
  
**Внести в скрипт столбцы просмотра**  
Объявляет столбцы представления в заголовках представлений. Значение по умолчанию — False. Дополнительные сведения см. в статье [CREATE VIEW (Transact-SQL)](../../t-sql/statements/create-view-transact-sql.md).  
  
**Включить системные имена DRI**  
Включает созданные системой имена ограничений для обеспечения декларативной ссылочной целостности. Значение по умолчанию — False. Дополнительные сведения см. в статье [REFERENTIAL_CONSTRAINTS (Transact-SQL)](../../relational-databases/system-information-schema-views/referential-constraints-transact-sql.md).  
  
### <a name="version-options"></a>Параметры версии

**Использовать параметры сценариев согласно источнику**. Если этот параметр включен, целевая версия, выпуск ядра и тип ядра для создаваемых скриптов аналогичны тем, что используются на сервере, где находится объект скрипта. При этом другие параметры версий отключаются (и игнорируются). 

**Скрипт для выпуска ядра СУБД**. Создаваемые скрипты будут предназначены для указанного [выпуска ядра](/dotnet/api/microsoft.sqlserver.management.smo.edition).

**Скрипт для типа ядра СУБД**. Создаваемые скрипты будут предназначены для указанного [типа ядра СУБД](/previous-versions/sql/sql-server-2014/ee642509(v=sql.120)).

**Скрипт для версии сервера**  
Создаваемые скрипты будут предназначены для указанной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Новые функции [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] нельзя внести в скрипты для более ранних версий. Некоторые скрипты, созданные для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , нельзя выполнять на серверах, где выполняется более ранняя версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или в базе данных с более ранним значением [уровня совместимости баз данных](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  

## <a name="see-also"></a>См. также раздел  
[Формирование скриптов (среда SQL Server Management Studio)](../scripting/generate-scripts-sql-server-management-studio.md)  
