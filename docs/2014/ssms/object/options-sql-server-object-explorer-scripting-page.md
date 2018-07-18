---
title: Параметры (SQL Server объекта страницы обозревателя сценариев) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.ObjectExplorerScripting
- VS.ToolsOptionsPages.Sql_Server_Object_Explorer.ObjectExplorerScripting
ms.assetid: 6105aec9-1b72-4cb2-bd24-fc35f6d95240
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 094fd9d740501fafee8c75eff162a132c01e08ae
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37170225"
---
# <a name="options-sql-server-object-explorer-scripting-page"></a>Параметры (SQL Server объекта скрипта в обозревателе страница)
  Эта страница используется для задания параметров скриптов, применяемых к следующим командам контекстных меню объектов в **обозревателе объектов**:  
  
-   Команды **Правка** для пользовательских таблиц и представлений.  
  
-   **Сценарий \<объекта > как** команд для объектов, созданных пользователем.  
  
-   Команда **Изменить** для объектов, созданных пользователем.  
  
-   На этой странице также задаются параметры скриптов по умолчанию для **мастера формирования скриптов SQL Server**.  
  
## <a name="remarks"></a>Примечания  
 **Изменить** и **изменить** команд может дать результаты, отличные от **сценарий \<объекта > как** команду в том же значении параметра. Команды **Правка** и **Изменить** предназначены для изменения объектов в текущей базе данных во время сеанса работы редактора запросов. **Сценарий \<объекта > как** команда предназначена для создания скрипта, чтобы его можно использовать позже для создания объектов.  
  
## <a name="options"></a>Параметры  
 Укажите параметры создания скриптов, выбрав нужные настройки из числа доступных в окне списка, расположенном справа от каждого параметра.  
  
