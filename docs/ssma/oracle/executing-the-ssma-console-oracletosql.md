---
title: Выполнение консоли SSMA (OracleToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Oracle SSMA Console
- Script File Commands, Script Generation Commands,Manageability Commands
- Script File Commands,Project Commands
ms.assetid: 7228ccba-c69f-4b4c-8664-01a2750183c5
caps.latest.revision: 43
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 54055f1eb840d6c2160ac04f7713e86f05859a28
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="executing-the-ssma-console-oracletosql"></a>Выполнение консоли SSMA (OracleToSQL)
Корпорация Майкрософт предоставляет широкий набор сценариев файл команд для выполнения и контроля над SSMA действий. В консольном приложении используется определенных команд файла стандартный сценарий как перечисленные в этом разделе.  
  
## <a name="project-script-file-commands"></a>Команд файла скрипта проекта  
Дескриптор команды проекта, создание проектов, открытие, сохранение и выход из проектов.  
  
**Command**  
  
Создание нового проекта  
                  : Создает новый проект SSMA.  
  
**Скрипт**  
  
-   `project-folder` Указывает папку проект, созданный в начало.  
  
-   `project-name` Указывает имя проекта. {Строка}  
  
-   `overwrite-if-exists`Необязательный атрибут указывает, должны ли перезаписываться существующий проект. {значение типа boolean}  
  
-   `project-type:`Необязательный атрибут. Указывает проекта типа т. е. «sql server 2005» проекта или проекта «sql server 2008» или «sql server 2012» проекта или проекта «sql server 2014» или «sql azure». Значение по умолчанию — «sql server 2014».  
  
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
  
Атрибут «тип проекта» **sql server 2008** по умолчанию.  
  
**Command**  
  
открыть проект: открытие существующего проекта.  
  
**Скрипт**  
  
-   `project-folder` Указывает папку проект, созданный в начало. Команда завершается ошибкой, если указанная папка не существует.  {Строка}  
  
-   `project-name` Указывает имя проекта. Команда завершается ошибкой, если указанный проект не существует.  {Строка}  
  
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
  
Сохранение проекта миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
Закрытие проекта  
  
Закрытие проекта миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<close-project  
  
   if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
  
## <a name="database-connection-script-file-commands"></a>Команд файла скрипта подключения базы данных  
Команды подключения к базе данных позволяют подключать к базе данных.  
  
-   **Обзор** компонент пользовательского интерфейса не поддерживается в консоли.  
  
-   Дополнительные сведения о «Создание файлов скриптов» в разделе [Создание файлов скриптов &#40;OracleToSQL&#41;](../../ssma/oracle/creating-script-files-oracletosql.md).  
  
**Command**  
  
подключения--базы данных источника  
  
-   Выполняет подключение к базе данных источника и загружает высокой метаданных уровня базы данных-источника, но не все метаданные.  
  
-   Если не удается установить подключение к источнику, возникнет ошибка, и консольного приложения дальнейшей останавливает выполнение  
  
**Скрипт**  
  
Определение сервера извлекается из атрибута name, определенных для каждого соединения в разделе сервер файла подключения сервера или файла скрипта.  
  
**Пример синтаксиса:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
Force нагрузки-/ target-базы данных источника  
  
-   Загружает метаданные источника.  
  
-   Это полезно для работы над проектом миграции в автономном режиме.  
  
-   Если не удается установить соединение с исходной или целевой, возникает ошибка, и консольного приложения дальнейшей останавливает выполнение  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
**Пример синтаксиса:**  
  
```xml  
<force-load object-name="<object-name>"  
  
  metabase="<source/target>"/>  
```  
либо  
  
```xml  
<force-load>  
  
   <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Command**  
  
повторное подключение--базы данных источника  
  
-   Выполняет повторное подключение к исходной базе данных, но не загружает все метаданные, в отличие от команды Подключение исходной базы данных.  
  
-   Если не удается установить (соединение с источником re), возникнет ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
подключения target-базы данных  
  
-   Подключается к целевой базе данных SQL Server и полностью загружает высокой метаданных уровня целевой базы данных, но не метаданные.  
  
-   Если не удается установить подключение к целевому объекту, возникает ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
**Скрипт**  
  
Определение сервера извлекается из атрибута name, определенных для каждого соединения в разделе сервер файла подключения сервера или файла скрипта  
  
**Пример синтаксиса:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
повторное подключение target-базы данных  
  
-   Выполняет повторное подключение к целевой базе данных, но не загружает все метаданные, в отличие от команды подключение целевой базы данных.  
  
-   Если не удается установить (подключение к целевому объекту re), возникнет ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file--commands"></a>Команды файл скрипта отчетов  
Команды отчетов создавать отчеты о производительности различных действий консоли SSMA.  
  
**Command**  
  
Создание оценки отчета  
  
-   Создает отчеты для оценки на базы данных-источника.  
  
-   Если подключение к исходной базе данных не выполняется перед выполнением этой команды, выводится сообщение об ошибке и завершает работу консольного приложения.  
  
-   Не удалось подключиться к исходному серверу базы данных во время выполнения команды также приводит завершение консольного приложения.  
  
**Скрипт**  
  
-   `conversion-report-folder:` Указывает папку, где возможно отчета оценки для сохранения. (необязательно)  
  
-   `object-name:` Указывает один или несколько объектов, для создания отчета оценки (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `conversion-report-overwrite:` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
-   `write-summary-report-to:` Указывает путь, где будут создаваться сводного отчета.  
  
    Если указано только имя папки, сохраните файл с именем **AssessmentReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные вложенные категории:  
  
    -   `report-errors` (= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
    -   `verbose` (= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
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
либо  
  
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
  
Задание для миграции команд вывод на консоль по умолчанию — «Полная» выходные данные отчет с отсутствия сообщений подробные сведения об ошибке: только сводки на корневой узел дерева объекта источника.  
  
**Command**  
  
преобразовать схему  
  
-   Выполняет преобразование схемы из источника в целевую схему.  
  
-   Если подключение к исходной или целевой базе данных не выполняется перед выполнением этой команды или сбой подключения к серверу базы данных источника или целевого объекта во время выполнения команды, формируется сообщение об ошибке и завершает работу консольного приложения.  
  
**Скрипт**  
  
-   `conversion-report-folder:` Указывает папку, где возможно отчета оценки для сохранения. (необязательно)  
  
-   `object-name:` Указывает источник объектов для преобразования схемы (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `conversion-report-overwrite:` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
-   `write-summary-report-to:` Указывает путь, где будут создаваться сводного отчета.  
  
    Если указано только имя папки, сохраните файл с именем **SchemaConversionReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные вложенные категории:  
  
    -   `report-errors` (= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
    -   `verbose` (= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
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
либо  
  
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
  
Переносит данные источника в целевой объект.  
  
**Скрипт**  
  
-   `conversion-report-folder:` Указывает папку, где возможно отчета оценки для сохранения. (необязательно)  
  
-   `object-name:` Указывает, считается для переноса всех объектов источника данных (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `conversion-report-overwrite:` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
-   `write-summary-report-to:` Указывает путь, где будут создаваться сводного отчета.  
  
    Если указано только имя папки, сохраните файл с именем **DataMigrationReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные вложенные категории:  
  
    -   `report-errors` (= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
    -   `verbose` (= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
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
либо  
  
```xml  
<migrate-data  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   report-errors="<true/false>"  
  
   verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-script-file-commands"></a>Команды файл скрипта подготовки к миграции  
Подготовка к миграции инициирует схемы сопоставления между исходной и целевой баз данных.  
  
**Command**  
  
map-schema  
  
Сопоставление схемы базы данных-источника в целевую схему.  
  
Переносит данные источника в целевой объект.  
  
**Скрипт**  
  
-   `source-schema` Указывает в исходной схеме, которую мы собираемся миграции.  
  
-   `sql-server-schema` Указывает целевую схему, где нам это нужно для миграции.  
  
**Пример синтаксиса:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>Команды файл сценария управляемости  
Команды управляемости помогают синхронизировать объекты целевой базы данных с исходной базой данных. Задание для миграции команд вывод на консоль по умолчанию — «Полная» выходные данные отчет с отсутствия сообщений подробные сведения об ошибке: только сводки на корневой узел дерева объекта источника.  
  
**Command**  
  
синхронизировать целевой  
  
-   Синхронизирует целевых объектов с целевой базы данных.  
  
-   Если эта команда выполняется для базы данных-источника, возникает ошибка.  
  
-   Если подключение к целевой базе данных не выполняется перед выполнением этой команды или подключения базы данных на целевой сервер сбой во время выполнения команды, формируется сообщение об ошибке и завершает работу консольного приложения.  
  
**Скрипт**  
  
-   `object-name:` Указывает целевых объектов для синхронизации с целевой базой данных (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `on-error:` Указывает, следует ли для задания синхронизации ошибки как предупреждения или ошибки. Доступные варианты в случае ошибки:  
  
    -   всего отчета как предупреждения  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
-   `report-errors-to:` Указывает расположение для отчета об ошибке для операции синхронизации (необязательно) Если дано путь к папке, затем по имени **TargetSynchronizationReport.XML** создается.  
  
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
**Command**  
  
обновление из базы данных  
  
-   Обновляет объекты из базы данных-источника.  
  
-   Если эта команда выполняется в целевой базе данных, возникнет ошибка.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:` Указывает источник объектов для обновление из базы данных-источника (он может иметь имена отдельных объектов или имя объекта групповой).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `on-error:` Указывает, следует ли для указания ошибок как предупреждения или ошибки. Доступные варианты в случае ошибки:  
  
    -   всего отчета как предупреждения  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
-   `report-errors-to:` Указывает расположение для отчета об ошибке для операции обновления (необязательно) Если дано путь к папке, затем по имени **SourceDBRefreshReport.XML** создается.  
  
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
либо  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"/>  
```  
либо  
  
```xml  
<refresh-from-database>  
  
   <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>Команды файл скрипта создания сценариев  
Создание скрипта команды выполнения двух задач: они помогают сохранить выходные данные в файл скрипта; консоли и запись вывода на консоль или файл, на основе параметра, указываемые T-SQL.  
  
**Command**  
  
Сохранить как сценарий  
  
Используется для сохранения скриптов для объектов в файл, когда упомянутые метабазы = цель, это является альтернативой команды синхронизации, которому мы получения сценариев и выполнение соответствует в целевой базе данных.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:` Указывает один или несколько объектов, чьи сценарии должны быть сохранены. (Он может иметь имена отдельных объектов или имя объекта групповой)  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `metabase:` Указывает, является ли он ithe исходной или целевой метабазы.  
  
-   `destination:` Указывает путь или папка, где сценарий должен быть сохранен, если имя файла не задан, выберите имя файла в-out-формат (значение атрибута object_name)  
  
-   `overwrite:` Если значение true, затем он переопределяет Если существует такое же имя файла. Он может принимать значения (true/false).  
  
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
либо  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   destination="<file/folder>"  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</save-as-script>  
```  
**Command**  
  
оператор CONVERT-sql  
  
-   `context` Задает имя схемы.  
  
-   `destination` Указывает, хранятся ли выходные данные в файле.  
  
    Если этот атрибут не указан, на консоли отображается преобразованный инструкции T-SQL. (необязательно)  
  
-   `conversion-report-folder` Указывает папку, где возможно отчета оценки для сохранения. (необязательно)  
  
-   `conversion-report-overwrite` Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
-   `write-converted-sql-to` Указывает путь к папке, где будет храниться преобразованный T-SQL, файл (или). Если путь к папке указан вместе с `sql-files` атрибут, каждый исходный файл будет иметь соответствующий целевой объект T-SQL-файла, созданного в указанной папке. Если путь к папке указан вместе с `sql` атрибута, преобразованное T-SQL записываются в файл с именем **Result.out** в указанной папке.  
  
-   `sql` Задает инструкции sql Oracle должны преобразовываться один или несколько операторов могут быть объединенные с помощью «;»  
  
-   `sql-files` Указывает путь к файлам sql, который необходимо преобразовать в код T-SQL.  
  
-   `write-summary-report-to` Указывает путь, где будет создан отчет. Если указано только имя папки, сохраните файл с именем **ConvertSQLReport.XML** создается. (необязательно)  
  
    Создания имеет 2 viz Далее подкатегорий, отчет.:  
  
    -   отчет ошибки (= «true/false», по умолчанию как «false» (необязательные атрибуты)).  
  
    -   verbose (= «true/false», по умолчанию как «false» (необязательные атрибуты)).  
  
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
либо  
  
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
либо  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   sql-files="<folder-name>\*.sql" />  
```  
  
## <a name="next-step"></a>Следующий шаг  
Сведения о параметрах командной строки см. в разделе [параметры командной строки в консоли SSMA &#40;OracleToSQL&#41; ](../../ssma/oracle/command-line-options-in-ssma-console-oracletosql.md) .  
  
Сведения о файлах сценария образец консоли, в разделе [работа с файлами скриптов образца консоли &#40;OracleToSQL&#41;](../../ssma/oracle/working-with-the-sample-console-script-files-oracletosql.md)  
  
Следующий шаг зависит от требований проекта:  
  
-   Для указания пароля или экспорта / импорта паролей см. в разделе [управление паролями &#40;OracleToSQL&#41;](../../ssma/oracle/managing-passwords-oracletosql.md).  
  
-   Для создания отчетов, в разделе [создания отчетами &#40;OracleToSQL&#41;](../../ssma/oracle/generating-reports-oracletosql.md).  
  
-   Для устранения неполадок в консоли, в разделе [Устранение неполадок &#40;OracleToSQL&#41;](../../ssma/oracle/troubleshooting-oracletosql.md).  
  
