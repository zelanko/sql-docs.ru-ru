---
title: Запуск консоли SSMA (Акцесстоскл) | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68006572"
---
# <a name="executing-the-ssma-console-accesstosql"></a>Запуск консоли SSMA (Акцесстоскл)
Корпорация Майкрософт предоставляет надежный набор команд для работы с файлами сценариев и команд командной строки для выполнения и управления действиями SSMA. Эти разделы подробно описываются.  
  
## <a name="project--script-file-commands"></a>Команды файла скрипта проекта  
Команды проекта обрабатывали создание проектов, открытие, сохранение и выход из проектов.  
  
**Command**  
  
Create-New-Project: создает новый проект SSMA.  
  
**Скрипт**  
  
-   `project-folder`Указывает папку создаваемого проекта.  
  
-   `project-name`Указывает имя проекта. {строка}  
  
-   `overwrite-if-exists`Необязательный атрибут указывает, следует ли перезаписывать существующий проект. логическая  
  
-   `project-type`является необязательным атрибутом.  Для типа проекта доступны следующие параметры:  
  
    -   SQL-Server — 2005  
  
    -   SQL-Server — 2008  
  
    -   SQL-Server — 2012  
  
    -   SQL-Server — 2014  
  
    -   SQL-Server — 2016  
  
    -   SQL — Azure  
  
    Значение по умолчанию — "SQL-Server-2008".  
  
**Пример.**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>"  
  
  project-type="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>"  
  
