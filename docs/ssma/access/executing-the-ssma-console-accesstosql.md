---
title: "Выполнение консоли SSMA (AccessToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: aa1bf665-8dc0-4259-b36f-46ae67197a43
caps.latest.revision: "25"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3d749a876fb128f55e653eca6fe8dda613a09dfa
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="executing-the-ssma-console-accesstosql"></a>Выполнение консоли SSMA (AccessToSQL)
Майкрософт предоставляет широкий набор команд файла скрипта и параметры командной строки для выполнения и контроля над SSMA действий. В последующих разделах подробно одинаковыми.  
  
## <a name="project--script-file-commands"></a>Команд файла скрипта проекта  
Дескриптор команды проекта, создание проектов, открытие, сохранение и выход из проектов.  
  
**Command**  
  
Создание new-project: создает новый проект SSMA.  
  
**Скрипт**  
  
-   `project-folder`Указывает папку проект, созданный в начало.  
  
-   `project-name`Указывает имя проекта. {Строка}  
  
-   `overwrite-if-exists`Необязательный атрибут указывает, должны ли перезаписываться существующий проект. {значение типа boolean}  
  
-   `project-type`— Это необязательный атрибут.  Следующие параметры доступны для типа проекта.  
  
    -   SQL server 2005  
  
    -   SQL server 2008  
  
    -   SQL server 2012  
  
    -   SQL server 2014  
  
    -   SQL server 2016  
  
    -   SQL azure  
  
    По умолчанию — «sql server 2008».  
  
**Пример:**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>"  
  
  project-type=”<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>”  
  
/>  
```  
Атрибут «перезаписать if-exists» **false** по умолчанию.  
  
Атрибут «тип проекта» **sql server 2008** по умолчанию.  
  
**Command**  
  
открыть проект: открытие существующего проекта.  
  
**Скрипт**  
  
-   `project-folder`Указывает папку проект, созданный в начало. Команда завершается ошибкой, если указанная папка не существует.  {Строка}  
  
-   `project-name`Указывает имя проекта. Команда завершается ошибкой, если указанный проект не существует.  {Строка}  
  
**Пример синтаксиса:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
**Примечание:** поддерживает приложение консоли SSMA для обеспечения обратной совместимости. Можно открывать проекты, созданные в предыдущей версии SSMA.  
  
**Command**  
  
проект сохранить: сохраняет проекта миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
Закрыть проект: закрывает проекта миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<close-project  
  
  if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
Атрибут «if-modified» является необязательным, **игнорировать** по умолчанию.  
  
## <a name="database-connection-script-file-commands"></a>Команд файла скрипта подключения базы данных  
Команды подключения к базе данных позволяют подключать к базе данных.  
  
**Обзор** компонент пользовательского интерфейса не поддерживается в консоли.  
  
**Проверки подлинности windows** и **порт** параметры не применяются при подключении к SQL Azure.  
  
Дополнительные сведения о «Создание файлов скриптов» в разделе [Создание файлов скриптов &#40; AccessToSQL &#41; ](../../ssma/access/creating-script-files-accesstosql.md).  
  
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
  
База данных access нагрузки: для загрузки файлов баз данных access  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<load-access-database  database-file="<Access-database>"/>  
```  
либо  
  
