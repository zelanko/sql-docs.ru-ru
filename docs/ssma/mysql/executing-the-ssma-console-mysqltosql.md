---
title: "Выполнение консоли SSMA (MySQLToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-mysql
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
helpviewer_keywords:
- Script file commands, Database connection commands
- Script file commands, Manageability commands
- Script file commands, Migration commands
- Script file commands, Migration preparation commands
- Script file commands, project commands
- Script file commands, Report commands
- Script file commands, Script generation commands
ms.assetid: e3e9f7e4-0619-4861-a202-3d5d39953b26
caps.latest.revision: "25"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 39b41addf566e326174a004a210a2ba2b1cdf311
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="executing-the-ssma-console-mysqltosql"></a>Выполнение консоли SSMA (MySQLToSQL)
Корпорация Майкрософт предоставляет широкий набор сценариев файл команд для выполнения и контроля над SSMA действий.  
  
В консольном приложении используется определенных команд файла стандартный сценарий как перечисленные в этом разделе.  
  
## <a name="project--script-file-commands"></a>Команд файла скрипта проекта  
**Command**  
  
Создание нового проекта:   
                   Создание нового проекта SSMA.  
  
Дескриптор команды проекта, создание проектов, открытие, сохранение и выход из проектов.  
  
**Скрипт**  
  
1.  `project-folder`Указывает папку проект, созданный в начало.  
  
2.  `project-name`Указывает имя проекта. {Строка}  
  
3.  `overwrite-if-exists`Необязательный атрибут указывает, должны ли перезаписываться существующий проект. {значение типа boolean}  
  
4.  `project-type:`Необязательный атрибут. Указывает тип проекта т. е. «sql server 2005» проекта или проекта «sql server 2008» или «sql server 2012» или «sql server 2014» проекта или проект «sql azure». По умолчанию — «sql server 2008».  
  
**Пример синтаксиса:**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type==”<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>”   (optional)  
  
/>  
```  
Атрибут «перезаписать if-exists» **false** по умолчанию.  
  
Атрибут «тип проекта» **sql server 2008** по умолчанию.  
  
**Command**  
  
открыть проект:   
                  Открывает существующий проект.  
  
**Скрипт**  
  
1.  `project-folder`Указывает папку проект, созданный в начало. Команда завершается ошибкой, если указанная папка не существует.  {Строка}  
  
2.  `project-name`Указывает имя проекта. Команда завершается ошибкой, если указанный проект не существует.  {Строка}  
  
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
  
проект сохранить: сохраняет проекта миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
Закрытие проекта  
                  : Закрывает проекта миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
Закрытие проекта  
                  : Закрывает проекта миграции.  
  
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
  
1.  **Обзор** компонент пользовательского интерфейса не поддерживается в консоли.  
  
2.  **Проверки подлинности windows** и **порт** параметры не применяются при подключении к SQL Azure.  
  
3.  Дополнительные сведения о «Создание файлов скриптов» в разделе [Создание файлов скриптов &#40; MySQLToSQL &#41; ](../../ssma/mysql/creating-script-files-mysqltosql.md).  
  
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
<force-load metabase="<source/target>"  
  
      <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Command**  
  
повторное подключение--базы данных источника  
  
1.  Выполняет повторное подключение к исходной базе данных, но не загружает все метаданные, в отличие от команды Подключение исходной базы данных.  
  
2.  Если не удается установить (соединение с источником re), возникнет ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
подключения target-базы данных  
  
1.  Подключается к базе данных назначения SQL Server или SQL Azure и полностью загружает высокой метаданных уровня целевой базы данных, но не метаданные.  
  
2.  Если не удается установить подключение к целевому объекту, возникает ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
**Скрипт**  
  
Определение сервера извлекается из атрибута name, определенных для каждого соединения в разделе сервер файла подключения сервера или файла скрипта  
  
**Пример синтаксиса:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
повторное подключение target-базы данных  
  
1.  Выполняет повторное подключение к целевой базе данных, но не загружает все метаданные, в отличие от команды подключение целевой базы данных.  
  
2.  Если не удается установить (подключение к целевому объекту re), возникнет ошибка, и консольного приложения дальнейшей останавливает выполнение.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>Команды файл скрипта отчетов  
Команды отчетов создавать отчеты о производительности различных действий консоли SSMA.  
  
**Command**  
  
Создание оценки отчета  
  
1.  Создает отчеты для оценки на базы данных-источника.  
  
2.  Если подключение к исходной базе данных не выполняется перед выполнением этой команды, выводится сообщение об ошибке и завершает работу консольного приложения.  
  
3.  Не удалось подключиться к исходному серверу базы данных во время выполнения команды также приводит завершение консольного приложения.  
  
**Скрипт**  
  
1.  `assessment-report-folder:`Указывает папку, где возможно отчета оценки для сохранения. (необязательно)  
  
2.  `object-name:`Указывает один или несколько объектов, для создания отчета оценки (он может иметь имена отдельных объектов или имя объекта групповой).  
  
3.  `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
4.  `assessment-report-overwrite:`Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
5.  `write-summary-report-to:`Указывает путь, где будут создаваться сводного отчета.  
  
    Если указано только имя папки, сохраните файл с именем **AssessmentReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные вложенные категории:  
  
    -   `report-errors`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
    -   `verbose`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
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
  
