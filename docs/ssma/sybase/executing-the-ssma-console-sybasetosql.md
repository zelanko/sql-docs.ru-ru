---
description: Выполнение команд консоли SSMA (SybaseToSQL)
title: Запуск консоли SSMA (SybaseToSQL) | Документация Майкрософт
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: fee973fdcb79105d5fe7c412c10bdda2cd1bbec5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88372240"
---
# <a name="executing-the-ssma-console-sybasetosql"></a>Выполнение команд консоли SSMA (SybaseToSQL)
Корпорация Майкрософт предоставляет надежный набор команд для работы с файлами сценариев для выполнения и управления действиями SSMA. Эти разделы подробно описываются.  
  
## <a name="script-file-commands"></a>Команды файла сценария  
Консольное приложение использует определенные стандартные команды файла сценария, перечисленные в этом разделе.  
  
## <a name="project-commands"></a>Команды проекта  
Команды проекта обрабатывали создание проектов, открытие, сохранение и выход из проектов.  
  
### <a name="create-new-project"></a>create-new-project  
Эта команда создает новый проект SSMA.  
  
-   `project-folder` Указывает папку создаваемого проекта.  
  
-   `project-name` Указывает имя проекта. {строка}  
  
-   `overwrite-if-exists`Необязательный атрибут указывает, следует ли перезаписывать существующий проект. логическая  
  
-   `project-type:`Необязательный атрибут. Указывает тип проекта, который является проектом "SQL-Server-2005" или "SQL-Server-2008" или проектом "SQL-Server-2012" или "SQL-Server-2014". Значение по умолчанию — "SQL-Server-2008".  
  
**Пример синтаксиса:**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>" (optional)  
  
   project-type="<sql-server-2008/sql-server-2005/sql-server-2012/sql-server-2014/sql-azure>"  
/>  
```  
Атрибут "overwrite-IF-EXISTS" имеет **значение false** по умолчанию.  
  
По умолчанию атрибут "Project-Type" имеет значение **SQL-Server-2008** .  
  
### <a name="open-project"></a>открыть-проект  
Эта команда открывает проект.

-   `project-folder` Указывает папку создаваемого проекта. Команда завершается ошибкой, если указанная папка не существует.  {строка}  
  
-   `project-name` Указывает имя проекта. Команда завершается ошибкой, если указанный проект не существует.  {строка}  
  
**Пример синтаксиса:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
> [!NOTE]  
> Консольное приложение SSMA для SAP ASE поддерживает обратную совместимость. Его можно использовать для открытия проектов, созданных в предыдущей версии SSMA.  
  
### <a name="save-project"></a>save-project  
Эта команда сохраняет проект миграции.  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
  
### <a name="close-project"></a>закрыть — проект  
Эта команда закрывает проект миграции.  
  
**Пример синтаксиса:**  
  
```xml  
<close-project   
  if-modified="<save/error/ignore>"   (optional)  
/>  
```  
Атрибут "If-Modified" является необязательным, по умолчанию **игнорируется** .  
  
## <a name="database-connection-commands"></a>Команды подключения к базе данных  
Команды подключения к базе данных помогают подключиться к базе данных.  
  
> [!NOTE]  
> - Функция **просмотра** пользовательского интерфейса не поддерживается в консоли.  
> - Дополнительные сведения о создании файлов скриптов см. в разделе [Создание файлов скриптов &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
### <a name="connect-source-database"></a>соединение-источник — база данных  
Эта команда выполняет подключение к базе данных-источнику и загружает метаданные высокого уровня базы данных-источника, но не все метаданные.
  
Если соединение с источником не может быть установлено, создается ошибка и консольное приложение останавливает выполнение.
  
Определение сервера извлекается из атрибута Name, определенного для каждого подключения в разделе Server файла соединения сервера или файла скрипта.  
  
**Пример синтаксиса:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="force-load-sourcetarget-database"></a>Принудительная Загрузка-источник/Целевая база данных  
Эта команда загружает исходные метаданные и полезна для работы над проектом миграции в автономном режиме.  
  
Если не удается установить соединение с источником или назначением, создается ошибка и консольное приложение останавливает выполнение.  
  
Для этой команды требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
**Пример синтаксиса:**  
  
```xml  
<force-load metabase="<source/target>" >  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
  
