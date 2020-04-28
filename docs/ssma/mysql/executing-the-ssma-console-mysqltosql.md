---
title: Запуск консоли SSMA (MySQLToSQL) | Документация Майкрософт
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
ms.openlocfilehash: 239ba5021363be583572d5d24887233261e359cc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "76909694"
---
# <a name="executing-the-ssma-console-mysqltosql"></a>Выполнение команд консоли SSMA (MySQLToSQL)
Корпорация Майкрософт предоставляет надежный набор команд для работы с файлами сценариев для выполнения и управления действиями SSMA.  
  
Консольное приложение использует определенные стандартные команды файла сценария, перечисленные в этом разделе.  
  
## <a name="project--script-file-commands"></a>Команды файла скрипта проекта  
**Command**  
  
Create-New-Project:   
                   Создает новый проект SSMA.  
  
Команды проекта обрабатывали создание проектов, открытие, сохранение и выход из проектов.  
  
**Скрипт**  
  
1.  `project-folder`Указывает папку создаваемого проекта.  
  
2.  `project-name`Указывает имя проекта. {строка}  
  
3.  `overwrite-if-exists`Необязательный атрибут указывает, следует ли перезаписывать существующий проект. логическая  
  
4.  `project-type:`Необязательный атрибут. Указывает тип проекта, т. е. проект SQL-Server-2005 или проект SQL-Server-2008 или проект SQL-Server-2012 или SQL-Server-2014. Значение по умолчанию — "SQL-Server-2008".  
  
**Пример синтаксиса:**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type=="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>"   (optional)  
  
/>  
```  
Атрибут "overwrite-IF-EXISTS" имеет **значение false** по умолчанию.  
  
По умолчанию атрибут "Project-Type" имеет значение **SQL-Server-2008** .  
  
**Command**  
  
открыть-проект:   
                  Открывает существующий проект.  
  
**Скрипт**  
  
1.  `project-folder`Указывает папку создаваемого проекта. Команда завершается ошибкой, если указанная папка не существует.  {строка}  
  
2.  `project-name`Указывает имя проекта. Команда завершается ошибкой, если указанный проект не существует.  {строка}  
  
**Пример синтаксиса:**  
  
```xml  
<open-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
/>  
```  
> [!IMPORTANT]  
> SSMA для консольного приложения MySQL поддерживает обратную совместимость. Вы сможете открывать проекты, созданные в предыдущей версии SSMA.  
  
**Command**  
  
Save-Project: сохраняет проект миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
закрыть — проект  
                  : Закрывает проект миграции.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
закрыть — проект  
                  : Закрывает проект миграции.  
  
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
  
1.  Функция **просмотра** пользовательского интерфейса не поддерживается в консоли.  
  
2.  Параметры **проверки подлинности Windows** и **портов** неприменимы при подключении к SQL Azure.  
  
3.  Дополнительные сведения о создании файлов скриптов см. в разделе [Создание файлов скриптов &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-script-files-mysqltosql.md).  
  
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
  
Принудительная Загрузка-источник/Целевая база данных  
  
-   Загружает исходные метаданные.  
  
-   Полезно для работы над проектом миграции в автономном режиме.  
  
-   Если не удается установить соединение с источником или назначением, создается ошибка и консольное приложение останавливает выполнение.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
**Пример синтаксиса:**  
  
```xml  
<force-load metabase="<source/target>"  
  
      <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Command**  
  
Повторное подключение-источник базы данных  
  
1.  Повторно подключается к базе данных-источнику, но не загружает метаданные в отличие от команды Connect-Source-Database.  
  
2.  Если не удается установить соединение с источником, создается ошибка и консольное приложение останавливает выполнение.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
соединение с целевым объектом базы данных  
  
1.  Подключается к целевой SQL Server или SQL Azure базе данных и загружает метаданные высокого уровня целевой базы данных, но не метаданные полностью.  
  