```xml  
<load-access-database>  
  
  <access-database database-file="<Access-database1>"/>  
  
  <access-database database-file="<Access-database2>"/>  
  
</load-access-database>  
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
<force-load  
  
  object-name="<object-name>"  
  
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
  
-   Подключается к базе данных назначения SQL Server или SQL Azure и полностью загружает высокой метаданных уровня целевой базы данных, но не метаданные.  
  
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
  
## <a name="report-script-file-commands"></a>Команды файл скрипта отчетов  
Команды отчетов создавать отчеты о производительности различных действий консоли SSMA.  
  
**Command**  
  
Создание оценки отчета  
  
-   Создает отчеты для оценки на базы данных-источника.  
  
-   Если подключение к исходной базе данных не выполняется перед выполнением этой команды, выводится сообщение об ошибке и завершает работу консольного приложения.  
  
-   Не удалось подключиться к исходному серверу базы данных во время выполнения команды также приводит завершение консольного приложения.  
  
**Скрипт**  
  
-   `assessment-report-folder:`Указывает папку, где возможно отчета оценки для сохранения. (необязательно)  
  
-   `object-name:`Указывает один или несколько объектов, для создания отчета оценки (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `assessment-report-overwrite:`Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
-   `write-summary-report-to:`Указывает путь, где будет создан отчет.  
  
    Если указано только имя папки, сохраните файл с именем **AssessmentReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные вложенные категории:  
  
    -   `report-errors`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
    -   `verbose`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
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
либо  
  
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
  
Задание для миграции команд вывод на консоль по умолчанию — «Полная» выходные данные отчет с отсутствия сообщений подробные сведения об ошибке: только сводки на корневой узел дерева объекта источника.  
  
**Command**  
  
преобразовать схему  
  
-   Выполняет преобразование схемы из источника в целевую схему.  
  
-   Если подключение к исходной или целевой базе данных не выполняется перед выполнением этой команды или сбой подключения к серверу базы данных источника или целевого объекта во время выполнения команды, формируется сообщение об ошибке и завершает работу консольного приложения.  
  
**Скрипт**  
  
-   `conversion-report-folder:`Указывает папку для хранения отчета оценки. (необязательно)  
  
-   `object-name:`Указывает источник объектов для преобразования схемы (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `conversion-report-overwrite:`Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
-   `write-summary-report-to:`Указывает путь, где будет создан отчет.  
  
    Если указано только имя папки, сохраните файл с именем **SchemaConversionReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные вложенные категории:  
  
    -   `report-errors`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
    -   `verbose`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
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
либо  
  
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
  
1.  Переносит данные источника в целевой объект.  
  
**Скрипт**  
  
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
либо  
  
```xml  
<migrate-data  
  
  object-name="ssma.Tables"  
  
  object-type="category"  
  
  write-summary-report-to="<filepath/folder>"  
  
  report-errors="true" verbose="true"/>  
```  
**Command**  
  
связь с таблицами: Эта команда связывает таблицу источника (Access) целевой таблицы.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<link-tables>  
  
  <metabase-object object-name="AccessDatabase.table1" object-type="Tables"/>  
  
  <metabase-object object-name="AccessDatabase.table2" object-type="Tables"/>  
  
</link-tables>  
```  
либо  
  
```xml  
<link-tables>  
  
  <metabase-object object-name="AccessDatabase.Tables" object-type="category"/>  
  
</link-tables>  
```  
**Command**  
  
удалить связь таблиц: Эта команда удаляет связь в таблице источника (доступ) из целевой таблицы.  
  
**Скрипт**  
  
**Примеры синтаксиса.**  
  
```xml  
<unlink-tables>  
  
  <metabase-object object-name="AccessDatabase.table1" object-type="Tables"/>  
  
  <metabase-object object-name="AccessDatabase.table2" object-type="Tables"/>  
  
</unlink-tables>  
```  
либо  
  
```xml  
<unlink-tables>  
  
  <metabase-object object-name="AccessDatabase.Tables" object-type="category"/>  
  
</unlink-tables>  
```  
  
## <a name="migration-preparation-script-file-commands"></a>Команды файл скрипта подготовки к миграции  
Подготовка к миграции инициирует схемы сопоставления между исходной и целевой баз данных.  
  
**Command**  
  
Схема сопоставления: сопоставление схемы базы данных-источника в целевую схему.  
  
**Скрипт**  
  
-   `source-schema`Указывает в исходной схеме, которую мы собираемся миграции.  
  
-   `sql-server-schema`Указывает целевую схему, где нам это нужно для миграции.  
  
**Пример синтаксиса:**  
  
```xml  
<map-schema source-schema="source-schema"  
  
            sql-server-schema="target-schema"/>  
```  
  
## <a name="manageability-commands"></a>Команды управления  
Команды управляемости помогают синхронизировать объекты целевой базы данных с исходной базой данных.  
  
Задание для миграции команд вывод на консоль по умолчанию — «Полная» выходные данные отчет с отсутствия сообщений подробные сведения об ошибке: только сводки на корневой узел дерева объекта источника.  
  
