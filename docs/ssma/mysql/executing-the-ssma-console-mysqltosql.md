---
title: Выполнение команд консоли SSMA (MySQLToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Script file commands, Database connection commands
- Script file commands, Manageability commands
- Script file commands, Migration commands
- Script file commands, Migration preparation commands
- Script file commands, project commands
- Script file commands, Report commands
- Script file commands, Script generation commands
ms.assetid: e3e9f7e4-0619-4861-a202-3d5d39953b26
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d309a1d0bbdf21c94458771e38aa67fd3eb3fe4d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102996"
---
# <a name="executing-the-ssma-console-mysqltosql"></a>Выполнение команд консоли SSMA (MySQLToSQL)
Корпорация Майкрософт предоставляет широкий набор сценариев файл команды для выполнения и контроля над SSMA действий.  
  
В консольном приложении используется определенные команды файла стандартный сценарий как перечисленные в этом разделе.  
  
## <a name="project--script-file-commands"></a>Команды для файла скрипта проекта  
**Command**  
  
Создание — новый проект:   
                   Создание проекта SSMA.  
  
Дескриптор команды проекта, создание проектов, открытие, сохранение и выход из проектов.  
  
**Скрипт**  
  
1.  `project-folder` Указывает на начало создания проекта.  
  
2.  `project-name` Указывает имя проекта. {строка}  
  
3.  `overwrite-if-exists`Необязательный атрибут указывает, следует ли перезаписать существующий проект. {значение типа boolean}  
  
4.  `project-type:`Необязательный атрибут. Указывает тип проекта т. е. «sql server 2005» проекта или проекта «sql server 2008"или «sql server 2012" или «sql server 2014"проекта или проекта «sql azure». Значение по умолчанию — «sql server 2008».  
  
**Пример синтаксиса:**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type=="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>"   (optional)  
  
/>  
```  
Атрибут «перезаписать if-exists» **false** по умолчанию.  
  
Атрибут «тип проекта» **sql server-2008** по умолчанию.  
  
**Command**  
  
открыть проект:   
                  Открывает существующий проект.  
  
**Скрипт**  
  
1.  `project-folder` Указывает на начало создания проекта. Команда завершается ошибкой, если указанная папка не существует.  {строка}  
  
2.  `project-name` Указывает имя проекта. Команда завершается ошибкой, если указанный проект не существует.  {строка}  
  
**Пример синтаксиса:**  
  
```xml  
<open-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
/>  
```  
> [!IMPORTANT]  
> SSMA для MySQL консольное приложение поддерживает обратную совместимость. Можно открывать проекты, созданные в предыдущей версии SSMA.  
  
**Command**  
  
Save проект: Сохраняет проект миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
Закрыть проект  
                  , перечислены ниже. Закрытие проекта миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
Закрыть проект  
                  , перечислены ниже. Закрытие проекта миграции.  
  
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
  
1.  **Обзор** функция пользовательского интерфейса не поддерживается в консоли.  
  
2.  **Проверку подлинности windows** и **порт** параметры не применяются, при подключении к SQL Azure.  
  
3.  Дополнительные сведения о «Создание файлов сценария», см. в разделе [Создание файлов сценария &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-script-files-mysqltosql.md).  
  
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
<force-load metabase="<source/target>"  
  
      <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Command**  
  
повторное подключение--базы данных источника  
  
1.  Выполняет повторное подключение к исходной базе данных, но не загружает все метаданные, в отличие от команды connect исходной базы данных.  
  
2.  Если не удается установить (соединение с источником re), формируется ошибка и консольного приложения дальнейшей прекращает выполнение.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
Connect-target-database  
  
1.  Подключается к базе данных назначения SQL Server или SQL Azure и загружает высокой метаданных уровня целевой базы данных, но не метаданные полностью.  
  
2.  Если не удается установить подключение к целевому объекту, формируется ошибка, и консольного приложения дальнейшей прекращает выполнение.  
  
**Скрипт**  
  
Определение сервера извлекается из атрибута name, определенных для каждого соединения в разделе сервера файле подключения сервера или файла скрипта  
  
**Пример синтаксиса:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
повторное подключение target-базы данных  
  
1.  Выполняет повторное подключение к целевой базе данных, но не загружает все метаданные, в отличие от команды connect целевую базу данных.  
  
2.  Если не удается установить (подключение к целевому объекту re), формируется ошибка и консольного приложения дальнейшей прекращает выполнение.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>Команды файл скрипта отчетов  
Команды отчетов создавать отчеты о производительности различных действий консоли SSMA.  
  
**Command**  
  
Создание оценка отчета  
  
1.  Создает отчеты для оценки на базы данных-источника.  
  
2.  Если подключение к базе данных источника не выполняется перед выполнением этой команды, ошибку и завершает работу консольного приложения.  
  
3.  Ошибка при подключении к исходному серверу базы данных во время выполнения команды, а также приводит завершение консольного приложения.  
  
**Скрипт**  
  
1.  `assessment-report-folder:` Указывает папку, где отчет об оценке можно хранить. (необязательно)  
  
2.  `object-name:` Указывает объекты, используемых при создании отчета оценки (он может иметь имена отдельных объектов или имя объекта группы).  
  
3.  `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
4.  `assessment-report-overwrite:` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** false. (необязательно)  
  
5.  `write-summary-report-to:` Указывает путь, где будет создан сводный отчет.  
  
    Если указано только путь к папке копией, затем файл по имени **AssessmentReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
    -   `verbose` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
**Пример синтаксиса:**  
  
```xml  
<generate-assessment-report  
  
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
<generate-assessment-report  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
>  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration--script-file-commands"></a>Команды файл сценария миграции  
Команды миграции преобразовать схему целевой базы данных в исходной схеме и переносит данные на целевой сервер.  
  
В выходных данных консоли по умолчанию для команды миграции — «Full» выходной отчет с отсутствия сообщений подробные сведения об ошибке: Только сводку в корневой узел дерева на объект источника.  
  
**Command**  
  
преобразовать схему  
  
1.  Выполняет преобразование схемы из источника в целевую схему.  
  
2.  Если подключение к исходной или целевой базе данных не выполняется перед выполнением этой команды или во время выполнения команды происходит сбой подключения к серверу базы данных исходной или целевой, ошибку и завершает работу консольного приложения.  
  
**Скрипт**  
  
1.  `conversion-report-folder:` Указывает папку, где отчет об оценке можно хранить. (необязательно)  
  
2.  `object-name:` Указывает объекты, используемых при преобразовании схемы (он может иметь имена отдельных объектов или имя объекта группы).  
  
3.  `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
4.  `conversion-report-overwrite:` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** false. (необязательно)  
  
5.  `write-summary-report-to:` Указывает путь, где будет создан сводный отчет.  
  
    Если указано только путь к папке копией, затем файл по имени **SchemaConversionReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание сводного отчета имеет две дополнительные подкатегории:  
  
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
  
      <metabase-object object-name="<object-names>"  
  
         object-type="<object-category>"/>  
  
</convert-schema>  
```  
**Command**  
  
Перенос данных  
  
1.  Переносит данные источника к целевому объекту.  
  
**Скрипт**  
  
1.  `object-name:` Указывает исходных объектов, для миграции данных (она может иметь имена отдельных объектов или имя объекта группы).  
  
2.  `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
3.  `write-summary-report-to:` Указывает путь, где будет создан сводный отчет.  
  
    Если указано только путь к папке копией, затем файл по имени **DataMigrationReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
    -   `verbose` (= «true/false», имеет значения по умолчанию как «false» (необязательных атрибутов))  
  
**Пример синтаксиса:**  
  
```xml  
<migrate-data  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   report-errors="true" verbose="true">  
  
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
  
   report-errors="true" verbose="true"/>  
```  
  
## <a name="migration-preparation-script-file-command"></a>Команда файл скрипта подготовки миграции  
Подготовка к миграции инициирует схемы сопоставления между исходной и целевой баз данных.  
  
**Command**  
  
map-schema  
  
Сопоставление схем базы данных-источника в целевую схему.  
  
**Скрипт**  
  
1.  `source-schema` Указывает в исходной схеме, который мы собираемся перенести.  
  
2.  `sql-server-schema` Указывает целевую схему, где мы удобно для миграции.  
  
**Пример синтаксиса:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>Команды файл сценария управляемости  
Команды управляемости помогают синхронизировать объекты целевой базы данных с базы данных-источника.  
  
> [!NOTE]  
> В выходных данных консоли по умолчанию для команды миграции — «Full» выходной отчет с отсутствия сообщений подробные сведения об ошибке: Только сводку в корневой узел дерева на объект источника.  
  
**Command**  
  
синхронизировать целевой объект  
  
1.  Синхронизирует целевых объектов с целевой базой данных.  
  
2.  Если эта команда выполняется в исходной базе данных, возникает ошибка.  
  
3.  Если подключение целевой базы данных не выполняется перед выполнением этой команды или подключения к целевому серверу базы данных завершается ошибкой во время выполнения команды, ошибку и завершает работу консольного приложения.  
  
**Скрипт**  
  
1.  `object-name:` Задает объекты для синхронизации с целевой базой данных (она может иметь имена отдельных объектов или имя объекта группы).  
  
2.  `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
3.  `on-error:` Указывает, следует ли для указания ошибок синхронизации в качестве предупреждения или ошибки. Доступные параметры для при ошибке:  
  
    -   Общее число отчетов как предупреждение  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
4.  `report-errors-to:` Указывает расположение отчет об ошибках для операции синхронизации (необязательно) если только путь к папке, затем файловых ресурсов по имени **TargetSynchronizationReport.XML** создается.  
  
**Пример синтаксиса:**  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name>"   (optional)  
  
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
  
1.  Обновляет объекты из базы данных-источника.  
  
2.  Если эта команда выполняется в целевой базе данных, формируется ошибка.  
  
**Скрипт**  
  
1.  `object-name:` Указывает исходных объектов, используемых при обновлении данных из базы данных-источника (он может иметь имена отдельных объектов или имя объекта группы).  
  
2.  `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
3.  `on-error:` Указывает, следует ли для указания ошибок синхронизации в качестве предупреждения или ошибки. Доступные параметры для при ошибке:  
  
    -   Общее число отчетов как предупреждение  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
4.  `report-errors-to:` Указывает расположение отчет об ошибках для операции синхронизации (необязательно) если только путь к папке, затем файловых ресурсов по имени **SourceDBRefreshReport.XML** создается.  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
**Пример синтаксиса:**  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name>"   (optional)  
  
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
Команды создания сценариев выполнения двух задач: Они помогают сохранить выходные данные в файл скрипта; консоли и запишите консоль или в файл, созданный на основе параметров, заданных выходных данных T-SQL.  
  
**Command**  
  
Сохранить как сценарий  
  
Позволяет сохранить скрипты объектов в файле, упомянутом при метабазы = цель, это является альтернативой команду синхронизации, где в мы получить скрипты и выполнить соответствует в целевой базе данных.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
1.  `object-name:` Указывает объекты, в которых сценарии должны быть сохранены. (Он может иметь имена отдельных объектов или имя объекта группы)  
  
2.  `object-type:` Указывает тип объекта, указанного в атрибуте имени объекта (если объект категории указан тип объекта будет «category»).  
  
3.  `metabase:` Указывает, является ли источником или целевой метабазы.  
  
4.  `destination:` Указывает путь или папку, где сценарий должен быть сохранен, если имя файла не имеет затем имя файла в-out-формат (значение атрибута object_name)  
  
5.  `overwrite:` Если значение true, затем он переопределяет Если существует такое же имя файла. Он может иметь значения (true или false).  
  
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
**Command**  
  
sql инструкцию Convert  
  
1.  `context` Указывает имя схемы.  
  
2.  `destination` Указывает, хранятся ли выходные данные в файле.  
  
    Если этот атрибут не указан, преобразованный инструкцию T-SQL отображается в консоли. (необязательно)  
  
3.  `conversion-report-folder` Указывает папку, где отчет об оценке можно хранить. (необязательно)  
  
4.  `conversion-report-overwrite` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** false. (необязательно)  
  
5.  `write-converted-sql-to` Указывает путь к папке, где будет храниться преобразованный T-SQL, файл (или). Если указан путь к папке вместе с `sql-files` атрибут, каждый исходный файл будет иметь соответствующий целевой объект T-SQL-файл, созданный в указанной папке. Если указан путь к папке вместе с `sql` атрибут, преобразованный T-SQL, записывается в файл с именем Result.out в указанной папке.  
  
6.  `sql` Задает операторы sql, MySQL для преобразования, один или несколько операторов можно разделенных с помощью «;»  
  
7.  `sql-files` Указывает путь к файлам sql, который должен преобразовываться в код T-SQL.  
  
8.  `write-summary-report-to` Указывает путь, где будет создан сводный отчет. Если указано только путь к папке копией, затем файл по имени **ConvertSQLReport.XML** создается. (необязательно)  
  
    Создание имеет 2 дополнительных подкатегорий, находящие отклик у отчета..,:  
  
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
  
   destination="stdout/file"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
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
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="<stdout/file>"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql-files="<folder-name>\*.sql"  
  
/>  
```  
или диспетчер конфигурации служб  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-step"></a>Следующий шаг  
Сведения о параметрах командной строки, см. в разделе [параметры командной строки в консоли SSMA &#40;MySQLToSQL&#41; ](../../ssma/mysql/command-line-options-in-ssma-console-mysqltosql.md) .  
  
Дополнительные сведения о образцами файлов сценария консоли, см. в разделе [работа с образцами файлов сценария консоли &#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-the-sample-console-script-files-mysqltosql.md)  
  
Следующий шаг зависит от требований проекта:  
  
1.  Для указания пароля или экспорта / импорта пароли, см. в разделе [управление паролями &#40;MySQLToSQL&#41;](../../ssma/mysql/managing-passwords-mysqltosql.md).  
  
2.  Для создания отчетов, см. в разделе [Создание отчеты &#40;MySQLToSQL&#41;](../../ssma/mysql/generating-reports-mysqltosql.md).  
  
3.  Для устранения неполадок в консоли, см. в разделе [Устранение неполадок &#40;MySQLToSQL&#41;](../../ssma/mysql/troubleshooting-mysqltosql.md).  
  