2.  Если не удается установить соединение с целевым объектом, то создается ошибка и консольное приложение прекращает выполнение.  
  
**Скрипт**  
  
Определение сервера извлекается из атрибута Name, определенного для каждого подключения в разделе Server файла подключения к серверу или файла скрипта.  
  
**Пример синтаксиса:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
Повторное соединение с целевой базой данных  
  
1.  Повторно подключается к целевой базе данных, но не загружает метаданные, в отличие от команды Connect-Target-Database.  
  
2.  Если не удается установить соединение с целевым объектом, то создается ошибка, и консольное приложение останавливает выполнение.  
  
**Скрипт**  
  
**Пример синтаксиса:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>Команды файла скрипта отчета  
Команды отчета создают отчеты о производительности различных действий консоли SSMA.  
  
**Command**  
  
Создание-Оценка-отчет  
  
1.  Создает отчеты об оценке в базе данных источника.  
  
2.  Если перед выполнением этой команды соединение с базой данных-источником не выполняется, выдается ошибка и консольное приложение завершает работу.  
  
3.  Не удалось подключиться к исходному серверу базы данных во время выполнения команды, также приведет к прерыванию консольного приложения.  
  
**Скрипт**  
  
1.  `assessment-report-folder:`Указывает папку, в которой может храниться отчет по оценке. (необязательный атрибут)  
  
2.  `object-name:`Указывает объекты, которые учитываются при создании отчета оценки (у него могут быть имена отдельных объектов или имя объекта группы).  
  
3.  `object-type:`Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
4.  `assessment-report-overwrite:`Указывает, следует ли перезаписывать папку с отчетом оценки, если она уже существует.  
  
    **Значение по умолчанию:** false. (необязательный атрибут)  
  
