---
title: "Выполнение консоли SSMA (SybaseToSQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
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
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0df634087870db32ed0357c97b1211d4fc1ddcba
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="executing-the-ssma-console-sybasetosql"></a>Выполнение консоли SSMA (SybaseToSQL)
Корпорация Майкрософт предоставляет широкий набор сценариев файл команд для выполнения и контроля над SSMA действий. В последующих разделах подробно одинаковыми.  
  
## <a name="script-file-commands"></a>Команды сценария файла  
В консольном приложении используется определенных команд файла стандартный сценарий как перечисленные в этом разделе.  
  
## <a name="project-commands"></a>Проект команды  
Дескриптор команды проекта, создание проектов, открытие, сохранение и выход из проектов.  
  
### <a name="create-new-project"></a>Создание нового проекта  
Создает новый проект SSMA  
  
-   `project-folder`Указывает папку проект, созданный в начало.  
  
-   `project-name`Указывает имя проекта. {Строка}  
  
-   `overwrite-if-exists`Необязательный атрибут указывает, должны ли перезаписываться существующий проект. {значение типа boolean}  
  
-   `project-type:`Необязательный атрибут. Указывает тип проекта т. е. «sql server 2005» проекта или проекта «sql server 2008» или проект «sql server 2012» или «sql server 2014» проекта или проекта «sql azure». По умолчанию — «sql server 2008».  
  
**Пример:**  
  
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
> SSMA для Sybase консольное приложение поддерживает обратную совместимость. Можно открывать проекты, созданные в предыдущей версии SSMA.  
  
### <a name="save-project"></a>Сохранение проекта  
Сохраняет проект миграции  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
  