**Command**  
  
синхронизировать целевой  
  
1.  Синхронизирует целевых объектов с целевой базы данных.  
  
2.  Если эта команда выполняется для базы данных-источника, возникает ошибка.  
  
3.  Если подключение к целевой базе данных не выполняется перед выполнением этой команды или подключения базы данных на целевой сервер сбой во время выполнения команды, формируется сообщение об ошибке и завершает работу консольного приложения.  
  
**Скрипт**  
  
1.  `object-name:`Указывает целевых объектов для синхронизации с целевой базой данных (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
2.  `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
3.  `on-error:`Указывает, следует ли для задания синхронизации ошибки как предупреждения или ошибки. Доступные варианты в случае ошибки:  
  
    -   всего отчета как предупреждения  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
4.  `report-errors-to:`Указывает расположение для отчета об ошибке для операции синхронизации (необязательно) Если дано путь к папке, затем по имени **TargetSynchronizationReport.XML** создается.  
  
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
либо  
  
```xml  
<synchronize-target  
  
  object-name="ssma.dbo.Procedures"  
  
  object-type="category"/>  
```  
либо  
  
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
  
-   Если эта команда выполняется в целевой базе данных, возникнет ошибка.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
1.  `object-name:`Указывает источник объектов для обновление из базы данных-источника (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
2.  `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
3.  `on-error:`Указывает, следует ли для указания ошибок как предупреждения или ошибки. Доступные варианты в случае ошибки:  
  
    -   всего отчета как предупреждения  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
4.  `report-errors-to:`Указывает расположение для отчета об ошибке для операции обновления (необязательно) Если дано путь к папке, затем по имени **SourceDBRefreshReport.XML** создается.  
  
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
либо  
  
```xml  
<refresh-from-database  
  
  object-name="ssma.Procedures"  
  
  object-type="category"/>  
```  
либо  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="ssma.TT_1"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>Команды файл скрипта создания сценариев  
Создание скрипта, помочь команды сохранить выходные данные в консоли в файле скрипта.  
  
**Command**  
  
Сохранить как сценарий  
  
Используется для сохранения скриптов для объектов в файл, когда упомянутые метабазы = цель, это является альтернативой команды синхронизации, которому мы получения сценариев и выполнение соответствует в целевой базе данных.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:`Указывает один или несколько объектов, чьи сценарии должны быть сохранены. (Он может иметь имена отдельных объектов или имя объекта групповой)  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
-   `metabase:`Указывает, является ли источник или целевая метабазы.  
  
-   `destination:`Указывает путь или папка, где сценарий должен быть сохранен, если имя файла не задан, выберите имя файла в-out-формат (значение атрибута object_name)  
  
-   `overwrite:`Если значение true, затем он переопределяет Если существует такое же имя файла. Он может принимать значения (true/false).  
  
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
либо  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file/folder>"  
  
    <metabase-object object-name="ssma.dbo.Procedures"  
  
                     object-type="category"/>  
  
</save-as-script>  
```  
  
## <a name="next-step"></a>Следующий шаг  
Сведения о параметрах командной строки см. в разделе [параметры командной строки в консоли SSMA &#40; AccessToSQL &#41; ](../../ssma/access/command-line-options-in-ssma-console-accesstosql.md) .  
  
На файлы скриптов образца консоли Подробнее [работа с FilesExecuting сценария образец консоли консоли SSMA &#40; AccessToSQL &#41;](../../ssma/access/working-sample-console-script-filesexecuting-ssma-console-accesstosql.md)  
  
Следующий шаг зависит от требований проекта:  
  
-   Для указания пароля или экспорта / импорта паролей см. в разделе [управление паролями &#40; AccessToSQL &#41; ](../../ssma/access/managing-passwords-accesstosql.md).  
  
-   Для создания отчетов, в разделе [создания отчетами &#40; AccessToSQL &#41; ](../../ssma/access/generating-reports-accesstosql.md).  
  
-   Для устранения неполадок в консоли, в разделе [Устранение неполадок &#40; AccessToSQL &#41; ](../../ssma/access/troubleshooting-accesstosql.md).  
  