/>  
```  
Атрибут "overwrite-IF-EXISTS" имеет **значение false** по умолчанию.  
  
По умолчанию атрибут "Project-Type" имеет значение **SQL-Server-2008** .  
  
**Command**  
  
открыть — проект: открывает существующий проект.  
  
**Скрипт**  
  
-   `project-folder`Указывает папку создаваемого проекта. Команда завершается ошибкой, если указанная папка не существует.  {строка}  
  
-   `project-name`Указывает имя проекта. Команда завершается ошибкой, если указанный проект не существует.  {строка}  
  
**Пример синтаксиса:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
**Примечание.** SSMA для консольного приложения Access поддерживает обратную совместимость. Вы сможете открывать проекты, созданные в предыдущей версии SSMA.  
  
**Command**  
  
Save-Project: сохраняет проект миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
закрыть — проект: закрывает проект миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<close-project  
  
  if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
Атрибут "If-Modified" является необязательным, по умолчанию **игнорируется** .  
  
## <a name="database-connection-script-file-commands"></a>Команды файла сценария подключения к базе данных  
Команды подключения к базе данных помогают подключиться к базе данных.  
  
Функция **просмотра** пользовательского интерфейса не поддерживается в консоли.  
  
Параметры **проверки подлинности Windows** и **портов** неприменимы при подключении к SQL Azure.  
  
Дополнительные сведения о создании файлов скриптов см. в разделе [Создание файлов скриптов &#40;акцесстоскл&#41;](../../ssma/access/creating-script-files-accesstosql.md).  
  
**Command**  
  
соединение-источник — база данных  
  
-   Выполняет подключение к базе данных источника и загружает метаданные высокого уровня базы данных источника, но не все метаданные.  
  
-   Если соединение с источником не может быть установлено, создается ошибка и консольное приложение останавливает выполнение.  
  
**Скрипт**  
  
Определение сервера извлекается из атрибута Name, определенного для каждого подключения в разделе Server файла соединения сервера или файла скрипта.  
  
**Пример синтаксиса:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
Загрузка-доступ к базе данных: используется для загрузки файлов базы данных Access  
  
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
  
Принудительная Загрузка-источник/Целевая база данных  
  
-   Загружает исходные метаданные.  
  
-   Полезно для работы над проектом миграции в автономном режиме.  
  
-   Если не удается установить соединение с источником или назначением, создается ошибка и консольное приложение останавливает выполнение.  
  
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
  
Повторное подключение-источник базы данных  
  
-   Повторно подключается к базе данных-источнику, но не загружает метаданные в отличие от команды Connect-Source-Database.  
  
-   Если не удается установить соединение с источником, создается ошибка и консольное приложение останавливает выполнение.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
соединение с целевым объектом базы данных  
  
-   Подключается к целевой SQL Server или SQL Azure базе данных и загружает метаданные высокого уровня целевой базы данных, но не метаданные полностью.  
  
-   Если не удается установить соединение с целевым объектом, то создается ошибка и консольное приложение прекращает выполнение.  
  
**Скрипт**  
  
Определение сервера извлекается из атрибута Name, определенного для каждого подключения в разделе Server файла подключения к серверу или файла скрипта.  
  
**Пример синтаксиса:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
Повторное соединение с целевой базой данных  
  
-   Повторно подключается к целевой базе данных, но не загружает метаданные, в отличие от команды Connect-Target-Database.  
  
-   Если не удается установить соединение с целевым объектом, то создается ошибка, и консольное приложение останавливает выполнение.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>Команды файла скрипта отчета  
Команды отчета создают отчеты о производительности различных действий консоли SSMA.  
  
**Command**  
  
Создание-Оценка-отчет  
  
-   Создает отчеты об оценке в базе данных источника.  
  
-   Если перед выполнением этой команды соединение с базой данных-источником не выполняется, выдается ошибка и консольное приложение завершает работу.  
  
-   Не удалось подключиться к исходному серверу базы данных во время выполнения команды, также приведет к прерыванию консольного приложения.  
  
**Скрипт**  
  
-   `assessment-report-folder:`Указывает папку, в которой может храниться отчет по оценке. (необязательный атрибут)  
  
-   `object-name:`Указывает объекты, которые учитываются при создании отчета оценки (они могут иметь имена объектов отдельных или имена объектов групп).  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
-   `assessment-report-overwrite:`Указывает, следует ли перезаписывать папку с отчетом оценки, если она уже существует.  
  
    **Значение по умолчанию:** false. (необязательный атрибут)  
  
-   `write-summary-report-to:`Указывает путь, по которому будет создан отчет.  
  
    Если упоминается только путь к папке, то File by name **ассессментрепорт&lt;n&gt;. Создается XML** . (необязательный атрибут)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors`(= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
    -   `verbose`(= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
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
  
## <a name="migration-script-file-commands"></a>Команды файла сценария миграции  
Команды миграции преобразуют схему целевой базы данных в исходную схему и переносят данные на целевой сервер.  
  
Параметр вывода консоли по умолчанию для команд миграции — "полный" выходной отчет без подробных отчетов об ошибках: сводка только на корневом узле дерева исходного объекта.  
  
**Command**  
  
Convert-Schema  
  
-   Выполняет преобразование схемы из источника в целевую схему.  
  
-   Если исходное или целевое подключение к базе данных не выполняется перед выполнением этой команды или при сбое подключения к исходному или целевому серверу базы данных во время выполнения команды, возникает ошибка и консольное приложение завершает работу.  
  
**Скрипт**  
  
-   `conversion-report-folder:`Указывает папку, в которой можно хранить отчет по оценке. (необязательный атрибут)  
  
-   `object-name:`Указывает исходные объекты, рассматриваемые для преобразования схемы (у нее могут быть имена объектов отдельных или имя объекта группы).  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
-   `conversion-report-overwrite:`Указывает, следует ли перезаписывать папку с отчетом оценки, если она уже существует.  
  
    **Значение по умолчанию:** false. (необязательный атрибут)  
  
-   `write-summary-report-to:`Указывает путь, по которому будет создан отчет.  
  
    Если упоминается только путь к папке, то File by name **счемаконверсионрепорт&lt;n&gt;. Создается XML** . (необязательный атрибут)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors`(= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
    -   `verbose`(= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
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
  
Миграция данных  
  
1.  Переносит исходные данные в целевой объект.  
  
**Скрипт**  
  
-   `object-name:`Указывает исходные объекты, которые учитываются при переносе данных (они могут иметь имена объектов отдельных или имена объектов групп).  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
-   `write-summary-report-to:`Указывает путь, по которому будет создан отчет.  
  
    Если упоминается только путь к папке, то File by name **датамигратионрепорт&lt;n&gt;. Создается XML** . (необязательный атрибут)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors`(= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
    -   `verbose`(= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
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
  
Link-Tables: Эта команда связывает исходную таблицу (Access) с целевой таблицей.  
  
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
  
несвязанные таблицы: Эта команда отменяет связь исходной таблицы (Access) с целевой таблицей.  
  
**Скрипт**  
  
**Примеры синтаксиса:**  
  
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
  
## <a name="migration-preparation-script-file-commands"></a>Команды файла сценария подготовки миграции  
Команда подготовки к миграции инициирует сопоставление схемы между исходной и целевой базами данных.  
  
**Command**  
  
Map-Schema: сопоставление схемы исходной базы данных с целевой схемой.  
  
**Скрипт**  
  
-   `source-schema`Указывает исходную схему, которую планируется перенести.  
  
-   `sql-server-schema`Указывает целевую схему, в которой требуется перенести ее.  
  
**Пример синтаксиса:**  
  
```xml  
<map-schema source-schema="source-schema"  
  
            sql-server-schema="target-schema"/>  
```  
  
## <a name="manageability-commands"></a>Команды управления  
Команды управления помогают синхронизировать объекты целевой базы данных с базой данных источника.  
  
Параметр вывода консоли по умолчанию для команд миграции — "полный" выходной отчет без подробных отчетов об ошибках: сводка только на корневом узле дерева исходного объекта.  
  
**Command**  
  
синхронизировать — целевой объект  
  
1.  Синхронизирует целевые объекты с целевой базой данных.  
  
2.  Если эта команда выполняется для базы данных-источника, то возникает ошибка.  
  
3.  Если целевое подключение к базе данных не выполняется до выполнения этой команды или при сбое подключения к целевому серверу базы данных во время выполнения команды, возникает ошибка, и консольное приложение завершает работу.  
  
**Скрипт**  
  
1.  `object-name:`Указывает целевые объекты, которые учитываются при синхронизации с целевой базой данных (у нее могут быть имена объектов отдельных или имя объекта группы).  
  
2.  `object-type:`Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
3.  `on-error:`Указывает, следует ли указывать ошибки синхронизации как предупреждения или ошибки. Доступные параметры для On-Error:  
  
    -   отчет-всего-как-предупреждение  
  
    -   отчет — каждое предупреждение  
  
    -   сценарий Fail  
  
4.  `report-errors-to:`Указывает расположение отчета об ошибках для операции синхронизации (необязательный атрибут), если указан только путь к папке, а затем создается файл с именем **таржетсинчронизатионрепорт. XML** .  
  
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
  
Обновление из базы данных  
  
-   Обновляет исходные объекты из базы данных.  
  
-   Если эта команда выполняется для целевой базы данных, создается ошибка.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
1.  `object-name:`Указывает исходные объекты, которые предполагается обновлять из базы данных-источника (они могут иметь имена объектов отдельных или имена объектов групп).  
  
2.  `object-type:`Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
3.  `on-error:`Указывает, следует ли указывать ошибки обновления как предупреждения или ошибки. Доступные параметры для On-Error:  
  
    -   отчет-всего-как-предупреждение  
  
    -   отчет — каждое предупреждение  
  
    -   сценарий Fail  
  
4.  `report-errors-to:`Указывает расположение отчета об ошибках для операции обновления (необязательный атрибут), если указан только путь к папке, а затем создается файл с именем **саурцедбрефрешрепорт. XML** .  
  
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
  
## <a name="script-generation-script-file-commands"></a>Команды файла сценария создания скрипта  
Команды создания скрипта помогают сохранить выходные данные консоли в файле скрипта.  
  
**Command**  
  
Сохранить как сценарий  
  
Используется для сохранения скриптов объектов в файл, упоминаемый в метабазе, который указан в параметре MetaBase = Target. это альтернатива команде синхронизации, в которой мы получаем сценарии и выполняющими те же операции в целевой базе данных.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:`Указывает объекты, скрипты для которых должны быть сохранены. (У него могут быть имена отдельных объектов или имя объекта группы).  
  
-   `object-type:`Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
-   `metabase:`Указывает, является ли это исходным или целевым метабазой.  
  
-   `destination:`Указывает путь или папку, в которой должен быть сохранен скрипт, если имя файла не указано, затем имя файла в формате (object_name значение атрибута). out  
  
-   `overwrite:`Если задано значение true, он перезаписывается, если такое же имя файла существует. Он может иметь значения (true/false).  
  
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
Сведения о параметрах командной строки см. [в разделе Параметры командной строки в консоли SSMA &#40;акцесстоскл&#41;](../../ssma/access/command-line-options-in-ssma-console-accesstosql.md) .  
  
Сведения о примерах файлов сценариев консоли см. в разделе [Работа с примером консольного сценария Филесексекутинг консоли SSMA &#40;акцесстоскл&#41;](../../ssma/access/working-sample-console-script-filesexecuting-ssma-console-accesstosql.md)  
  
Следующий шаг зависит от требований проекта:  
  
-   Сведения об указании пароля или экспорте и импорте паролей см. в статье [Управление паролями &#40;акцесстоскл&#41;](../../ssma/access/managing-passwords-accesstosql.md).  
  
-   Сведения о создании отчетов см. в разделе [Создание отчетов &#40;акцесстоскл&#41;](../../ssma/access/generating-reports-accesstosql.md).  
  
-   Сведения об устранении неполадок в консоли см. в разделе [Устранение неполадок &#40;акцесстоскл&#41;](../../ssma/access/troubleshooting-accesstosql.md).  
  
