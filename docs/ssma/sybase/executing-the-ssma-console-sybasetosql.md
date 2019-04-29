---
title: Выполнение команд консоли SSMA (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Database Connection Commands
- Sybase Console,Manageability Commands
- Sybase Console,Migration Commands
- Sybase Console,Migration Preparation Command
- Sybase Console,Project Commands
- Sybase Console,Report Commands
- Sybase Console,Script File Commands
- Sybase Console,Script Generation Commands
ms.assetid: ea8950b7-fabc-4aa4-89f8-9573a2617d70
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6cbdd0a1394114e3fdef0511c7ed14658f7dd9b0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63126307"
---
# <a name="executing-the-ssma-console-sybasetosql"></a>Выполнение команд консоли SSMA (SybaseToSQL)
Корпорация Майкрософт предоставляет широкий набор сценариев файл команды для выполнения и контроля над SSMA действий. В последующих разделах подробно описано же.  
  
## <a name="script-file-commands"></a>Файл команд скриптов  
В консольном приложении используется определенные команды файла стандартный сценарий как перечисленные в этом разделе.  
  
## <a name="project-commands"></a>Команды для проекта  
Дескриптор команды проекта, создание проектов, открытие, сохранение и выход из проектов.  
  
### <a name="create-new-project"></a>Создание new-project  
Эта команда создает нового проекта SSMA.  
  
-   `project-folder` Указывает на начало создания проекта.  
  
-   `project-name` Указывает имя проекта. {строка}  
  
-   `overwrite-if-exists`Необязательный атрибут указывает, следует ли перезаписывать существующий проект. {значение типа boolean}  
  
-   `project-type:`Необязательный атрибут. Указывает тип проекта, который проекта «sql server 2005» или «sql server 2008"проекта или проекта «sql server 2012" или «sql server 2014"проекта или проекта «sql azure». Значение по умолчанию — «sql-server-2008».  
  
**Пример синтаксиса:**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>" (optional)  
  
   project-type="<sql-server-2008/sql-server-2005/sql-server-2012/sql-server-2014/sql-azure>"  
/>  
```  
Атрибут «перезаписать if-exists» **false** по умолчанию.  
  
Атрибут «тип проекта» **sql server-2008** по умолчанию.  
  
### <a name="open-project"></a>Открытие проекта  
Эта команда открывает проект.

-   `project-folder` Указывает на начало создания проекта. Команда завершается ошибкой, если указанная папка не существует.  {строка}  
  
-   `project-name` Указывает имя проекта. Команда завершается ошибкой, если указанный проект не существует.  {строка}  
  
**Пример синтаксиса:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
> [!NOTE]  
> SSMA для SAP ASE консольное приложение поддерживает обратную совместимость. Его можно использовать для открытия проектов, созданных с предыдущей версией SSMA.  
  
### <a name="save-project"></a>Сохранение проекта  
Эта команда сохраняет проект миграции.  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
  
### <a name="close-project"></a>Закрыть проект  
Эта команда закрывает проект миграции.  
  
**Пример синтаксиса:**  
  
```xml  
<close-project   
  if-modified="<save/error/ignore>"   (optional)  
/>  
```  
Атрибут «if-modified» является необязательным, **игнорировать** по умолчанию.  
  
## <a name="database-connection-commands"></a>Команды подключения базы данных  
Подключение к базе данных команд помогает соединиться с базой данных.  
  
> [!NOTE]  
> - **Обзор** функция пользовательского интерфейса не поддерживается в консоли.  
> - Дополнительные сведения о «Создание файлов сценария», см. в разделе [Создание файлов сценария &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
### <a name="connect-source-database"></a>подключения--базы данных источника  
Эта команда выполняет подключение к базе данных источника и загружает высокоуровневые метаданные базы данных-источника, но не все метаданные.
  
Если не удается установить соединение с источником, создается ошибка, и консольного приложения дальнейшей прекращает выполнение.
  
Определение сервера извлекается из атрибута name, определенных для каждого соединения в разделе сервера файле подключения сервера или файла скрипта.  
  
**Пример синтаксиса:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="force-load-sourcetarget-database"></a>Force-load-/ target-базы данных источника  
Эта команда загружает метаданные источника, и это полезно для работы над проектом миграции в автономном режиме.  
  
Если не удается установить подключение к исходной или целевой, формируется ошибка, и консольного приложения дальнейшей прекращает выполнение.  
  
Эта команда требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
**Пример синтаксиса:**  
  
```xml  
<force-load metabase="<source/target>" >  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
  
### <a name="reconnect-source-database"></a>повторное подключение--базы данных источника  
Эта команда выполняет повторное подключение к исходной базе данных, но не загружает все метаданные, в отличие от команды connect исходной базы данных.  
  
Если не удается установить (соединение с источником re), формируется ошибка и консольного приложения дальнейшей прекращает выполнение.  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="connect-target-database"></a>Connect-target-database  
Эта команда подключается к целевой базе данных SQL Server и загружает высокоуровневые метаданные целевой базы данных, но не метаданные полностью.  
  
Если не удается установить подключение к целевому объекту, формируется ошибка, и консольного приложения дальнейшей прекращает выполнение.  
  
Определение сервера извлекается из атрибута name, определенных для каждого соединения в разделе сервера файле подключения сервера или файла скрипта.  
  
**Пример синтаксиса:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
  
### <a name="reconnect-target-database"></a>повторное подключение target-базы данных  
  
Эта команда выполняет повторное подключение к целевой базе данных, но не загружает все метаданные, в отличие от команды connect целевую базу данных.  
  
Если не удается установить (подключение к целевому объекту re), формируется ошибка и консольного приложения дальнейшей прекращает выполнение.  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-commands"></a>Команды отчета  
Команды отчетов создавать отчеты о производительности различных действий консоли SSMA.  
  
### <a name="generate-assessment-report"></a>Создание оценка отчета  
  
Эта команда создает отчеты для оценки на базы данных-источника.  
  
Если подключение к базе данных источника не выполняется перед выполнением этой команды, ошибку и завершает работу консольного приложения.  
  
Ошибка при подключении к исходному серверу базы данных во время выполнения команды, а также приводит завершение консольного приложения.  
  
-   `conversion-report-folder:` Указывает папку, в котором можно хранить отчет об оценке. (необязательно)  
  
-   `object-name:` Указывает объекты, используемых при создании отчета оценки (поддерживает имена отдельного объекта или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, вызванной в атрибуте имени объекта (Если указан объект категории, то тип объекта будет называться «category»).  
  
-   `conversion-report-overwrite:` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** false. (необязательно)  
  
-   `write-summary-report-to:` Указывает путь, по которому будет создаваться отчет.  
  
    Если указано только путь к папке копией, затем файл по имени **AssessmentReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет два дополнительных раздела:  
  
    -   `report-errors` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
    -   `verbose` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
**Пример синтаксиса:**  
  
```xml  
<generate-assessment-report  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>"             (optional)  
  
  verbose="<true/false>"                       (optional)  
  
  report-errors="<true/false>"                 (optional)  
  
  assessment-report-folder="<folder-name>"          (optional)  
  
  conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<generate-assessment-report  
  
  assessment-report-folder="<folder-name>"            (optional)  
  
  conversion-report-overwrite="<true/false>"     (optional)  
  
>  
<metabase-object object-name="<object-name>"  
  
        object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-commands"></a>Команды миграции  
Команды миграции преобразовать схему целевой базы данных в исходной схеме и перенос данных на целевой сервер.  
  
### <a name="convert-schema"></a>преобразовать схему  
Эта команда выполняет преобразование схемы из источника в целевой схеме.  
  
Если подключение к исходной или целевой базе данных не выполняется перед выполнением этой команды или во время выполнения команды происходит сбой подключения к серверу базы данных исходной или целевой, ошибку и завершает работу консольного приложения.  
  
-   `conversion-report-folder:` Указывает папку, в котором можно хранить отчет об оценке. (необязательно)  
  
-   `object-name:` Указывает исходных объектов, используемых при преобразовании схемы (поддерживает имена отдельного объекта или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, вызванной в атрибуте имени объекта (Если указан объект категории, то тип объекта будет называться «category»).  
  
-   `conversion-report-overwrite:` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** false. (необязательно)  
  
-   `write-summary-report-to:` Указывает путь, по которому будет создан сводный отчет.  
  
    Если указано только путь к папке копией, затем файл по имени **SchemaConversionReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет два дополнительных раздела:  
  
    -   `report-errors` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
    -   `verbose` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
**Пример синтаксиса:**  
  
```xml  
<convert-schema  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  write-summary-report-to="<file-name/folder-name>"     (optional)  
  
  verbose="<true/false>"                          (optional)  
  
  report-errors="<true/false>"                    (optional)  
  
  conversion-report-folder="<folder-name>"             (optional)  
  
  conversion-report-overwrite="<true/false>"      (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder-name>"         (optional)  
  
  conversion-report-overwrite="<true/false>"> (optional)  
  
  <metabase-object object-name="<object-name>"  
  
    object-type="<object-category>"/>  
  
</convert-schema>  
```  
  
### <a name="migrate-data"></a>Перенос данных  
Эта команда переносит исходных данных в целевой объект.  
  
-   `object-name:` Указывает исходных объектов, для миграции данных (поддерживает имена отдельного объекта или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, вызванной в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `write-summary-report-to:` Указывает путь, по которому будет создаваться отчет.  
  
    Если указано только путь к папке копией, затем файл по имени **DataMigrationReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет два дополнительных раздела:  
  
    -   `report-errors` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
    -   `verbose` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
**Пример синтаксиса:**  
  
```xml  
<migrate-data  
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>">  
  
    <metabase-object object-name="<object-name>"/>  
  
    <metabase-object object-name="<object-name>"/>  
  
    <metabase-object object-name="<object-name>"/>  
  
    <data-migration-connection  
  
      source-use-last-used="true"/source-server="<server-unique-name>"  
  
      target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
или диспетчер конфигурации служб  
  
```xml  
<migrate-data  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-command"></a>Команда подготовки миграции  
Подготовка к миграции инициирует схемы сопоставления между исходной и целевой баз данных.  
  
> [!NOTE]  
> В выходных данных консоли по умолчанию для команды миграции — «Full» выходной отчет с отсутствия сообщений подробные сведения об ошибке: Только сводку в корневой узел дерева на объект источника.  
  
### <a name="map-schema"></a>map-schema  
Эта команда предоставляет сопоставление схемы базы данных-источника в целевую схему.  
  
-   `source-schema` Указывает исходную схему для миграции.  
  
-   `sql-server-schema` Указывает целевую схему, к которой будут перенесены в исходной схеме.  
  
**Пример синтаксиса:**  
  
```xml  
<map-schema source-schema="<source-schema>"  
  
sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-commands"></a>Команды управления  
Команды управляемости помогают синхронизировать объекты целевой базы данных с базы данных-источника.  
  
> [!NOTE]  
> В выходных данных консоли по умолчанию для команды миграции — «Full» выходной отчет с отсутствия сообщений подробные сведения об ошибке: Только сводку в корневой узел дерева на объект источника.  
  
### <a name="synchronize-target"></a>синхронизировать целевой объект  
Эта команда синхронизирует целевых объектов с целевой базой данных.  
 
Если эта команда выполняется в исходной базе данных, возникает ошибка.  
  
Если подключение целевой базы данных не выполняется перед выполнением этой команды или подключения к целевому серверу базы данных завершается ошибкой во время выполнения команды, ошибку и завершает работу консольного приложения.  
  
-   `object-name:` Указывает целевой объекты для синхронизации с целевой базой данных (поддерживает имена отдельного объекта или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, вызванной в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `on-error:` Указывает, следует ли для указания ошибок синхронизации в качестве предупреждения или ошибки. Доступные параметры для при ошибке:  
  
    -   report-total-as-warning  
  
    -   report-each-as-warning  
  
    -   Сбой скрипта  
  
-   `report-errors-to:` Указывает расположение отчет об ошибках для операции синхронизации (необязательно). Если только путь к папке, затем файл по имени **TargetSynchronizationReport.XML** создается.  
  
**Пример синтаксиса:**  
  
```xml  
<synchronize-target  
  
object-name="<object-name>"  
  
on-error="<report-total-as-warning/  
  
report-each-as-warning/  
  
fail-script>" (optional)  
  
  report-errors-to="<file-name/folder-name>"        (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<synchronize-target  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<synchronize-target>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
</synchronize-target>  
```  
  
### <a name="refresh-from-database"></a>обновление из базы данных  
Эта команда обновляет исходные объекты из базы данных.  
  
Если эта команда выполняется в целевой базе данных, формируется ошибка.  
  
Эта команда требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:` Указывает исходных объектов, используемых при обновлении данных из базы данных-источника (поддерживает имена отдельного объекта или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `on-error:` Указывает, следует ли вызывать обновление ошибки как предупреждения или ошибки. Доступные параметры для при ошибке:  
  
    -   report-total-as-warning  
  
    -   report-each-as-warning  
  
    -   Сбой скрипта  
  
-   `report-errors-to:` Указывает расположение отчет об ошибках для операции обновления (необязательно). Если только путь к папке, затем файл по имени **SourceDBRefreshReport.XML** создается.  
  
**Пример синтаксиса:**  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  on-error="<report-total-as-warning/  
  
             report-each-as-warning/  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name/folder-name>"        (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  object-type="<object-category>" />  
```  
или диспетчер конфигурации служб  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-commands"></a>Команды создания сценариев  
Команды создания сценариев выполнения двух задач: они помогают сохранить выходные данные в файле скрипта консоли, и они записывают выходные данные T-SQL на консоль или файл, созданный на основе параметров, можно указать.  
  
### <a name="save-as-script"></a>save-as-script  
Эта команда используется для сохранения скриптов для объектов в файл упоминалось, когда метабазы = target. Это является альтернативой команду синхронизации, в том, что мы получить скрипты и выполнить соответствует в целевой базе данных.  
  
Эта команда требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:` Указывает объекты, в которых сценарии должны быть сохранены (поддерживает имена отдельного объекта или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, вызванной в атрибуте имени объекта (Если указан объект категории, то тип объекта будет называться «category»).  
  
-   `metabase:` Указывает, является ли источником или целевой метабазы.  
  
-   `destination:` Указывает путь или папку, в котором необходимо сохранить сценарий. Если имя файла не указан, имя файла в формат (значение атрибута object_name) .out предоставляется.
  
-   `overwrite:` Если значение равно true, перекрывает тем же именем файла, если он существует. Он может иметь значения (true или false).  
  
**Пример синтаксиса:**  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  destination="<file-name/folder-name>"  
  
  overwrite="<true/false>"   (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file-name/folder-name>"  
  
    <metabase-object object-name="<object-name>"  
  
                     object-type="<object-category>"/>  
  
</save-as-script>  
```  
  
### <a name="convert-sql-statement"></a>sql инструкцию Convert
Эта команда преобразует инструкции SQL.  
  
-   `context` Указывает имя схемы.  
  
-   `destination` Указывает, хранятся ли выходные данные в файле.  
  
    Если этот атрибут не указан, преобразованный инструкцию T-SQL отображается в консоли. (необязательно)  
  
-   `conversion-report-folder` Указывает папку, в котором можно хранить отчет об оценке. (необязательно)  
  
-   `conversion-report-overwrite` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** false. (необязательно)  
  
-   `write-converted-sql-to` Указывает путь к папке файла (или) для которой должны храниться преобразованный код T-SQL. Если указан путь к папке вместе с `sql-files` атрибут, каждый исходный файл имеет соответствующий целевой файл T-SQL, созданный в указанной папке. Если указан путь к папке вместе с `sql` атрибут, преобразованный T-SQL, записывается в файл с именем Result.out в указанной папке.  
  
-   `sql` Задает Sybase инструкции sql для преобразования, один или несколько операторов могут быть разделены с помощью «;»  
  
-   `sql-files` Указывает путь к файлам sql, которое должно быть преобразовано в код T-SQL.  
  
-   `write-summary-report-to` Указывает путь, где будет создан сводный отчет. Если указано только путь к папке копией, затем файл по имени **ConvertSQLReport.XML** создается. (необязательно)  
  
    Создание сводного отчета имеет два дополнительных раздела, а именно:  
  
    -   ошибки (= «true/false» имеет значения по умолчанию как «false» (необязательных атрибутов)).  
  
    -   verbose (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов)).  
  
Эта команда требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
**Пример синтаксиса:**  
  
```  
<convert-sql-statement  
  
       context="<database-name>.<schema-name>"  
  
        conversion-report-folder="<folder-name>"  
  
        conversion-report-overwrite="<true/false>"  
  
        write-summary-report-to="<file-name/folder-name>"   (optional)  
  
        verbose="<true/false>"   (optional)  
  
        report-errors="<true/false>"   (optional)  
  
        destination="<stdout/file>"   (optional)  
  
        write-converted-sql-to ="<file-name/folder-name>"  
  
        sql="SELECT 1 FROM DUAL;">  
  
    <output-window suppress-messages="<true/false>" />  
  
</convert-sql-statement>  
```  
или диспетчер конфигурации служб  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         write-summary-report-to="<file-name/folder-name>"   (optional)  
  
         verbose="<true/false>"   (optional)  
  
         report-errors="<true/false>"   (optional)  
  
         destination="<stdout/file>"   (optional)  
  
         write-converted-sql-to ="<file-name/folder-name>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
или диспетчер конфигурации служб  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-steps"></a>Следующие шаги  
Сведения о параметрах командной строки, см. в разделе [параметры командной строки в консоли SSMA (AccessToSQL)](../access/command-line-options-in-ssma-console-accesstosql.md).  
  
Сведения о консоли образец файла скрипта, см. в разделе [работа с образцами файлов сценария консоли &#40;SybaseToSQL&#41;](../../ssma/sybase/working-with-the-sample-console-script-files-sybasetosql.md)  
  
Следующий шаг зависит от требований проекта:  
  
-   Для указания пароля или экспорта / импорта пароли, см. в разделе [управление паролями &#40;SybaseToSQL&#41;](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   Для создания отчетов, см. в разделе [Создание отчеты &#40;SybaseToSQL&#41;](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   Для устранения неполадок в консоли, см. в разделе [Устранение неполадок &#40;SybaseToSQL&#41;](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  