### <a name="close-project"></a>Закрытие проекта  
Закрытие проекта миграции  
  
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
> 1.  **Обзор** компонент пользовательского интерфейса не поддерживается в консоли.  
> 2.  Дополнительные сведения о «Создание файлов скриптов» в разделе [Создание файлов скриптов &#40; SybaseToSQL &#41; ](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
### <a name="connect-source-database"></a>подключения--базы данных источника  
  
-   Выполняет подключение к базе данных источника и загружает высокой метаданных уровня базы данных-источника, но не все метаданные.  
  
-   Если не удается установить подключение к источнику, возникнет ошибка, и консольного приложения дальнейшей останавливает выполнение  
  
Определение сервера извлекается из атрибута name, определенных для каждого соединения в разделе сервер файла подключения сервера или файла скрипта.  
  
**Пример синтаксиса:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="force-load-sourcetarget-database"></a>Force нагрузки-/ target-базы данных источника  
  
-   Загружает метаданные источника.  
  
-   Это полезно для работы над проектом миграции в автономном режиме.  
  
-   Если не удается установить соединение с исходной или целевой, возникает ошибка, и консольного приложения дальнейшей останавливает выполнение  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
**Пример синтаксиса:**  
  
```xml  
<force-load metabase=”<source/target>” >  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
  
### <a name="reconnect-source-database"></a>повторное подключение--базы данных источника  
  
-   Выполняет повторное подключение к исходной базе данных, но не загружает все метаданные, в отличие от команды Подключение исходной базы данных.  
  
-   Если не удается установить (соединение с источником re), возникнет ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="connect-target-database"></a>подключения target-базы данных  
  
-   Подключается к целевой базе данных SQL Server и полностью загружает высокой метаданных уровня целевой базы данных, но не метаданные.  
  
-   Если не удается установить подключение к целевому объекту, возникает ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
Определение сервера извлекается из атрибута name, определенных для каждого соединения в разделе сервер файла подключения сервера или файла скрипта  
  
**Пример синтаксиса:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
  
### <a name="reconnect-target-database"></a>повторное подключение target-базы данных  
  
-   Выполняет повторное подключение к целевой базе данных, но не загружает все метаданные, в отличие от команды подключение целевой базы данных.  
  
-   Если не удается установить (подключение к целевому объекту re), возникнет ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-commands"></a>Команды отчета  
Команды отчетов создавать отчеты о производительности различных действий консоли SSMA.  
  
### <a name="generate-assessment-report"></a>Создание оценки отчета  
  
-   Создает отчеты для оценки на базы данных-источника.  
  
-   Если подключение к исходной базе данных не выполняется перед выполнением этой команды, выводится сообщение об ошибке и завершает работу консольного приложения.  
  
-   Не удалось подключиться к исходному серверу базы данных во время выполнения команды также приводит завершение консольного приложения.  
  
-   `conversion-report-folder:`Указывает папку, где возможно отчета оценки для сохранения. (необязательно)  
  
-   `object-name:`Указывает один или несколько объектов, для создания отчета оценки (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `conversion-report-overwrite:`Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
-   `write-summary-report-to:`Указывает путь, где будет создан отчет.  
  
    Если указано только имя папки, сохраните файл с именем **AssessmentReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные вложенные категории:  
  
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
либо  
  
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
Команды миграции преобразовать схему целевой базы данных в исходной схеме и переносит данные на целевой сервер.  
  
### <a name="convert-schema"></a>преобразовать схему  
  
-   Выполняет преобразование схемы из источника в целевую схему.  
  
-   Если подключение к исходной или целевой базе данных не выполняется перед выполнением этой команды или сбой подключения к серверу базы данных источника или целевого объекта во время выполнения команды, формируется сообщение об ошибке и завершает работу консольного приложения.  
  
-   `conversion-report-folder:`Указывает папку, где возможно отчета оценки для сохранения. (необязательно)  
  
-   `object-name:`Указывает источник объектов для преобразования схемы (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `conversion-report-overwrite:`Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
-   `write-summary-report-to:`Указывает путь, где будут создаваться сводного отчета.  
  
    Если указано только имя папки, сохраните файл с именем **SchemaConversionReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные вложенные категории:  
  
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
либо  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder-name>"         (optional)  
  
  conversion-report-overwrite="<true/false>"> (optional)  
  
  <metabase-object object-name="<object-name>"  
  
    object-type="<object-category>"/>  
  
</convert-schema>  
```  
  
### <a name="migrate-data"></a>Перенос данных  
Переносит данные источника в целевой объект.  
  
-   `object-name:`Указывает, считается для переноса всех объектов источника данных (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `write-summary-report-to:`Указывает путь, где будет создан отчет.  
  
    Если указано только имя папки, сохраните файл с именем **DataMigrationReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные вложенные категории:  
  
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
либо  
  
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
Сопоставление схемы базы данных-источника в целевую схему.  
  
-   `source-schema`Указывает в исходной схеме, которую мы собираемся миграции.  
  
-   `sql-server-schema`Указывает целевую схему, где нам это нужно для миграции.  
  
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
  
-   Синхронизирует целевых объектов с целевой базы данных.  
  
-   Если эта команда выполняется для базы данных-источника, возникает ошибка.  
  
-   Если подключение к целевой базе данных не выполняется перед выполнением этой команды или подключения базы данных на целевой сервер сбой во время выполнения команды, формируется сообщение об ошибке и завершает работу консольного приложения.  
  
-   `object-name:`Указывает целевых объектов для синхронизации с целевой базой данных (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `on-error:`Указывает, следует ли для задания синхронизации ошибки как предупреждения или ошибки. Доступные варианты в случае ошибки:  
  
    -   всего отчета как предупреждения  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
-   `report-errors-to:`Указывает расположение для отчета об ошибке для операции синхронизации (необязательно) Если дано путь к папке, затем по имени **TargetSynchronizationReport.XML** создается.  
  
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
либо  
  
```xml  
<synchronize-target  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"/>  
```  
либо  
  
```xml  
<synchronize-target>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
</synchronize-target>  
```  
  
### <a name="refresh-from-database"></a>обновление из базы данных  
  
-   Обновляет объекты из базы данных-источника.  
  
-   Если эта команда выполняется в целевой базе данных, возникнет ошибка.  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:`Указывает источник объектов для обновление из базы данных-источника (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `on-error:`Указывает, следует ли для указания ошибок как предупреждения или ошибки. Доступные варианты в случае ошибки:  
  
    -   всего отчета как предупреждения  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
-   `report-errors-to:`Указывает расположение для отчета об ошибке для операции обновления (необязательно) Если дано путь к папке, затем по имени **SourceDBRefreshReport.XML** создается.  
  
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
либо  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  object-type="<object-category>" />  
```  
либо  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-commands"></a>Создание команд сценария  
Создание скрипта команды выполнения двух задач: они помогают сохранить выходные данные в файл скрипта; консоли и запись вывода на консоль или файл, на основе параметра, указываемые T-SQL.  
  
### <a name="save-as-script"></a>Сохранить как сценарий  
Используется для сохранения скриптов для объектов в файл, когда упомянутые метабазы = цель, это является альтернативой команды синхронизации, которому мы получения сценариев и выполнение соответствует в целевой базе данных.  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:`Указывает один или несколько объектов, чьи сценарии должны быть сохранены. (Он может иметь имена пометку отдельных объектов или имя объекта групповой)  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `metabase:`Указывает, является ли он ithe исходной или целевой метабазы.  
  
-   `destination:`Указывает путь или папка, где сценарий должен быть сохранен, если имя файла не задан, выберите имя файла в-out-формат (значение атрибута object_name)  
  
-   `overwrite:`Если значение true, затем он переопределяет Если существует такое же имя файла. Он может принимать значения (true/false).  
  
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
либо  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file-name/folder-name>"  
  
    <metabase-object object-name="<object-name>"  
  
                     object-type="<object-category>"/>  
  
</save-as-script>  
```  
  
### <a name="convert-sql-statement"></a>оператор CONVERT-sql  
  
-   `context`Задает имя схемы.  
  
-   `destination`Указывает, хранятся ли выходные данные в файле.  
  
    Если этот атрибут не указан, на консоли отображается преобразованный инструкции T-SQL. (необязательно)  
  
-   `conversion-report-folder`Указывает папку, где возможно отчета оценки для сохранения. (необязательно)  
  
-   `conversion-report-overwrite`Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
-   `write-converted-sql-to`Указывает путь к папке, где будет храниться преобразованный T-SQL, файл (или). Если путь к папке указан вместе с `sql-files` атрибут, каждый исходный файл будет иметь соответствующий целевой объект T-SQL-файла, созданного в указанной папке. Если путь к папке указан вместе с `sql` атрибута, преобразованное T-SQL записываются в файл с именем Result.out в указанной папке.  
  
-   `sql`Задает инструкции sql Sybase должны преобразовываться один или несколько операторов могут быть объединенные с помощью «;»  
  
-   `sql-files`Указывает путь к файлам sql, который необходимо преобразовать в код T-SQL.  
  
-   `write-summary-report-to`Указывает путь, где будут создаваться сводного отчета. Если указано только имя папки, сохраните файл с именем **ConvertSQLReport.XML** создается. (необязательно)  
  
    Создание имеет 2 viz Далее подкатегорий, сводный отчет..,:  
  
    -   отчет ошибки (= «true/false», по умолчанию как «false» (необязательные атрибуты)).  
  
    -   verbose (= «true/false», по умолчанию как «false» (необязательные атрибуты)).  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
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
либо  
  
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
либо  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-step"></a>Следующий шаг  
Сведения о параметрах командной строки см. в разделе [параметры командной строки в консоли SSMA &#40; SybaseToSQL &#41; ](../../ssma/sybase/command-line-options-in-ssma-console-sybasetosql.md) .  
  
Сведения о консоли файла сценария см. в разделе [работа с консоли скрипт образцы файлов &#40; SybaseToSQL &#41;](../../ssma/sybase/working-with-the-sample-console-script-files-sybasetosql.md)  
  
Следующий шаг зависит от требований проекта:  
  
-   Для указания пароля или экспорта / импорта паролей см. в разделе [управление паролями &#40; SybaseToSQL &#41; ](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   Для создания отчетов, в разделе [создания отчетами &#40; SybaseToSQL &#41; ](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   Для устранения неполадок в консоли, в разделе [Устранение неполадок &#40; SybaseToSQL &#41; ](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  

