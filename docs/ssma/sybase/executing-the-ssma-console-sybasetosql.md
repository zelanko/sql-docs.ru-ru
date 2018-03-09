---
title: "Выполнение консоли SSMA (SybaseToSQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
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
caps.latest.revision: "22"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5a76b457d7178483d18a5a7a26d176d7e606b6fa
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="executing-the-ssma-console-sybasetosql"></a>Выполнение консоли SSMA (SybaseToSQL)
Корпорация Майкрософт предоставляет широкий набор сценариев файл команд для выполнения и контроля над SSMA действий. В последующих разделах подробно одинаковыми.  
  
## <a name="script-file-commands"></a>Команды сценария файла  
В консольном приложении используется определенных команд файла стандартный сценарий как перечисленные в этом разделе.  
  
## <a name="project-commands"></a>Проект команды  
Дескриптор команды проекта, создание проектов, открытие, сохранение и выход из проектов.  
  
### <a name="create-new-project"></a>Создание нового проекта  
Эта команда создает новый проект SSMA.  
  
-   `project-folder`Указывает папку проект, созданный в начало.  
  
-   `project-name`Указывает имя проекта. {Строка}  
  
-   `overwrite-if-exists`Необязательный атрибут указывает, следует ли перезаписывать существующий проект. {значение типа boolean}  
  
-   `project-type:`Необязательный атрибут. Указывает тип проекта, проекта «sql server 2005» или проекта «sql server 2008» или проекта «sql server 2012» или «sql server 2014» проекта или проекта «sql azure». Значение по умолчанию — «sql-server-2008».  
  
**Пример синтаксиса:**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>" (optional)  
  
   project-type=”<sql-server-2008/sql-server-2005/sql-server-2012/sql-server-2014/sql-azure>”  
/>  
```  
Атрибут «перезаписать if-exists» **false** по умолчанию.  
  
Атрибут «тип проекта» **sql server 2008** по умолчанию.  
  
### <a name="open-project"></a>Открытие проекта  
Эта команда открывает проект.

-   `project-folder`Указывает папку проект, созданный в начало. Команда завершается ошибкой, если указанная папка не существует.  {Строка}  
  
-   `project-name`Указывает имя проекта. Команда завершается ошибкой, если указанный проект не существует.  {Строка}  
  
**Пример синтаксиса:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
> [!NOTE]  
> SSMA для консольного приложения SAP ASE поддерживает обратную совместимость. Его можно использовать для открытия проектов, созданных с предыдущей версии SSMA.  
  
### <a name="save-project"></a>Сохранение проекта  
Эта команда сохраняет проекта миграции.  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
  
### <a name="close-project"></a>Закрытие проекта  
Эта команда закрывает проекта миграции.  
  
**Пример синтаксиса:**  
  
```xml  
<close-project   
  if-modified="<save/error/ignore>"   (optional)  
/>  
```  
Атрибут «if-modified» является необязательным, **игнорировать** по умолчанию.  
  
## <a name="database-connection-commands"></a>Команды подключения базы данных  
Команды подключения к базе данных позволяют подключать к базе данных.  
  
> [!NOTE]  
> - **Обзор** компонент пользовательского интерфейса не поддерживается в консоли.  
> - Дополнительные сведения о «Создание файлов скриптов» в разделе [Создание файлов скриптов &#40; SybaseToSQL &#41; ](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
### <a name="connect-source-database"></a>подключения--базы данных источника  
Эта команда выполняет подключение к базе данных источника и загружает метаданные высокого уровня базы данных-источника, но не все метаданные.
  
Если не удается установить соединение с источником, возникнет ошибка, и консольного приложения дальнейшей останавливает выполнение.
  
Определение сервера извлекается из атрибута name, определенных для каждого соединения в разделе сервер файла подключения сервера или файла скрипта.  
  
**Пример синтаксиса:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="force-load-sourcetarget-database"></a>Force нагрузки-/ target-базы данных источника  
Эта команда загружает метаданные источника и полезна для работы над проектом миграции в автономный режим.  
  
Если не удается установить соединение с исходной или целевой, возникает ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
Эта команда требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
**Пример синтаксиса:**  
  
```xml  
<force-load metabase=”<source/target>” >  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
  
### <a name="reconnect-source-database"></a>повторное подключение--базы данных источника  
Эта команда выполняет повторное подключение к исходной базе данных, но не загружает все метаданные, в отличие от команды Подключение исходной базы данных.  
  
Если не удается установить (соединение с источником re), возникнет ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="connect-target-database"></a>подключения target-базы данных  
Эта команда подключается к целевой базе данных SQL Server и полностью загружает общие метаданные целевой базы данных, но не метаданные.  
  
Если не удается установить подключение к целевому объекту, возникает ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
Определение сервера извлекается из атрибута name, определенных для каждого соединения в разделе сервер файла подключения сервера или файла скрипта.  
  
**Пример синтаксиса:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
  