### <a name="reconnect-source-database"></a>Повторное подключение-источник базы данных  
Эта команда повторно подключается к базе данных-источнику, но не загружает метаданные в отличие от команды Connect-Source-Database.  
  
Если не удается установить соединение с источником, создается ошибка и консольное приложение останавливает выполнение.  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="connect-target-database"></a>соединение с целевым объектом базы данных  
Эта команда подключается к целевой базе данных SQL Server и загружает высокоуровневые метаданные целевой базы данных, но не метаданные полностью.  
  
Если не удается установить соединение с целевым объектом, то создается ошибка и консольное приложение прекращает выполнение.  
  
Определение сервера извлекается из атрибута Name, определенного для каждого подключения в разделе Server файла соединения сервера или файла скрипта.  
  
**Пример синтаксиса:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
  
### <a name="reconnect-target-database"></a>Повторное соединение с целевой базой данных  
  
Эта команда повторно подключается к целевой базе данных, но не загружает метаданные, в отличие от команды Connect-Target-Database.  
  
Если не удается установить соединение с целевым объектом, то создается ошибка, и консольное приложение останавливает выполнение.  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-commands"></a>Команды отчета  
Команды отчета создают отчеты о производительности различных действий консоли SSMA.  
  
### <a name="generate-assessment-report"></a>Создание-Оценка-отчет  
  
Эта команда создает отчеты об оценке в базе данных источника.  
  
Если перед выполнением этой команды соединение с базой данных-источником не выполняется, выдается ошибка и консольное приложение завершает работу.  
  
Не удалось подключиться к исходному серверу базы данных во время выполнения команды, также приведет к прерыванию консольного приложения.  
  
-   `conversion-report-folder:` Указывает папку, в которой может храниться отчет по оценке. (необязательный атрибут)  
  
-   `object-name:` Указывает объекты, которые учитываются при создании отчета оценки (поддерживает отдельные имена объектов или имена объектов групп).  
  
-   `object-type:` Указывает тип объекта, вызываемого в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
-   `conversion-report-overwrite:` Указывает, следует ли перезаписывать папку с отчетом оценки, если она уже существует.  
  
    **Значение по умолчанию:** false. (необязательный атрибут)  
  
