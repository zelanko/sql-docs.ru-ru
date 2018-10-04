---
title: Выполнение команд консоли SSMA (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Oracle SSMA Console
- Script File Commands, Script Generation Commands,Manageability Commands
- Script File Commands,Project Commands
ms.assetid: 7228ccba-c69f-4b4c-8664-01a2750183c5
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 84194cf92cfd4c6270697aa1c3fd4f475df956ac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47714092"
---
# <a name="executing-the-ssma-console-oracletosql"></a>Выполнение команд консоли SSMA (OracleToSQL)
Корпорация Майкрософт предоставляет широкий набор сценариев файл команды для выполнения и контроля над SSMA действий. В консольном приложении используется определенные команды файла стандартный сценарий как перечисленные в этом разделе.  
  
## <a name="project-script-file-commands"></a>Команды для файла скрипта проекта  
Дескриптор команды проекта, создание проектов, открытие, сохранение и выход из проектов.  
  
**Command**  
  
Создание new-project  
                  : Создает проекта SSMA.  
  
**Скрипт**  
  
-   `project-folder` Указывает на начало создания проекта.  
  
-   `project-name` Указывает имя проекта. {строка}  
  
-   `overwrite-if-exists`Необязательный атрибут указывает, следует ли перезаписать существующий проект. {значение типа boolean}  
  
-   `project-type:`Необязательный атрибут. Указывает тип проекта т. е. проект «sql server 2005» или проекта «sql server 2008"или «sql server 2012" проекта или проекта «sql server 2014"или «sql azure». Значение по умолчанию — «sql server 2014».  
  
**Пример:**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014>"   (optional)  
  
/>  
```  
Атрибут «перезаписать if-exists» **false** по умолчанию.  
  
Атрибут «тип проекта» **sql server-2008** по умолчанию.  
  
**Command**  
  
открыть проект: открытие существующего проекта.  
  
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
SSMA для Oracle консольное приложение поддерживает обратную совместимость. Можно открывать проекты, созданные в предыдущей версии SSMA.  
  
**Command**  
  
Сохранение проекта  
  
Сохраняет проект миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
Закрыть проект  
  
Закрытие проекта миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<close-project  
  
   if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
  
## <a name="database-connection-script-file-commands"></a>Файл скрипта команд для базы данных соединения  
Подключение к базе данных команд помогает соединиться с базой данных.  
  
-   **Обзор** функция пользовательского интерфейса не поддерживается в консоли.  
  
-   Дополнительные сведения о «Создание файлов сценария», см. в разделе [Создание файлов сценария &#40;OracleToSQL&#41;](../../ssma/oracle/creating-script-files-oracletosql.md).  
  
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
  
Force-load-/ target-базы данных источника  
  
-   Загружает метаданные источника.  
  
-   Это удобно для работы над проектом миграции в автономном режиме.  
  
-   Если не удается установить подключение к исходной или целевой, формируется ошибка, и консольного приложения дальнейшей останавливает выполнение  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
**Пример синтаксиса:**  
  
```xml  
<force-load object-name="<object-name>"  
  
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
  
-   Подключается к целевой базе данных SQL Server и полностью загружает высокой метаданных уровня целевой базы данных, но не метаданные.  
  
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
  
## <a name="report-script-file--commands"></a>Команды файл скрипта отчетов  
Команды отчетов создавать отчеты о производительности различных действий консоли SSMA.  
  
**Command**  
  
Создание оценка отчета  
  
-   Создает отчеты для оценки на базы данных-источника.  
  
-   Если подключение к базе данных источника не выполняется перед выполнением этой команды, ошибку и завершает работу консольного приложения.  
  
-   Ошибка при подключении к исходному серверу базы данных во время выполнения команды, а также приводит завершение консольного приложения.  
  
**Скрипт**  
  
-   `conversion-report-folder:` Указывает папку, где отчет об оценке можно хранить. (необязательно)  
  
-   `object-name:` Указывает объекты, используемых при создании отчета оценки (он может иметь имена отдельных объектов или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `conversion-report-overwrite:` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** false. (необязательно)  
  
-   `write-summary-report-to:` Указывает путь, где будет создан сводный отчет.  
  
    Если указано только путь к папке копией, затем файл по имени **AssessmentReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
    -   `verbose` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
**Пример синтаксиса:**  
  
```xml  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   assessment-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<generate-assessment-report  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
>  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-script-file-commands"></a>Команды файл сценария миграции  
Команды миграции преобразовать схему целевой базы данных в исходной схеме и переносит данные на целевой сервер.  
  
В выходных данных консоли по умолчанию для команды миграции — «Full» выходной отчет с отчет не подробные сведения об ошибке выводится: только сводку в корневом узле дерева исходного объекта.  
  
**Command**  
  
преобразовать схему  
  
-   Выполняет преобразование схемы из источника в целевую схему.  
  
-   Если подключение к исходной или целевой базе данных не выполняется перед выполнением этой команды или во время выполнения команды происходит сбой подключения к серверу базы данных исходной или целевой, ошибку и завершает работу консольного приложения.  
  
**Скрипт**  
  
-   `conversion-report-folder:` Указывает папку, где отчет об оценке можно хранить. (необязательно)  
  
-   `object-name:` Указывает исходных объектов, используемых при преобразовании схемы (он может иметь имена отдельных объектов или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `conversion-report-overwrite:` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** false. (необязательно)  
  
-   `write-summary-report-to:` Указывает путь, где будет создан сводный отчет.  
  
    Если указано только путь к папке копией, затем файл по имени **SchemaConversionReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
    -   `verbose` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
**Пример синтаксиса:**  
  
```xml  
<convert-schema  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<convert-schema  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</convert-schema>  
```  
**Command**  
  
Перенос данных  
  
Переносит данные источника к целевому объекту.  
  
**Скрипт**  
  
-   `conversion-report-folder:` Указывает папку, где отчет об оценке можно хранить. (необязательно)  
  
-   `object-name:` Указывает исходных объектов, для миграции данных (она может иметь имена отдельных объектов или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `conversion-report-overwrite:` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** false. (необязательно)  
  
-   `write-summary-report-to:` Указывает путь, где будет создан сводный отчет.  
  
    Если указано только путь к папке копией, затем файл по имени **DataMigrationReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
    -   `verbose` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
**Пример синтаксиса:**  
  
```xml  
<migrate-data  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   report-errors="<true/false>"  
  
   verbose="<true/false>">  
  
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
  
   report-errors="<true/false>"  
  
   verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-script-file-commands"></a>Команды файл скрипта подготовки миграции  
Подготовка к миграции инициирует схемы сопоставления между исходной и целевой баз данных.  
  
**Command**  
  
map-schema  
  
Сопоставление схем базы данных-источника в целевую схему.  
  
Переносит данные источника к целевому объекту.  
  
**Скрипт**  
  
-   `source-schema` Указывает в исходной схеме, который мы собираемся перенести.  
  
-   `sql-server-schema` Указывает целевую схему, где мы удобно для миграции.  
  
**Пример синтаксиса:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>Команды файл сценария управляемости  
Команды управляемости помогают синхронизировать объекты целевой базы данных с базы данных-источника. В выходных данных консоли по умолчанию для команды миграции — «Full» выходной отчет с отчет не подробные сведения об ошибке выводится: только сводку в корневом узле дерева исходного объекта.  
  
**Command**  
  
синхронизировать целевой объект  
  
-   Синхронизирует целевых объектов с целевой базой данных.  
  
-   Если эта команда выполняется в исходной базе данных, возникает ошибка.  
  
-   Если подключение целевой базы данных не выполняется перед выполнением этой команды или подключения к целевому серверу базы данных завершается ошибкой во время выполнения команды, ошибку и завершает работу консольного приложения.  
  
**Скрипт**  
  
-   `object-name:` Указывает целевой объекты для синхронизации с целевой базой данных (она может иметь имена отдельных объектов или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `on-error:` Указывает, следует ли для указания ошибок синхронизации в качестве предупреждения или ошибки. Доступные параметры для при ошибке:  
  
    -   Общее число отчетов как предупреждение  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
-   `report-errors-to:` Указывает расположение отчет об ошибках для операции синхронизации (необязательно) если только путь к папке, затем файловых ресурсов по имени **TargetSynchronizationReport.XML** создается.  
  
**Пример синтаксиса:**  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name/folder-name>"   (optional)  
  
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
**Command**  
  
обновление из базы данных  
  
-   Обновляет объекты из базы данных-источника.  
  
-   Если эта команда выполняется в целевой базе данных, формируется ошибка.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:` Указывает исходных объектов, используемых при обновлении данных из базы данных-источника (он может иметь имена отдельных объектов или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `on-error:` Указывает, следует ли для указания ошибки обновления как предупреждения или ошибки. Доступные параметры для при ошибке:  
  
    -   Общее число отчетов как предупреждение  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
-   `report-errors-to:` Указывает расположение отчет об ошибках для операции обновления (необязательно) если только путь к папке, затем файловых ресурсов по имени **SourceDBRefreshReport.XML** создается.  
  
**Пример синтаксиса:**  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name/folder-name>"   (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<refresh-from-database>  
  
   <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>Команд файла скрипта создания скриптов  
Команды создания сценариев выполнения двух задач: они помогают сохранить выходные данные в файл скрипта; консоли, и запишите консоль или в файл, созданный на основе параметров, заданных выходных данных T-SQL.  
  
**Command**  
  
Сохранить как сценарий  
  
Позволяет сохранить скрипты объектов в файле, упомянутом при метабазы = цель, это является альтернативой команду синхронизации, где в мы получить скрипты и выполнить соответствует в целевой базе данных.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:` Указывает объекты, в которых сценарии должны быть сохранены. (Он может иметь имена отдельных объектов или имя объекта группы)  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
-   `metabase:` Указывает ли его вывод источника или целевой метабазы.  
  
-   `destination:` Указывает путь или папку, где сценарий должен быть сохранен, если имя файла не имеет затем имя файла в-out-формат (значение атрибута object_name)  
  
-   `overwrite:` Если значение true, затем он переопределяет Если существует такое же имя файла. Он может иметь значения (true или false).  
  
**Пример синтаксиса:**  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   destination="<file/folder>"  
  
   overwrite="<true/false>"   (optional)  
  
/>  
```  
или диспетчер конфигурации служб  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   destination="<file/folder>"  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</save-as-script>  
```  
**Command**  
  
sql инструкцию Convert  
  
-   `context` Указывает имя схемы.  
  
-   `destination` Указывает, хранятся ли выходные данные в файле.  
  
    Если этот атрибут не указан, преобразованный инструкцию T-SQL отображается в консоли. (необязательно)  
  
-   `conversion-report-folder` Указывает папку, где отчет об оценке можно хранить. (необязательно)  
  
-   `conversion-report-overwrite` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** false. (необязательно)  
  
-   `write-converted-sql-to` Указывает путь к папке, где будет храниться преобразованный T-SQL, файл (или). Если указан путь к папке вместе с `sql-files` атрибут, каждый исходный файл будет иметь соответствующий целевой объект T-SQL-файл, созданный в указанной папке. Если указан путь к папке вместе с `sql` атрибут, преобразованный T-SQL, записывается в файл с именем **Result.out** в указанной папке.  
  
-   `sql` Задает операторы sql, Oracle, для преобразования, один или несколько операторов можно разделенных с помощью «;»  
  
-   `sql-files` Указывает путь к файлам sql, который должен преобразовываться в код T-SQL.  
  
-   `write-summary-report-to` Указывает путь, где будет создаваться отчет. Если указано только путь к папке копией, затем файл по имени **ConvertSQLReport.XML** создается. (необязательно)  
  
    Создание имеет 2 дополнительных подкатегорий, находящие отклик у отчета.:  
  
    -   ошибки (= «true/false» имеет значения по умолчанию как «false» (необязательных атрибутов)).  
  
    -   verbose (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов)).  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
**Пример синтаксиса:**  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="<stdout/file>"   (optional)  
  
   file-name="<file-name>"  
  
   sql="SELECT 1 FROM DUAL;">  
  
   <output-window suppress-messages="<true/false>" />  
  
</convert-sql-statement>  
```  
или диспетчер конфигурации служб  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>" (optional)  
  
   verbose="<true/false>" (optional)  
  
   report-errors="<true/false>"  
  
   destination="<stdout/file>"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql-files="<folder-name>\*.sql" />  
```  
или диспетчер конфигурации служб  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   sql-files="<folder-name>\*.sql" />  
```  
  
## <a name="next-step"></a>Следующий шаг  
Сведения о параметрах командной строки, см. в разделе [параметры командной строки в консоли SSMA &#40;OracleToSQL&#41; ](../../ssma/oracle/command-line-options-in-ssma-console-oracletosql.md) .  
  
Сведения о образцами файлов сценария консоли, см. в разделе [работа с образцами файлов сценария консоли &#40;OracleToSQL&#41;](../../ssma/oracle/working-with-the-sample-console-script-files-oracletosql.md)  
  
Следующий шаг зависит от требований проекта:  
  
-   Для указания пароля или экспорта / импорта пароли, см. в разделе [управление паролями &#40;OracleToSQL&#41;](../../ssma/oracle/managing-passwords-oracletosql.md).  
  
-   Для создания отчетов, см. в разделе [Создание отчеты &#40;OracleToSQL&#41;](../../ssma/oracle/generating-reports-oracletosql.md).  
  
-   Для устранения неполадок в консоли, см. в разделе [Устранение неполадок &#40;OracleToSQL&#41;](../../ssma/oracle/troubleshooting-oracletosql.md).  
  