### <a name="reconnect-target-database"></a>повторное подключение target-базы данных  
  
Эта команда выполняет повторное подключение к целевой базе данных, но не загружает все метаданные, в отличие от команды подключение целевой базы данных.  
  
Если не удается установить (подключение к целевому объекту re), возникнет ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-commands"></a>Команды отчета  
Команды отчетов создавать отчеты о производительности различных действий консоли SSMA.  
  
### <a name="generate-assessment-report"></a>Создание оценки отчета  
  
Эта команда создает отчеты для оценки на базы данных-источника.  
  
Если подключение к исходной базе данных не выполняется перед выполнением этой команды, выводится сообщение об ошибке и завершает работу консольного приложения.  
  
Не удалось подключиться к исходному серверу базы данных во время выполнения команды также приводит завершение консольного приложения.  
  
-   `conversion-report-folder:`Указывает папку, в котором могут храниться отчета оценки. (необязательно)  
  
-   `object-name:`Указывает один или несколько объектов, для создания отчета оценки (поддерживает имена отдельного объекта или имя объекта группы).  
  
-   `object-type:`Указывает тип объекта, вызванной в атрибуте имя объекта (Если указан объект категория, тип объекта будет «категория»).  
  
-   `conversion-report-overwrite:`Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
-   `write-summary-report-to:`Указывает путь, с которой будет создаваться отчет.  
  
    Если указано только имя папки, сохраните файл с именем **AssessmentReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет два дополнительных раздела:  
  
    -   `report-errors`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
    -   `verbose`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
**Пример синтаксиса:**  
  
```xml  
<generate-assessment-report  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>”             (optional)  
  
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
Команды миграции преобразовать схему целевой базы данных в исходной схеме и переноса данных на целевом сервере.  
  
### <a name="convert-schema"></a>преобразовать схему  
Эта команда выполняет преобразование схемы из источника в целевую схему.  
  
Если подключение к исходной или целевой базе данных не выполняется перед выполнением этой команды или сбой подключения к серверу базы данных источника или целевого объекта во время выполнения команды, формируется сообщение об ошибке и завершает работу консольного приложения.  
  
-   `conversion-report-folder:`Указывает папку, в котором могут храниться отчета оценки. (необязательно)  
  
-   `object-name:`Указывает исходных объектов, для преобразования схемы (поддерживает имена отдельного объекта или имя объекта группы).  
  
-   `object-type:`Указывает тип объекта, вызванной в атрибуте имя объекта (Если указан объект категория, тип объекта будет «категория»).  
  
-   `conversion-report-overwrite:`Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
-   `write-summary-report-to:`Указывает путь, по которому создается сводный отчет.  
  
    Если указано только имя папки, сохраните файл с именем **SchemaConversionReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет два дополнительных раздела:  
  
    -   `report-errors`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
    -   `verbose`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
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
Эта команда перемещает данные источника в целевой объект.  
  
-   `object-name:`Указывает, считается для переноса всех объектов источника данных (поддерживает имена отдельного объекта или имя объекта группы).  
  
-   `object-type:`Указывает тип объекта, вызванной в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `write-summary-report-to:`Указывает путь, с которой будет создаваться отчет.  
  
    Если указано только имя папки, сохраните файл с именем **DataMigrationReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет два дополнительных раздела:  
  
    -   `report-errors`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
    -   `verbose`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
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
  
## <a name="migration-preparation-command"></a>Команда подготовки к миграции  
Подготовка к миграции инициирует схемы сопоставления между исходной и целевой баз данных.  
  
> [!NOTE]  
> Задание для миграции команд вывод на консоль по умолчанию — «Полная» выходные данные отчет с отсутствия сообщений подробные сведения об ошибке: только сводки на корневой узел дерева объекта источника.  
  
### <a name="map-schema"></a>Схема сопоставления  
Эта команда предоставляет сопоставление схемы базы данных-источника в целевую схему.  
  
-   `source-schema`Указывает исходную схему для миграции.  
  
-   `sql-server-schema`Указывает целевую схему, в которую будут перенесены в исходной схеме.  
  
**Пример синтаксиса:**  
  
```xml  
<map-schema source-schema="<source-schema>"  
  
sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-commands"></a>Команды управления  
Команды управляемости помогают синхронизировать объекты целевой базы данных с исходной базой данных.  
  
> [!NOTE]  
> Задание для миграции команд вывод на консоль по умолчанию — «Полная» выходные данные отчет с отсутствия сообщений подробные сведения об ошибке: только сводки на корневой узел дерева объекта источника.  
  
### <a name="synchronize-target"></a>синхронизировать целевой  
Эта команда синхронизирует целевых объектов с целевой базой данных.  
 
Если эта команда выполняется для базы данных-источника, возникает ошибка.  
  
Если подключение к целевой базе данных не выполняется перед выполнением этой команды или подключения базы данных на целевой сервер сбой во время выполнения команды, формируется сообщение об ошибке и завершает работу консольного приложения.  
  