-   `write-summary-report-to:` Указывает путь, по которому будет создан отчет.  
  
    Если упоминается только путь к папке, то File by name **ассессментрепорт &lt; n &gt; . Создается XML** . (необязательный атрибут)  
  
    Создание отчета включает еще две подкатегории:  
  
    -   `report-errors` (= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
    -   `verbose` (= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
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
Команды миграции преобразуют схему целевой базы данных в исходную схему и переносят данные на целевой сервер.  
  
### <a name="convert-schema"></a>Convert-Schema  
Эта команда выполняет преобразование схемы из источника в целевую схему.  
  
Если исходное или целевое подключение к базе данных не выполняется перед выполнением этой команды или при сбое подключения к исходному или целевому серверу базы данных во время выполнения команды, возникает ошибка и консольное приложение завершает работу.  
  
-   `conversion-report-folder:` Указывает папку, в которой может храниться отчет по оценке. (необязательный атрибут)  
  
-   `object-name:` Указывает исходные объекты, которые учитываются при преобразовании схемы (поддерживает отдельные имена объектов или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, вызываемого в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
-   `conversion-report-overwrite:` Указывает, следует ли перезаписывать папку с отчетом оценки, если она уже существует.  
  
    **Значение по умолчанию:** false. (необязательный атрибут)  
  
-   `write-summary-report-to:` Указывает путь, по которому будет создан сводный отчет.  
  
    Если упоминается только путь к папке, то File by name **счемаконверсионрепорт &lt; n &gt; . Создается XML** . (необязательный атрибут)  
  
    Создание отчета включает еще две подкатегории:  
  
    -   `report-errors` (= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
    -   `verbose` (= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
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
  
### <a name="migrate-data"></a>Миграция данных  
Эта команда переносит исходные данные в целевой объект.  
  
-   `object-name:` Указывает исходные объекты, рассматриваемые для переноса данных (поддерживает отдельные имена объектов или имена объектов групп).  
  
-   `object-type:` Указывает тип объекта, вызываемого в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
-   `write-summary-report-to:` Указывает путь, по которому будет создан отчет.  
  
    Если упоминается только путь к папке, то File by name **датамигратионрепорт &lt; n &gt; . Создается XML** . (необязательный атрибут)  
  
    Создание отчета включает еще две подкатегории:  
  
    -   `report-errors` (= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
    -   `verbose` (= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
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
Команда подготовки к миграции инициирует сопоставление схемы между исходной и целевой базами данных.  
  
> [!NOTE]  
> Параметр вывода консоли по умолчанию для команд миграции — "полный" выходной отчет без подробных отчетов об ошибках: сводка только на корневом узле дерева исходного объекта.  
  
### <a name="map-schema"></a>Map-Schema  
Эта команда обеспечивает сопоставление схемы базы данных источника с целевой схемой.  
  
-   `source-schema` Указывает исходную схему для переноса.  
  
-   `sql-server-schema` Указывает целевую схему, в которую будет перенесена исходная схема.  
  
**Пример синтаксиса:**  
  
```xml  
<map-schema source-schema="<source-schema>"  
  
sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-commands"></a>Команды управления  
Команды управления помогают синхронизировать объекты целевой базы данных с базой данных источника.  
  
> [!NOTE]  
> Параметр вывода консоли по умолчанию для команд миграции — "полный" выходной отчет без подробных отчетов об ошибках: сводка только на корневом узле дерева исходного объекта.  
  
### <a name="synchronize-target"></a>синхронизировать — целевой объект  
Эта команда синхронизирует целевые объекты с целевой базой данных.  
 
Если эта команда выполняется для базы данных-источника, то возникает ошибка.  
  
Если целевое подключение к базе данных не выполняется до выполнения этой команды или при сбое подключения к целевому серверу базы данных во время выполнения команды, возникает ошибка, и консольное приложение завершает работу.  
  
-   `object-name:` Указывает целевые объекты, которые учитываются при синхронизации с целевой базой данных (поддерживает отдельные имена объектов или имя объекта группы).  
  
-   `object-type:` Указывает тип объекта, вызываемого в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
-   `on-error:` Указывает, следует ли указывать ошибки синхронизации как предупреждения или ошибки. Доступные параметры для On-Error:  
  
    -   отчет-всего-как-предупреждение  
  
    -   отчет — каждое предупреждение  
  
    -   сценарий Fail  
  
-   `report-errors-to:` Указывает расположение отчета об ошибках для операции синхронизации (необязательный атрибут). Если указан только путь к папке, то создается файл с именем **TargetSynchronizationReport.XML** .  
  
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
  
### <a name="refresh-from-database"></a>Обновление из базы данных  
Эта команда обновляет исходные объекты из базы данных.  
  
Если эта команда выполняется для целевой базы данных, создается ошибка.  
  
Для этой команды требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:` Указывает исходные объекты, которые предполагается обновлять из базы данных-источника (поддерживает имена отдельных объектов или имена объектов групп).  
  
-   `object-type:` Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
-   `on-error:` Указывает, следует ли вызывать ошибки обновления как предупреждения или ошибки. Доступные параметры для On-Error:  
  
    -   отчет-всего-как-предупреждение  
  
    -   отчет — каждое предупреждение  
  
    -   сценарий Fail  
  
-   `report-errors-to:` Указывает расположение отчета об ошибках для операции обновления (необязательный атрибут). Если указан только путь к папке, то создается файл с именем **SourceDBRefreshReport.XML** .  
  
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
  
## <a name="script-generation-commands"></a>Команды создания скрипта  
Команды создания скрипта выполняют две задачи: они помогают сохранить выходные данные консоли в файле скрипта и записать выходные данные T-SQL в консоль или файл на основе указанного параметра.  
  
### <a name="save-as-script"></a>Сохранить как сценарий  
Эта команда используется для сохранения скриптов объектов в файл, упоминаемый в метабазе = Target. Это альтернатива команде синхронизации в том, что мы получаем скрипты и исполняем их в целевой базе данных.  
  
Для этой команды требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
-   `object-name:` Указывает объекты, скрипты для которых должны быть сохранены (поддерживает отдельные имена объектов или имена объектов групп).  
  
-   `object-type:` Указывает тип объекта, вызываемого в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
-   `metabase:` Указывает, является ли это исходным или целевым метабазой.  
  
-   `destination:` Указывает путь или папку, в которой должен быть сохранен скрипт. Если имя файла не указано, то используется имя файла в формате (значение атрибута object_name). out будет предоставлено.
  
-   `overwrite:` Если значение — true, то будет перезаписано то же имя файла, если оно существует. Он может иметь значения (true/false).  
  
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
  
### <a name="convert-sql-statement"></a>Convert-SQL-оператор
Эта команда преобразует инструкцию SQL.  
  
-   `context` Указывает имя схемы.  
  
-   `destination` Указывает, должны ли выходные данные храниться в файле.  
  
    Если этот атрибут не указан, преобразованная инструкция T-SQL отображается на консоли. (необязательный атрибут)  
  
-   `conversion-report-folder` Указывает папку, в которой может храниться отчет по оценке. (необязательный атрибут)  
  
-   `conversion-report-overwrite` Указывает, следует ли перезаписывать папку с отчетом оценки, если она уже существует.  
  
    **Значение по умолчанию:** false. (необязательный атрибут)  
  
-   `write-converted-sql-to` Указывает путь к папке файла (или), в которую должен храниться преобразованный T-SQL. Если путь к папке указан вместе с `sql-files` атрибутом, то каждый исходный файл имеет соответствующий целевой файл T-SQL, созданный в указанной папке. Если путь к папке указан вместе с `sql` атрибутом, преобразованный T-SQL записывается в файл с именем result. out в указанной папке.  
  
-   `sql` Указывает инструкции SQL Sybase для преобразования, одну или несколько инструкций можно разделить с помощью ";"  
  
-   `sql-files` Указывает путь к файлам SQL, которые должны быть преобразованы в код T-SQL.  
  
-   `write-summary-report-to` Указывает путь, по которому будет создан сводный отчет. Если упоминается только путь к папке, то создается файл с именем **ConvertSQLReport.XML** . (необязательный атрибут)  
  
    Создание сводного отчета имеет две дополнительные подкатегории, а именно:  
  
    -   отчет — ошибки (= "true/false", по умолчанию — "false" (необязательные атрибуты)).  
  
    -   verbose (= "true/false", значение по умолчанию — "false" (необязательные атрибуты)).  
  
Для этой команды требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
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
  
## <a name="next-steps"></a>Дальнейшие действия  
Сведения о параметрах командной строки см. [в разделе Параметры командной строки в консоли SSMA (акцесстоскл)](../access/command-line-options-in-ssma-console-accesstosql.md).  
  
Сведения о примере файла сценария консоли см. в разделе [Работа с примерами файлов сценариев консоли &#40;SybaseToSQL&#41;](../../ssma/sybase/working-with-the-sample-console-script-files-sybasetosql.md)  
  
Следующий шаг зависит от требований проекта:  
  
-   Сведения об указании пароля или экспорте и импорте паролей см. в статье [Управление паролями &#40;SybaseToSQL&#41;](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   Сведения о создании отчетов см. в разделе [Создание отчетов &#40;SybaseToSQL&#41;](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   Сведения об устранении неполадок в консоли см. в разделе [Устранение неполадок &#40;SybaseToSQL&#41;](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  
