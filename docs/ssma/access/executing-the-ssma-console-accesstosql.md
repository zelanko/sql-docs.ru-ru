---
title: Выполнение команд консоли SSMA (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: aa1bf665-8dc0-4259-b36f-46ae67197a43
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 97425a6795889f72b329280ff70f9638378e7799
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006572"
---
# <a name="executing-the-ssma-console-accesstosql"></a>Выполнение команд консоли SSMA (AccessToSQL)
Майкрософт предоставляет широкий набор команд файла скрипта и параметры командной строки для выполнения и SSMA действия управления. В последующих разделах подробно описано же.  
  
## <a name="project--script-file-commands"></a>Команды для файла скрипта проекта  
Дескриптор команды проекта, создание проектов, открытие, сохранение и выход из проектов.  
  
**Command**  
  
Создание — новый проект: Создание проекта SSMA.  
  
**Скрипт**  
  
-   `project-folder` Указывает на начало создания проекта.  
  
-   `project-name` Указывает имя проекта. {строка}  
  
-   `overwrite-if-exists`Необязательный атрибут указывает, следует ли перезаписать существующий проект. {значение типа boolean}  
  
-   `project-type` является необязательным атрибутом.  Следующие параметры доступны для типа проекта:  
  
    -   SQL server 2005 г.  
  
    -   SQL server 2008 г.  
  
    -   SQL server 2012 г.  
  
    -   SQL server 2014 г.  
  
    -   SQL server 2016 г.  
  
    -   SQL azure  
  
    Значение по умолчанию — «sql server 2008».  
  
**Пример.**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>"  
  
  project-type="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>"  
  
/>  
```  
Атрибут «перезаписать if-exists» **false** по умолчанию.  
  
Атрибут «тип проекта» **sql server-2008** по умолчанию.  
  
**Command**  
  
открыть проект: Открывает существующий проект.  
  
**Скрипт**  
  
-   `project-folder` Указывает на начало создания проекта. Команда завершается ошибкой, если указанная папка не существует.  {строка}  
  
-   `project-name` Указывает имя проекта. Команда завершается ошибкой, если указанный проект не существует.  {строка}  
  
**Пример синтаксиса:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
**Примечание.** SSMA для Access консольное приложение поддерживает обратную совместимость. Можно открывать проекты, созданные в предыдущей версии SSMA.  
  
**Command**  
  
Save проект: Сохраняет проект миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
Close проект: Закрытие проекта миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<close-project  
  
  if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
Атрибут «if-modified» является необязательным, **игнорировать** по умолчанию.  
  
## <a name="database-connection-script-file-commands"></a>Файл скрипта команд для базы данных соединения  
Подключение к базе данных команд помогает соединиться с базой данных.  
  
**Обзор** функция пользовательского интерфейса не поддерживается в консоли.  
  
**Проверку подлинности windows** и **порт** параметры не применяются, при подключении к SQL Azure.  
  
Дополнительные сведения о «Создание файлов сценария», см. в разделе [Создание файлов сценария &#40;AccessToSQL&#41;](../../ssma/access/creating-script-files-accesstosql.md).  
  
**Command**  
  
подключения--базы данных источника  
  
-   Выполняет подключение к базе данных источника и загружает высокой метаданных уровня базы данных-источника, но не все метаданные.  
  
-   Если не удается установить соединение с источником, формируется ошибка, и консольного приложения дальнейшей останавливает выполнение  
  
**Скрипт**  
  
Определение сервера извлекается из атрибута name, определенных для каждого соединения в разделе сервера файле подключения сервера или файла скрипта.  
  
**Пример синтаксиса:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
Load-access-database: Используется для загрузки файлов баз данных access  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<load-access-database  database-file="<Access-database>"/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<load-access-database>  
  
  <access-database database-file="<Access-database1>"/>  
  
  <access-database database-file="<Access-database2>"/>  
  
</load-access-database>  
```  
**Command**  
  
Force-load-/ target-базы данных источника  
  
-   Загружает метаданные источника.  
  
-   Это удобно для работы над проектом миграции в автономном режиме.  
  
-   Если не удается установить подключение к исходной или целевой, формируется ошибка, и консольного приложения дальнейшей останавливает выполнение  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
**Пример синтаксиса:**  
  
```xml  
<force-load  
  
  object-name="<object-name>"  
  
  metabase="<source/target>"/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<force-load>  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Command**  
  
повторное подключение--базы данных источника  
  
-   Выполняет повторное подключение к исходной базе данных, но не загружает все метаданные, в отличие от команды connect исходной базы данных.  
  
-   Если не удается установить (соединение с источником re), формируется ошибка и консольного приложения дальнейшей прекращает выполнение.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
Connect-target-database  
  
-   Подключается к базе данных назначения SQL Server или SQL Azure и загружает высокой метаданных уровня целевой базы данных, но не метаданные полностью.  
  
-   Если не удается установить подключение к целевому объекту, формируется ошибка, и консольного приложения дальнейшей прекращает выполнение.  
  
**Скрипт**  
  
Определение сервера извлекается из атрибута name, определенных для каждого соединения в разделе сервера файле подключения сервера или файла скрипта  
  
**Пример синтаксиса:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
повторное подключение target-базы данных  
  
-   Выполняет повторное подключение к целевой базе данных, но не загружает все метаданные, в отличие от команды connect целевую базу данных.  
  
-   Если не удается установить (подключение к целевому объекту re), формируется ошибка и консольного приложения дальнейшей прекращает выполнение.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>Команды файл скрипта отчетов  
Команды отчетов создавать отчеты о производительности различных действий консоли SSMA.  
  
**Command**  
  
Создание оценка отчета  
  
-   Создает отчеты для оценки на базы данных-источника.  
  
-   Если подключение к базе данных источника не выполняется перед выполнением этой команды, ошибку и завершает работу консольного приложения.  
  
-   Ошибка при подключении к исходному серверу базы данных во время выполнения команды, а также приводит завершение консольного приложения.  
  
**Скрипт**  
  
-   `assessment-report-folder:` Указывает папку, где отчет об оценке можно хранить. (необязательно)  
  
-   `object-name:` Указывает объекты, используемых при создании отчета оценки (он может иметь имена отдельных объектов или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `assessment-report-overwrite:` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** false. (необязательно)  
  
-   `write-summary-report-to:` Указывает путь, где будет создаваться отчет.  
  
    Если указано только путь к папке копией, затем файл по имени **AssessmentReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
    -   `verbose` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
**Пример синтаксиса:**  
  
```xml  
<generate-assessment-report  
  
  object-name="ssma.Procedures"  
  
  object-type="category"  
  
  write-summary-report-to="<file>"             (optional)  
  
  verbose="<true/false>"                       (optional)  
  
  report-errors="<true/false>"                 (optional)  
  
  conversion-report-folder="<folder>"          (optional)  
  
  conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<generate-assessment-report  
  
  conversion-report-folder="<folder>"            (optional)  
  
  conversion-report-overwrite="<true/false>"     (optional)  
  
>  
    <metabase-object object-name="ssma.Procedures"  
  
        object-type="category"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-script-file-commands"></a>Команды файл сценария миграции  
Команды миграции преобразовать схему целевой базы данных в исходной схеме и переносит данные на целевой сервер.  
  
В выходных данных консоли по умолчанию для команды миграции — «Full» выходной отчет с отсутствия сообщений подробные сведения об ошибке: Только сводку в корневой узел дерева на объект источника.  
  
**Command**  
  
преобразовать схему  
  
-   Выполняет преобразование схемы из источника в целевую схему.  
  
-   Если подключение к исходной или целевой базе данных не выполняется перед выполнением этой команды или во время выполнения команды происходит сбой подключения к серверу базы данных исходной или целевой, ошибку и завершает работу консольного приложения.  
  
**Скрипт**  
  
-   `conversion-report-folder:` Указывает папку, где можно сохранить отчет об оценке. (необязательно)  
  
-   `object-name:` Указывает исходных объектов, используемых при преобразовании схемы (он может иметь имена отдельных объектов или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `conversion-report-overwrite:` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** false. (необязательно)  
  
-   `write-summary-report-to:` Указывает путь, где будет создаваться отчет.  
  
    Если указано только путь к папке копией, затем файл по имени **SchemaConversionReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
    -   `verbose` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
**Пример синтаксиса:**  
  
```xml  
<convert-schema  
  
  object-name="ssma.Procedures"  
  
  object-type="category"  
  write-summary-report-to="<filepath/folder>"     (optional)  
  
  verbose="<true/false>"                          (optional)  
  
  report-errors="<true/false>"                    (optional)  
  
  conversion-report-folder="<folder>"             (optional)  
  
  conversion-report-overwrite="<true/false>"      (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder>"         (optional)  
  
  conversion-report-overwrite="<true/false>"  (optional)  
  
  <metabase-object object-name="ssma.Procedures"  
  
    object-type="category"/>  
  
</convert-schema>  
```  
**Command**  
  
Перенос данных  
  
1.  Переносит данные источника к целевому объекту.  
  
**Скрипт**  
  
-   `object-name:` Указывает исходных объектов, для миграции данных (она может иметь имена отдельных объектов или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `write-summary-report-to:` Указывает путь, где будет создаваться отчет.  
  
    Если указано только путь к папке копией, затем файл по имени **DataMigrationReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
    -   `verbose` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
**Пример синтаксиса:**  
  
```xml  
<migrate-data  
  
  write-summary-report-to="<filepath/folder>"  
  
  report-errors="true" verbose="true">  
  
    <metabase-object object-name="ssma.TT1"/>  
  
    <metabase-object object-name="ssma.TT2"/>  
  
    <metabase-object object-name="ssma.TT3"/>  
  
    <data-migration-connection  
  
      source-use-last-used="true"/source-server="<server-unique-name>"  
  
      target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
или диспетчер конфигурации служб  
  
```xml  
<migrate-data  
  
  object-name="ssma.Tables"  
  
  object-type="category"  
  
  write-summary-report-to="<filepath/folder>"  
  
  report-errors="true" verbose="true"/>  
```  
**Command**  
  
таблицы ссылок: Эта команда связывает целевой таблицы в таблице источника (доступ).  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<link-tables>  
  
  <metabase-object object-name="AccessDatabase.table1" object-type="Tables"/>  
  
  <metabase-object object-name="AccessDatabase.table2" object-type="Tables"/>  
  
</link-tables>  
```  
или диспетчер конфигурации служб  
  
```xml  
<link-tables>  
  
  <metabase-object object-name="AccessDatabase.Tables" object-type="category"/>  
  
</link-tables>  
```  
**Command**  
  
отменить привязку таблицы: Эта команда удаляет связь в таблице источника (доступ) из целевой таблицы.  
  
**Скрипт**  
  
**Примеры синтаксиса.**  
  
```xml  
<unlink-tables>  
  
  <metabase-object object-name="AccessDatabase.table1" object-type="Tables"/>  
  
  <metabase-object object-name="AccessDatabase.table2" object-type="Tables"/>  
  
</unlink-tables>  
```  
или диспетчер конфигурации служб  
  
```xml  
<unlink-tables>  
  
  <metabase-object object-name="AccessDatabase.Tables" object-type="category"/>  
  
</unlink-tables>  
```  
  
## <a name="migration-preparation-script-file-commands"></a>Команды файл скрипта подготовки миграции  
Подготовка к миграции инициирует схемы сопоставления между исходной и целевой баз данных.  
  
**Command**  
  
Схема сопоставления: Сопоставление схем базы данных-источника в целевую схему.  
  
**Скрипт**  
  
-   `source-schema` Указывает в исходной схеме, который мы собираемся перенести.  
  
-   `sql-server-schema` Указывает целевую схему, где мы удобно для миграции.  
  
**Пример синтаксиса:**  
  
```xml  
<map-schema source-schema="source-schema"  
  
            sql-server-schema="target-schema"/>  
```  
  
## <a name="manageability-commands"></a>Команды управления  
Команды управляемости помогают синхронизировать объекты целевой базы данных с базы данных-источника.  
  
В выходных данных консоли по умолчанию для команды миграции — «Full» выходной отчет с отсутствия сообщений подробные сведения об ошибке: Только сводку в корневой узел дерева на объект источника.  
  
**Command**  
  
синхронизировать целевой объект  
  
1.  Синхронизирует целевых объектов с целевой базой данных.  
  
2.  Если эта команда выполняется в исходной базе данных, возникает ошибка.  
  
3.  Если подключение целевой базы данных не выполняется перед выполнением этой команды или подключения к целевому серверу базы данных завершается ошибкой во время выполнения команды, ошибку и завершает работу консольного приложения.  
  
**Скрипт**  
  
1.  `object-name:` Указывает целевой объекты для синхронизации с целевой базой данных (она может иметь имена отдельных объектов или имя объекта группы).  
  
2.  `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
3.  `on-error:` Указывает, следует ли для указания ошибок синхронизации в качестве предупреждения или ошибки. Доступные параметры для при ошибке:  
  
    -   Общее число отчетов как предупреждение  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
4.  `report-errors-to:` Указывает расположение отчет об ошибках для операции синхронизации (необязательно) если только путь к папке, затем файловых ресурсов по имени **TargetSynchronizationReport.XML** создается.  
  
**Пример синтаксиса:**  
  
```xml  
<synchronize-target  
  
  object-name="ots_triggers.dbo"  
  
  on-error="<report-total-as-warning|  
  
             report-each-as-warning|  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name>"        (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<synchronize-target  
  
  object-name="ssma.dbo.Procedures"  
  
  object-type="category"/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<synchronize-target>  
  
  <metabase-object object-name="ssma.dbo.TT1"/>  
  
  <metabase-object object-name="ssma.dbo.TT2"/>  
  
  <metabase-object object-name="ssma.dbo.TT3"/>  
  
</synchronize-target>  
```  
**Command**  
  
обновление из базы данных  
  
-   Обновляет объекты из базы данных-источника.  
  
-   Если эта команда выполняется в целевой базе данных, формируется ошибка.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
1.  `object-name:` Указывает исходных объектов, используемых при обновлении данных из базы данных-источника (он может иметь имена отдельных объектов или имя объекта группы).  
  
2.  `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
3.  `on-error:` Указывает, следует ли для указания ошибки обновления как предупреждения или ошибки. Доступные параметры для при ошибке:  
  
    -   Общее число отчетов как предупреждение  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
4.  `report-errors-to:` Указывает расположение отчет об ошибках для операции обновления (необязательно) если только путь к папке, затем файловых ресурсов по имени **SourceDBRefreshReport.XML** создается.  
  
**Пример синтаксиса:**  
  
```xml  
<refresh-from-database  
  
  object-name="ssma.TT1"  
  
  on-error="<report-total-as-warning|  
  
             report-each-as-warning|  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name>"        (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<refresh-from-database  
  
  object-name="ssma.Procedures"  
  
  object-type="category"/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="ssma.TT_1"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>Команд файла скрипта создания скриптов  
Создание скрипта, который команд помогает сохранить выходные данные консоли в файле скрипта.  
  
**Command**  
  
Сохранить как сценарий  
  
Позволяет сохранить скрипты объектов в файле, упомянутом при метабазы = цель, это является альтернативой команду синхронизации, где в мы получить скрипты и выполнить соответствует в целевой базе данных.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:` Указывает объекты, в которых сценарии должны быть сохранены. (Он может иметь имена отдельных объектов или имя объекта группы)  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `metabase:` Указывает, является ли источником или целевой метабазы.  
  
-   `destination:` Указывает путь или папку, где сценарий должен быть сохранен, если имя файла не имеет затем имя файла в-out-формат (значение атрибута object_name)  
  
-   `overwrite:` Если значение true, затем он переопределяет Если существует такое же имя файла. Он может иметь значения (true или false).  
  
**Пример синтаксиса:**  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  object-name="ssma.dbo.Procedures"  
  
  object-type="category"  
  
  destination="<file/folder>"  
  
  overwrite="<true/false>"             (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file/folder>"  
  
    <metabase-object object-name="ssma.dbo.Procedures"  
  
                     object-type="category"/>  
  
</save-as-script>  
```  
  
## <a name="next-step"></a>Следующий шаг  
Сведения о параметрах командной строки, см. в разделе [параметры командной строки в консоли SSMA &#40;AccessToSQL&#41; ](../../ssma/access/command-line-options-in-ssma-console-accesstosql.md) .  
  
Сведения о образцами файлов сценария консоли, см. в разделе [работа с FilesExecuting сценария образец консоли команд консоли SSMA &#40;AccessToSQL&#41;](../../ssma/access/working-sample-console-script-filesexecuting-ssma-console-accesstosql.md)  
  
Следующий шаг зависит от требований проекта:  
  
-   Для указания пароля или экспорта / импорта пароли, см. в разделе [управление паролями &#40;AccessToSQL&#41;](../../ssma/access/managing-passwords-accesstosql.md).  
  
-   Для создания отчетов, см. в разделе [Создание отчеты &#40;AccessToSQL&#41;](../../ssma/access/generating-reports-accesstosql.md).  
  
-   Для устранения неполадок в консоли, см. в разделе [Устранение неполадок &#40;AccessToSQL&#41;](../../ssma/access/troubleshooting-accesstosql.md).  
  