### <a name="general-scripting-options"></a>Общие параметры скрипта  
 **Разделить отдельные инструкции**  
 Разделяет отдельные инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью пакетного разделителя. Чтобы изменить пакетный разделитель по умолчанию для **редактора запросов**, выберите **Сервис**/**Параметры**/**Выполнение запроса**/**SQL Server**/**Общие**/**Разделитель пакетов**. Значение по умолчанию — False. Дополнительные сведения см. в разделе [GO &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/sql-server-utilities-statements-go).  
  
 **Включить описательные заголовки**  
 Добавляет к скрипту описательные комментарии, разделяя его на разделы для каждого объекта. Значение по умолчанию — True. Дополнительные сведения см. в разделе [комментарий &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/comment-transact-sql).  
  
 **Включить параметры vardecimal**  
 Включает параметры хранения vardecimal. Значение по умолчанию — False. Дополнительные сведения см. в разделе и [sp_db_vardecimal_storage_format &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql).  
  
 **Создать скрипт для отслеживания изменений**  
 Включает в скрипт сведения об отслеживании изменений.  
  
 **Скрипт для версии сервера**  
 Создает скрипт, который можно выполнять на выбранной версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Новые функции [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] нельзя внести в скрипты для более ранних версий. Некоторые скрипты, созданные для [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , нельзя выполнять на серверах, где выполняется более ранняя версия [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], или в базе данных с более ранним значением [уровня совместимости баз данных](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  
 **Внести в скрипт полнотекстовые каталоги**  
 Включает скрипт для полнотекстовых каталогов. Значение по умолчанию — False. Дополнительные сведения см. в разделе [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql).  
  
 **Сценарий использования \<базы данных >**  
 Добавляет в скрипт инструкцию USE DATABASE для создания объектов базы данных в контексте текущей базы данных в **обозревателе объектов** . Если предполагается выполнение скрипта в другой базе данных, присвойте этому параметру значение False, чтобы не включать инструкцию USE DATABASE. Значение по умолчанию — True. Дополнительные сведения см. в статье [USE (Transact-SQL)](/sql/t-sql/language-elements/use-transact-sql).  
  
### <a name="object-scripting-options"></a>Параметры скрипта объекта  
 **Сформировать скрипт для зависимых объектов**  
 Формирует скрипт для дополнительных объектов, необходимых при выполнении скрипта для выбранного объекта. Значение по умолчанию — False.  
  
 **Включить предложение IF NOT EXISTS**  
 Включает инструкцию для проверки отсутствия каждого объекта в базе данных перед попыткой создания этого объекта. Значение по умолчанию — False. Дополнительные сведения см. в разделе [IF... ELSE &#40;Transact-SQL&#41; ](/sql/t-sql/language-elements/if-else-transact-sql) и [EXISTS &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/exists-transact-sql).  
  
 **Имена объектов квалификаторов схемы**  
 Квалифицирует имена объектов по схеме объектов. Значение по умолчанию — False. Дополнительные сведения см. в разделе [Создание схемы базы данных](../../relational-databases/security/authentication-access/create-a-database-schema.md).  
  
 **Внести в скрипт расширенные свойства**  
 Включает в скрипт расширенные свойства, если они имеются у объекта. Значение по умолчанию — False. Дополнительные сведения см. в разделе [sp_addextendedproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql).  
  
 **Владелец скрипта**  
 Включает владельца в созданный скрипт. Значение по умолчанию — False.  
  
 **Внести в скрипт разрешения**  
 Включает в скрипт разрешения для объектов базы данных. Значение по умолчанию — True. Дополнительные сведения см. в разделе [разрешения &#40;СУБД&#41;](../../relational-databases/security/permissions-database-engine.md).  
  
### <a name="tableview-options"></a>Параметры таблицы или представления  
 Следующие параметры применяются только к скриптам таблиц и представлений.  
  
 **Преобразовать определяемые пользователем типы данных в базовые типы**  
 Преобразует определяемые пользователем типы данных в базовые типы, из которых они были созданы. Используйте значение True, если в базе данных, в которой будет выполняться скрипт, отсутствуют определяемые пользователем типы данных базы данных-источника. Используйте значение False для сохранения определяемых пользователем типов данных. Значение по умолчанию — False. Дополнительные сведения см. в разделе [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).  
  
 **Создать команды SET ANSI PADDING**  
 Добавляет инструкцию SET ANSI_PADDING до и после каждой инструкции CREATE TABLE. Значение по умолчанию — True. Дополнительные сведения см. в разделе [SET ANSI_PADDING (Transact-SQL)](/sql/t-sql/statements/set-ansi-padding-transact-sql).  
  
 **Включить сортировку**  
 Включить параметры сортировки в определение столбца. Значение по умолчанию — True. Дополнительные сведения см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
 **Включить свойство IDENTITY**  
 Включает определения для начального значения свойства IDENTITY и шага приращения значения свойства IDENTITY. Значение по умолчанию — True. Дополнительные сведения см. в статье о [свойстве IDENTITY (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql-identity-property).  
  
 **Ссылки на внешние ключи квалификаторов схемы**  
 Добавляет имя схемы к ссылкам на таблицы для ограничений FOREIGN KEY. Значение по умолчанию — True.  
  
 **Внести в скрипт связанные значения по умолчанию и правила**  
 Включает вызовы хранимых процедур привязки **sp_bindefault** и **sp_bindrule** . Значение по умолчанию — True. Дополнительные сведения см. в разделе [sp_bindefault &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-bindefault-transact-sql) и [sp_bindrule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindrule-transact-sql).  
  
 **Внести в скрипт ограничения CHECK**  
 Добавляет в скрипт [ограничения CHECK](../../relational-databases/tables/unique-constraints-and-check-constraints.md) . Значение по умолчанию — True.  
  
 **Внести в скрипт значения по умолчанию**  
 Включает в скрипт значения по умолчанию для столбца. Значение по умолчанию — False. Дополнительные сведения см. в статье [CREATE DEFAULT (Transact-SQL)](/sql/t-sql/statements/create-default-transact-sql).  
  
 **Внести в скрипт файловые группы**  
 Указывает файловую группу в предложении ON для определений таблиц. Значение по умолчанию — False. Дополнительные сведения см. в разделе [CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql).  
  
 **Внести в скрипт внешние ключи**  
 Включает в скрипт [ограничения FOREIGN KEY](../../relational-databases/tables/primary-and-foreign-key-constraints.md) . Значение по умолчанию — False.  
  
 **Внести в скрипт полнотекстовые индексы**  
 Включает в скрипт полнотекстовые индексы. Значение по умолчанию — False. Дополнительные сведения см. в разделе [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).  
  
 **Внести в скрипт индексы**  
 Включает в скрипт кластеризованные, некластеризованные индексы и XML-индексы. Значение по умолчанию — True. Дополнительные сведения см. в разделе [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql).  
  
 **Внести в скрипт схемы секционирования**  
 Включить в скрипт схемы секционирования таблиц. Значение по умолчанию — False. Дополнительные сведения см. в разделе [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql).  
  
 **Внести в скрипт первичные ключи**  
 Включает в скрипт [ограничения первичных и внешних ключей](../../relational-databases/tables/primary-and-foreign-key-constraints.md) . Значение по умолчанию — True.  
  
 **Внести в скрипт команды сбора статистики**  
 Включает в скрипт определяемые пользователем команды сбора статистики. Значение по умолчанию — False. Дополнительные сведения см. в статье [CREATE STATISTICS (Transact-SQL)](/sql/t-sql/statements/create-statistics-transact-sql).  
  
 **Внести в скрипт триггеры**  
 Включает в скрипт триггеры. Значение по умолчанию — False. Дополнительные сведения см. в разделе [CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql).  
  
 **Внести в скрипт уникальные ключи**  
 Включает в скрипт [ограничения уникальности и ограничения проверки](../../relational-databases/tables/unique-constraints-and-check-constraints.md) . Значение по умолчанию — False.  
  
 **Внести в скрипт столбцы просмотра**  
 Объявляет столбцы представления в заголовках представлений. Значение по умолчанию — False. Дополнительные сведения см. в статье [CREATE VIEW (Transact-SQL)](/sql/t-sql/statements/create-view-transact-sql).  
  
 **ScriptDriIncludeSystemNames**  
 Включает созданные системой имена ограничений для обеспечения декларативной ссылочной целостности. Значение по умолчанию — False. Дополнительные сведения см. в разделе [REFERENTIAL_CONSTRAINTS &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/referential-constraints-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [Формирование скриптов (среда SQL Server Management Studio)](../../relational-databases/scripting/generate-scripts-sql-server-management-studio.md)  
  
  