## <a name="migration--script-file-commands"></a>Команды файл сценария миграции  
Команды миграции преобразовать схему целевой базы данных в исходной схеме и переносит данные на целевой сервер.  
  
Задание для миграции команд вывод на консоль по умолчанию — «Полная» выходные данные отчет с отсутствия сообщений подробные сведения об ошибке: только сводки на корневой узел дерева объекта источника.  
  
**Command**  
  
преобразовать схему  
  
1.  Выполняет преобразование схемы из источника в целевую схему.  
  
2.  Если подключение к исходной или целевой базе данных не выполняется перед выполнением этой команды или сбой подключения к серверу базы данных источника или целевого объекта во время выполнения команды, формируется сообщение об ошибке и завершает работу консольного приложения.  
  
**Скрипт**  
  
1.  `conversion-report-folder:`Указывает папку, где возможно отчета оценки для сохранения. (необязательно)  
  
2.  `object-name:`Указывает один или несколько объектов, для преобразования схемы (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
3.  `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
4.  `conversion-report-overwrite:`Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
5.  `write-summary-report-to:`Указывает путь, где будут создаваться сводного отчета.  
  
    Если указано только имя папки, сохраните файл с именем **SchemaConversionReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание сводного отчета имеет две дополнительные вложенные категории:  
  
    -   `report-errors`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
    -   `verbose`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
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
  
      <metabase-object object-name="<object-names>"  
  
         object-type="<object-category>"/>  
  
</convert-schema>  
```  
**Command**  
  
Перенос данных  
  
1.  Переносит данные источника в целевой объект.  
  
**Скрипт**  
  
1.  `object-name:`Указывает, считается для переноса всех объектов источника данных (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
2.  `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
3.  `write-summary-report-to:`Указывает путь, где будут создаваться сводного отчета.  
  
    Если указано только имя папки, сохраните файл с именем **DataMigrationReport&lt;n&gt;. XML** создается. (необязательно)  
  
    Создание отчета имеет две дополнительные вложенные категории:  
  
    -   `report-errors`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
    -   `verbose`(= «true/false», по умолчанию как «false» (необязательные атрибуты))  
  
**Пример синтаксиса:**  
  
```xml  
<migrate-data  
  
   write-summary-report-to="<file-name/folder-name>”  
  
   report-errors="true" verbose="true">  
  
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
  
   write-summary-report-to="<file-name/folder-name>”  
  
   report-errors="true" verbose="true"/>  
```  
  
## <a name="migration-preparation-script-file-command"></a>Подготовка сценария миграции файл-команда  
Подготовка к миграции инициирует схемы сопоставления между исходной и целевой баз данных.  
  
**Command**  
  
Схема сопоставления  
  
Сопоставление схемы базы данных-источника в целевую схему.  
  
**Скрипт**  
  
1.  `source-schema`Указывает в исходной схеме, которую мы собираемся миграции.  
  
2.  `sql-server-schema`Указывает целевую схему, где нам это нужно для миграции.  
  
**Пример синтаксиса:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>Команды файл сценария управляемости  
Команды управляемости помогают синхронизировать объекты целевой базы данных с исходной базой данных.  
  
> [!NOTE]  
> Задание для миграции команд вывод на консоль по умолчанию — «Полная» выходные данные отчет с отсутствия сообщений подробные сведения об ошибке: только сводки на корневой узел дерева объекта источника.  
  
**Command**  
  
синхронизировать целевой  
  
1.  Синхронизирует целевых объектов с целевой базы данных.  
  
2.  Если эта команда выполняется для базы данных-источника, возникает ошибка.  
  
3.  Если подключение к целевой базе данных не выполняется перед выполнением этой команды или подключения базы данных на целевой сервер сбой во время выполнения команды, формируется сообщение об ошибке и завершает работу консольного приложения.  
  
**Скрипт**  
  
1.  `object-name:`Указывает один или несколько объектов, для синхронизации с целевой базой данных (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
2.  `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
3.  `on-error:`Указывает, следует ли для задания синхронизации ошибки как предупреждения или ошибки. Доступные варианты в случае ошибки:  
  
    -   всего отчета как предупреждения  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
4.  `report-errors-to:`Указывает расположение для отчета об ошибке для операции синхронизации (необязательно) Если дано путь к папке, затем по имени **TargetSynchronizationReport.XML** создается.  
  
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
  
1.  Обновляет объекты из базы данных-источника.  
  
2.  Если эта команда выполняется в целевой базе данных, возникнет ошибка.  
  
**Скрипт**  
  
1.  `object-name:`Указывает источник объектов для обновление из базы данных-источника (он может иметь имена пометку отдельных объектов или имя объекта групповой).  
  
2.  `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
3.  `on-error:`Указывает, следует ли для задания синхронизации ошибки как предупреждения или ошибки. Доступные варианты в случае ошибки:  
  
    -   всего отчета как предупреждения  
  
    -   отчет each как предупреждение  
  
    -   Сбой скрипта  
  
4.  `report-errors-to:`Указывает расположение для отчета об ошибке для операции синхронизации (необязательно) Если дано путь к папке, затем по имени **SourceDBRefreshReport.XML** создается.  
  
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
  
1.  `object-name:`Указывает один или несколько объектов, чьи сценарии должны быть сохранены. (Он может иметь имена пометку отдельных объектов или имя объекта групповой)  
  
2.  `object-type:`Указывает тип объекта, указанного в атрибуте имя объекта (если категории объекта указан тип объекта будет «категория»).  
  
3.  `metabase:`Указывает, является ли источник или целевая метабазы.  
  
4.  `destination:`Указывает путь или папка, где сценарий должен быть сохранен, если имя файла не задан, выберите имя файла в-out-формат (значение атрибута object_name)  
  
5.  `overwrite:`Если значение true, затем он переопределяет Если существует такое же имя файла. Он может принимать значения (true/false).  
  
**Пример синтаксиса:**  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   destination="<file-name/folder-name>”  
  
   overwrite="<true/false>"   (optional)  
  
/>  
```  
либо  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   destination="<file-name/folder-name>”  
  
      <metabase-object object-name="<object-name>"  
  
            object-type="<object-category>"/>  
  
</save-as-script>  
```  
**Command**  
  
оператор CONVERT-sql  
  
1.  `context`Задает имя схемы.  
  
2.  `destination`Указывает, хранятся ли выходные данные в файле.  
  
    Если этот атрибут не указан, на консоли отображается преобразованный инструкции T-SQL. (необязательно)  
  
3.  `conversion-report-folder`Указывает папку, где возможно отчета оценки для сохранения. (необязательно)  
  
4.  `conversion-report-overwrite`Указывает, следует ли перезаписать папку отчета оценки, если он уже существует.  
  
    **Значение по умолчанию:** значение false. (необязательно)  
  
5.  `write-converted-sql-to`Указывает путь к папке, где будет храниться преобразованный T-SQL, файл (или). Если путь к папке указан вместе с `sql-files` атрибут, каждый исходный файл будет иметь соответствующий целевой объект T-SQL-файла, созданного в указанной папке. Если путь к папке указан вместе с `sql` атрибута, преобразованное T-SQL записываются в файл с именем Result.out в указанной папке.  
  
6.  `sql`Задает инструкции sql MySQL для преобразования, один или несколько операторов могут быть объединенные с помощью «;»  
  
7.  `sql-files`Указывает путь к файлам sql, который необходимо преобразовать в код T-SQL.  
  
8.  `write-summary-report-to`Указывает путь, где будут создаваться сводного отчета. Если указано только имя папки, сохраните файл с именем **ConvertSQLReport.XML** создается. (необязательно)  
  
    Отчетов, создания имеет 2 далее подкатегорий, viz..,:  
  
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
  
   destination="stdout/file"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
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
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="<stdout/file>"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql-files="<folder-name>\*.sql"  
  
/>  
```  
либо  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-step"></a>Следующий шаг  
Сведения о параметрах командной строки см. в разделе [параметры командной строки в консоли SSMA &#40; MySQLToSQL &#41; ](../../ssma/mysql/command-line-options-in-ssma-console-mysqltosql.md) .  
  
Дополнительные сведения о файлах сценария образец консоли, в разделе [работа с консоли скрипт образцы файлов &#40; MySQLToSQL &#41;](../../ssma/mysql/working-with-the-sample-console-script-files-mysqltosql.md)  
  
Следующий шаг зависит от требований проекта:  
  
1.  Для указания пароля или экспорта / импорта паролей см. в разделе [управление паролями &#40; MySQLToSQL &#41; ](../../ssma/mysql/managing-passwords-mysqltosql.md).  
  
2.  Для создания отчетов, в разделе [создания отчетами &#40; MySQLToSQL &#41; ](../../ssma/mysql/generating-reports-mysqltosql.md).  
  
3.  Для устранения неполадок в консоли, в разделе [Устранение неполадок &#40; MySQLToSQL &#41; ](../../ssma/mysql/troubleshooting-mysqltosql.md).  
  
