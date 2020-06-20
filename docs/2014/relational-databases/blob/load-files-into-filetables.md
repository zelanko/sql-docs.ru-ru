---
title: выполнить загрузку файлов в таблицу FileTables | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], migrating files
- FileTables [SQL Server], bulk loading
- FileTables [SQL Server], loading files
ms.assetid: dc842a10-0586-4b0f-9775-5ca0ecc761d9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 43ea31523da2dfa8b387f68ce4f7c7f07868dd6f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970884"
---
# <a name="load-files-into-filetables"></a>выполнить загрузку файлов в таблицу FileTables
  Описывает процедуру загрузки или переноса файлов в таблицы FileTable.  
  
##  <a name="loading-or-migrating-files-into-a-filetable"></a><a name="BasicsLoadNew"></a> загрузить или перенести файлы в таблицу FileTable  
 Выбор метода загрузки или переноса файлов в таблицу FileTable зависит от того, где хранятся файлы в настоящее время.  
  
|Текущее местоположение файлов|Параметры для переноса|  
|-------------------------------|---------------------------|  
|Файлы в настоящее время хранятся в файловой системе.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не имеет сведений о файлах.|Поскольку таблица FileTable в файловой системе Windows отображается в виде папки, можно легко загрузить файлы в новую таблицу FileTable любым из доступных способов перемещения или копирования файлов. Это может быть проводник Windows, программы командной строки, включая xcopy и robocopy, и пользовательские скрипты или приложения.<br /><br /> Существующую папку невозможно преобразовать в таблицу FileTable.|  
|Файлы в настоящее время хранятся в файловой системе.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит таблицу метаданных, в которой находятся указатели на файлы.|Сначала нужно переместить или скопировать файлы одним из способов, описанных выше.<br /><br /> Затем нужно обновить существующую таблицу метаданных, чтобы они указывали на новое расположение файлов.<br /><br /> Дополнительные сведения см. в подразделе [Пример. Перенос файлов из файловой системы в таблицу FileTable](#HowToMigrateFiles) этого раздела.|  
  
###  <a name="how-to-load-files-into-a-filetable"></a><a name="HowToLoadNew"></a> Как выполнить загрузку файлов в таблицу FileTable  
 Ниже перечислены методы, которые можно использовать для загрузки файлов в таблицу FileTable.  
  
-   Перетаскивание файлов из исходной папки в новую папку FileTable в проводнике Windows.  
  
-   Применение программ командной строки, таких как MOVE, COPY, XCOPY или ROBOCOPY из командной строки или пакетного файла или скрипта.  
  
-   Написание на C# или Visual Basic.NET пользовательского приложения для перемещения или копирования файлов с применением методов из пространства имен **System.IO** .  
  
###  <a name="example-migrating-files-from-the-file-system-into-a-filetable"></a><a name="HowToMigrateFiles"></a> Пример. Перенос файлов из файловой системы в таблицу FileTable  
 В этом сценарии файлы хранятся в файловой системе, а в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеется таблица метаданных, содержащая указатели на эти файлы. Необходимо переместить файлы в таблицу FileTable, затем заменить исходный путь UNC для каждого файла в метаданных на путь UNC таблицы FileTable. Функция [GetPathLocator (Transact-SQL)](/sql/relational-databases/system-functions/getpathlocator-transact-sql) помогает добиться этой цели.  
  
 В этом примере предположим, что существует таблица базы данных, `PhotoMetadata` содержащая данные о фотографиях. В этой таблице также имеется столбец `UNCPath` типа `varchar`(512), содержащий фактический путь UNC к JPG-файлу.  
  
 Чтобы перенести файлы изображений из файловой системы в таблицу FileTable, нужно выполнить следующие действия.  
  
1.  Создайте новую таблицу FileTable для хранения файлов. В этом примере используется имя таблицы `dbo.PhotoTable`, но не показан код для создания самой таблицы.  
  
2.  Для копирования JPG-файлов с их структурой каталогов в корневой каталог таблицы FileTable можно использовать программу xcopy или аналогичное средство.  
  
3.  Исправьте метаданные в таблице `PhotoMetadata` с помощью кода, похожего на следующий:  
  
```sql  
--  Add a path locator column to the PhotoMetadata table.  
ALTER TABLE PhotoMetadata ADD pathlocator hierarchyid;  
  
-- Get the root path of the Photo directory on the File Server.  
DECLARE @UNCPathRoot varchar(100) = '\\RemoteShare\Photographs';  
  
-- Get the root path of the FileTable.  
DECLARE @FileTableRoot varchar(1000);  
SELECT @FileTableRoot = FileTableRootPath('dbo.PhotoTable');  
  
-- Update the PhotoMetadata table.  
  
-- Replace the File Server UNC path with the FileTable path.  
UPDATE PhotoMetadata  
    SET UNCPath = REPLACE(UNCPath, @UNCPathRoot, @FileTableRoot);  
  
-- Update the pathlocator column to contain the pathlocator IDs from the FileTable.  
UPDATE PhotoMetadata  
    SET pathlocator = GetPathLocator(UNCPath);  
```  
  
##  <a name="bulk-loading-files-into-a-filetable"></a><a name="BasicsBulkLoad"></a> массовая загрузка файлов в таблицу FileTable  
 FileTable ведет себя как обычный стол для массовых операций, со следующей квалификацией.  
  
 Таблица FileTable имеет системные ограничения, гарантирующие целостность пространства имен файлов и каталогов. Эти ограничения должны быть проверены на массовых данных, загружаемых в FileTable. Так как часть операций массовой вставки разрешает игнорировать табличные ограничения, следующие меры применяются принудительно.  
  
-   В настоящее время операции массовой загрузки в таблицу FileTable, принудительно применяющие ограничения, можно выполнять, как с любой другой таблицей. В эту категорию входят следующие операции:  
  
    -   bcp с предложением CHECK_CONSTRAINTS;  
  
    -   BULK INSERT с предложением CHECK_CONSTRAINTS;  
  
    -   ВСТАВИТЬ В... SELECT * FROM OPENROWSET (BULK...) без предложения IGNORE_CONSTRAINTS.  
  
-   Операции массовой загрузки, не применяющие принудительно ограничения, завершаются неуспешно, если системные ограничения для таблицы FileTable не были отключены. В эту категорию входят следующие операции:  
  
    -   bcp без предложения CHECK_CONSTRAINTS;  
  
    -   BULK INSERT без предложения CHECK_CONSTRAINTS;  
  
    -   ВСТАВИТЬ В... Выберите * FROM OPENROWSET (BULK...) с предложением IGNORE_CONSTRAINTS.  
  
###  <a name="how-to-bulk-load-files-into-a-filetable"></a><a name="HowToBulkLoad"></a> Практическое руководство. Массовая загрузка файлов в таблицу FileTable  
 Для массовой загрузки файлов в таблицу FileTable можно использовать различные способы.  
  
-   **bcp**  
  
    -   Вызвать с предложением **CHECK_CONSTRAINTS** .  
  
    -   Отключить пространство имен FileTable и вызвать без предложения **CHECK_CONSTRAINTS** . Затем снова включить пространство имен FileTable.  
  
-   **BULK INSERT**  
  
    -   Вызвать с предложением **CHECK_CONSTRAINTS** .  
  
    -   Отключить пространство имен FileTable и вызвать без предложения **CHECK_CONSTRAINTS** . Затем снова включить пространство имен FileTable.  
  
-   **ВСТАВИТЬ В... Выбор \* из OPENROWSET (BULK...)**  
  
    -   Вызвать с предложением **IGNORE_CONSTRAINTS** .  
  
    -   Отключить пространство имен FileTable и выполнить вызов без предложения **IGNORE_CONSTRAINTS** . Затем снова включить пространство имен FileTable.  
  
 Сведения об отключении ограничений FileTable см. в разделе [Управление таблицами FileTable](manage-filetables.md).  
  
###  <a name="how-to-disable-filetable-constraints-for-bulk-loading"></a><a name="disabling"></a> Практическое руководство. Отключение ограничений FileTable для массовой загрузки  
 Для массовой загрузки файлов в таблицу FileTable без издержек по применению определенных в системе ограничений, можно временно отключить ограничения. Дополнительные сведения см. в статье [Управление таблицами FileTable](manage-filetables.md).  
  
## <a name="see-also"></a>См. также:  
 [Доступ к таблицам FileTable с помощью Transact-SQL](access-filetables-with-transact-sql.md)   
 [Доступ к таблицам FileTable с помощью API-интерфейсов ввода-вывода файлов](access-filetables-with-file-input-output-apis.md)  
  
  