-   `object-name:`Указывает целевых объектов для синхронизации с целевой базой данных (поддерживает имена отдельного объекта или имя объекта группы).  
  
-   `object-type:`Указывает тип объекта, вызванной в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `on-error:`Указывает, следует ли для задания синхронизации ошибки как предупреждения или ошибки. Доступные варианты в случае ошибки:  
  
    -   всего отчета как предупреждения  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
-   `report-errors-to:`Указывает расположение отчет об ошибках для операции синхронизации (необязательно). Если дано путь к папке, сохраните файл с именем **TargetSynchronizationReport.XML** создается.  
  
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
  
Если эта команда выполняется в целевой базе данных, возникнет ошибка.  
  
Эта команда требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:`Указывает источник объектов для обновление из базы данных-источника (поддерживает имена отдельного объекта или имя объекта группы).  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `on-error:`Указывает, следует вызвать ошибки обновления в качестве предупреждения или ошибки. Доступные варианты в случае ошибки:  
  
    -   всего отчета как предупреждения  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
-   `report-errors-to:`Указывает расположение отчет об ошибках для операции обновления (необязательно). Если дано путь к папке, сохраните файл с именем **SourceDBRefreshReport.XML** создается.  
  
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
  
## <a name="script-generation-commands"></a>Создание команд сценария  
Создание скрипта команды выполнения двух задач: они помогают сохранить выходные данные в файле скрипта консоли, и они записывают T-SQL output в консоли или на основе параметра указывается файл.  
  
### <a name="save-as-script"></a>Сохранить как сценарий  
Эта команда используется для сохранения скриптов для объектов в файле упоминалось, когда метабазы = target. Это является альтернативой команды синхронизации, в том, что мы получить скрипты и выполнить соответствует в целевой базе данных.  
  
Эта команда требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:`Указывает один или несколько объектов, которого сценарии должны быть сохранены (поддерживает имена отдельного объекта или имя объекта группы).  
  
-   `object-type:`Указывает тип объекта, вызванной в атрибуте имя объекта (Если указан объект категория, тип объекта будет «категория»).  
  
-   `metabase:`Указывает, является ли источник или целевая метабазы.  
  
-   `destination:`Указывает путь или папка, в которой необходимо сохранить скрипт. Если имя файла не указан, будет указано имя файла в формате (значение атрибута object_name)-out.
  
-   `overwrite:`Если значение равно true, перекрывает тем же именем файла, если он существует. Он может принимать значения (true/false).  
  
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
  
### <a name="convert-sql-statement"></a>оператор CONVERT-sql
Эта команда преобразует инструкции SQL.  
  
-   `context`Задает имя схемы.  
  
-   `destination`Указывает, хранятся ли выходные данные в файле.  
  
    Если этот атрибут не указан, на консоли отображается преобразованный инструкции T-SQL. (необязательно)  
  
-   `conversion-report-folder`Указывает папку, в котором могут храниться отчета оценки. (необязательно)  
  
-   `conversion-report-overwrite`Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
-   `write-converted-sql-to`Указывает путь к папке файла (или) для которого должны храниться преобразованный T-SQL. Если путь к папке указан вместе с `sql-files` атрибут, всех исходных файлов имеет соответствующий целевой объект T-SQL-файла, созданного в указанной папке. Если путь к папке указан вместе с `sql` атрибута, преобразованное T-SQL записываются в файл с именем Result.out в указанной папке.  
  
-   `sql`Задает Sybase инструкции sql для преобразования, можно разделить один или несколько операторов с помощью «;»  
  
-   `sql-files`Указывает путь к файлам sql, который необходимо преобразовать в код T-SQL.  
  
-   `write-summary-report-to`Указывает путь, где будут создаваться сводного отчета. Если указано только имя папки, сохраните файл с именем **ConvertSQLReport.XML** создается. (необязательно)  
  
    Создание сводного отчета имеет два дополнительных подкатегории, а именно:  
  
    -   отчет ошибки (= «true/false», по умолчанию как «false» (необязательные атрибуты)).  
  
    -   verbose (= «true/false», по умолчанию как «false» (необязательные атрибуты)).  
  
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
Сведения о параметрах командной строки см. в разделе [параметры командной строки в консоли SSMA (AccessToSQL)](../access/command-line-options-in-ssma-console-accesstosql.md).  
  
Сведения о консоли образец файла сценария см. в разделе [работа с консоли скрипт образцы файлов &#40; SybaseToSQL &#41;](../../ssma/sybase/working-with-the-sample-console-script-files-sybasetosql.md)  
  
Следующий шаг зависит от требований проекта:  
  
-   Для указания пароля или экспорта / импорта паролей см. в разделе [управление паролями &#40; SybaseToSQL &#41; ](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   Для создания отчетов, в разделе [создания отчетами &#40; SybaseToSQL &#41; ](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   Для устранения неполадок в консоли, в разделе [Устранение неполадок &#40; SybaseToSQL &#41; ](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  