5.  `write-summary-report-to:`Указывает путь, по которому будет создан сводный отчет.  
  
    Если упоминается только путь к папке, то File by name **ассессментрепорт&lt;n&gt;. Создается XML** . (необязательный атрибут)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors`(= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
    -   `verbose`(= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
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
  
## <a name="migration--script-file-commands"></a>Команды файла сценария миграции  
Команды миграции преобразуют схему целевой базы данных в исходную схему и переносят данные на целевой сервер.  
  
Параметр вывода консоли по умолчанию для команд миграции — "полный" выходной отчет без подробных отчетов об ошибках: сводка только на корневом узле дерева исходного объекта.  
  
**Command**  
  
Convert-Schema  
  
1.  Выполняет преобразование схемы из источника в целевую схему.  
  
2.  Если исходное или целевое подключение к базе данных не выполняется перед выполнением этой команды или при сбое подключения к исходному или целевому серверу базы данных во время выполнения команды, возникает ошибка и консольное приложение завершает работу.  
  
**Скрипт**  
  
1.  `conversion-report-folder:`Указывает папку, в которой может храниться отчет по оценке. (необязательный атрибут)  
  
2.  `object-name:`Указывает объекты, которые учитываются при преобразовании схемы (у нее могут быть имена объектов отдельных или имя объекта группы).  
  
3.  `object-type:`Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
4.  `conversion-report-overwrite:`Указывает, следует ли перезаписывать папку с отчетом оценки, если она уже существует.  
  
    **Значение по умолчанию:** false. (необязательный атрибут)  
  
5.  `write-summary-report-to:`Указывает путь, по которому будет создан сводный отчет.  
  
    Если упоминается только путь к папке, то File by name **счемаконверсионрепорт&lt;n&gt;. Создается XML** . (необязательный атрибут)  
  
    Создание сводного отчета включает две дополнительные подкатегории:  
  
    -   `report-errors`(= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
    -   `verbose`(= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
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
  
Миграция данных  
  
1.  Переносит исходные данные в целевой объект.  
  
**Скрипт**  
  
1.  `object-name:`Указывает исходные объекты, которые учитываются при переносе данных (они могут иметь имена объектов отдельных или имена объектов групп).  
  
2.  `object-type:`Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
3.  `write-summary-report-to:`Указывает путь, по которому будет создан сводный отчет.  
  
    Если упоминается только путь к папке, то File by name **датамигратионрепорт&lt;n&gt;. Создается XML** . (необязательный атрибут)  
  
    Создание отчета имеет две дополнительные подкатегории:  
  
    -   `report-errors`(= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
    -   `verbose`(= "true/false", значение по умолчанию — "false" (необязательные атрибуты))  
  
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
  
## <a name="migration-preparation-script-file-command"></a>Команда подготовки файла сценария миграции  
Команда подготовки к миграции инициирует сопоставление схемы между исходной и целевой базами данных.  
  
**Command**  
  
Map-Schema  
  
Сопоставление схемы базы данных источника с целевой схемой.  
  
**Скрипт**  
  
1.  `source-schema`Указывает исходную схему, которую планируется перенести.  
  
2.  `sql-server-schema`Указывает целевую схему, в которой требуется перенести ее.  
  
**Пример синтаксиса:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>Команды файла сценария управляемости  
Команды управления помогают синхронизировать объекты целевой базы данных с базой данных источника.  
  
> [!NOTE]  
> Параметр вывода консоли по умолчанию для команд миграции — "полный" выходной отчет без подробных отчетов об ошибках: сводка только на корневом узле дерева исходного объекта.  
  
**Command**  
  
синхронизировать — целевой объект  
  
1.  Синхронизирует целевые объекты с целевой базой данных.  
  
2.  Если эта команда выполняется для базы данных-источника, то возникает ошибка.  
  
3.  Если целевое подключение к базе данных не выполняется до выполнения этой команды или при сбое подключения к целевому серверу базы данных во время выполнения команды, возникает ошибка, и консольное приложение завершает работу.  
  
**Скрипт**  
  
1.  `object-name:`Указывает объекты, которые учитываются при синхронизации с целевой базой данных (у нее могут быть имена объектов отдельных или имя объекта группы).  
  
2.  `object-type:`Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
3.  `on-error:`Указывает, следует ли указывать ошибки синхронизации как предупреждения или ошибки. Доступные параметры для On-Error:  
  
    -   отчет-всего-как-предупреждение  
  
    -   отчет — каждое предупреждение  
  
    -   сценарий Fail  
  
4.  `report-errors-to:`Указывает расположение отчета об ошибках для операции синхронизации (необязательный атрибут), если указан только путь к папке, а затем создается файл с именем **таржетсинчронизатионрепорт. XML** .  
  
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
  
Обновление из базы данных  
  
1.  Обновляет исходные объекты из базы данных.  
  
2.  Если эта команда выполняется для целевой базы данных, создается ошибка.  
  
**Скрипт**  
  
1.  `object-name:`Указывает исходные объекты, которые предполагается обновлять из базы данных-источника (они могут иметь имена объектов отдельных или имена объектов групп).  
  
2.  `object-type:`Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
3.  `on-error:`Указывает, следует ли указывать ошибки синхронизации как предупреждения или ошибки. Доступные параметры для On-Error:  
  
    -   отчет-всего-как-предупреждение  
  
    -   отчет — каждое предупреждение  
  
    -   сценарий Fail  
  
4.  `report-errors-to:`Указывает расположение отчета об ошибках для операции синхронизации (необязательный атрибут), если указан только путь к папке, а затем создается файл с именем **саурцедбрефрешрепорт. XML** .  
  
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
  
## <a name="script-generation-script-file-commands"></a>Команды файла сценария создания скрипта  
Команды создания скрипта выполняют две задачи: они помогают сохранить выходные данные консоли в файле скрипта. и запишите выходные данные T-SQL в консоль или файл на основе указанного параметра.  
  
**Command**  
  
Сохранить как сценарий  
  
Используется для сохранения скриптов объектов в файл, упоминаемый в метабазе, который указан в параметре MetaBase = Target. это альтернатива команде синхронизации, в которой мы получаем сценарии и выполняющими те же операции в целевой базе данных.  
  
**Скрипт**  
  
Требуется один или несколько узлов метабазы в качестве параметра командной строки.  
  
1.  `object-name:`Указывает объекты, скрипты для которых должны быть сохранены. (У него могут быть имена объектов отдельных или имя объекта Group).  
  
2.  `object-type:`Указывает тип объекта, указанного в атрибуте object-name (если указана категория объекта, тип объекта будет "Category").  
  
3.  `metabase:`Указывает, является ли это исходным или целевым метабазой.  
  
4.  `destination:`Указывает путь или папку, в которой должен быть сохранен скрипт, если имя файла не указано, затем имя файла в формате (object_name значение атрибута). out  
  
5.  `overwrite:`Если задано значение true, он перезаписывается, если такое же имя файла существует. Он может иметь значения (true/false).  
  
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
  
Convert-SQL-оператор  
  
1.  `context`Указывает имя схемы.  
  
2.  `destination`Указывает, должны ли выходные данные храниться в файле.  
  
    Если этот атрибут не указан, преобразованная инструкция T-SQL отображается на консоли. (необязательный атрибут)  
  
3.  `conversion-report-folder`Указывает папку, в которой может храниться отчет по оценке. (необязательный атрибут)  
  
4.  `conversion-report-overwrite`Указывает, следует ли перезаписывать папку с отчетом оценки, если она уже существует.  
  
    **Значение по умолчанию:** false. (необязательный атрибут)  
  
5.  `write-converted-sql-to`Указывает путь к папке файла (или), в которой будет сохранен преобразованный T-SQL. Если путь к папке указан вместе с `sql-files` атрибутом, то каждый исходный файл будет иметь соответствующий целевой файл T-SQL, созданный в указанной папке. Если путь к папке указан вместе с `sql` атрибутом, преобразованный T-SQL записывается в файл с именем result. out в указанной папке.  
  
6.  `sql`задает инструкции MySQL SQL для преобразования, одна или несколько инструкций могут быть разделены с помощью ";"  
  
7.  `sql-files`Указывает путь к файлам SQL, которые должны быть преобразованы в код T-SQL.  
  
8.  `write-summary-report-to`Указывает путь, по которому будет создан сводный отчет. Если упоминается только путь к папке, то создается файл с именем **конвертсклрепорт. XML** . (необязательный атрибут)  
  
    Создание отчета имеет две дополнительные подкатегории, визуализациям..,:  
  
    -   отчет — ошибки (= "true/false", по умолчанию — "false" (необязательные атрибуты)).  
  
    -   verbose (= "true/false", значение по умолчанию — "false" (необязательные атрибуты)).  
  
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
Сведения о параметрах командной строки см. [в разделе Параметры командной строки в консоли SSMA &#40;MySQLToSQL&#41;](../../ssma/mysql/command-line-options-in-ssma-console-mysqltosql.md) .  
  
Дополнительные сведения о примерах файлов сценариев консоли см. [в разделе Работа с примерами файлов сценариев консоли &#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-the-sample-console-script-files-mysqltosql.md)  
  
Следующий шаг зависит от требований проекта:  
  
1.  Сведения об указании пароля или экспорте и импорте паролей см. в статье [Управление паролями &#40;MySQLToSQL&#41;](../../ssma/mysql/managing-passwords-mysqltosql.md).  
  
2.  Сведения о создании отчетов см. в разделе [Создание отчетов &#40;MySQLToSQL&#41;](../../ssma/mysql/generating-reports-mysqltosql.md).  
  
3.  Сведения об устранении неполадок в консоли см. в разделе [Устранение неполадок &#40;MySQLToSQL&#41;](../../ssma/mysql/troubleshooting-mysqltosql.md).  
  
