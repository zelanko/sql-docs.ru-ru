---
title: FileTableRootPath (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- FileTableRootPath_TSQL
- FileTableRootPath
dev_langs:
- TSQL
helpviewer_keywords:
- FileTableRootPath function
ms.assetid: 0cba908a-c85c-4b09-b16a-df1cb333c629
author: rothja
ms.author: jroth
ms.openlocfilehash: 80651e82fb643d044f4c953481dde2114adcadda
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68042859"
---
# <a name="filetablerootpath-transact-sql"></a>FileTableRootPath (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает корневой путь UNC для конкретной таблицы FileTable или для текущей базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FileTableRootPath ( [ '[schema_name.]FileTable_name' ], @option )  
```  
  
## <a name="arguments"></a>Аргументы  
 *FileTable_name*  
 Имя таблицы FileTable. *FileTable_name* имеет тип **nvarchar**. Этот параметр является необязательным. Значением по умолчанию является текущая база данных. Указание *schema_name* также является необязательным. Вы можете передать значение NULL для *FileTable_name* использовать значение параметра по умолчанию  
  
 *@option*  
 Целочисленное выражение, определяющее способ форматирования серверных компонентов пути. *@option* Может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Возвращает имя сервера, преобразованное в формат NetBIOS, например<br /><br /> `\\SERVERNAME\MSSQLSERVER\MyDocumentDatabase`<br /><br /> Это значение по умолчанию.|  
|**1**|Возвращает имя сервера без преобразования, например:<br /><br /> `\\ServerName\MSSQLSERVER\MyDocumentDatabase`|  
|**2**|Возвращает полный путь сервера, например:<br /><br /> `\\ServerName.MyDomain.com\MSSQLSERVER\MyDocumentDatabase`|  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **nvarchar(4000)**  
  
 Если база данных принадлежит к группе доступности Always On, то **FileTableRootPath** функция возвращает имя виртуальной сети (VNN) вместо имени компьютера.  
  
## <a name="general-remarks"></a>Общие замечания  
 **FileTableRootPath** функция возвращает значение NULL, если выполняется одно из следующих условий:  
  
-   Значение *FileTable_name* является недопустимым.  
  
-   Вызывающая сторона не имеет достаточных разрешений для ссылки на указанную таблицу или текущую базу данных.  
  
-   Параметр FILESTREAM *database_directory* не задан для текущей базы данных.  
  
 Дополнительные сведения см. в статье [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md).  
  
## <a name="best-practices"></a>Рекомендации  
 Чтобы код и приложения были независимы от текущего компьютера и базы данных, следует избегать создания кода с использованием абсолютных путей. Вместо этого рекомендуется получать полный путь для файла во время выполнения с помощью **FileTableRootPath** и **GetFileNamespacePath** функций, как показано в следующем примере. По умолчанию функция **GetFileNamespacePath** возвращает относительный путь к файлу, находящемуся внутри корневого пути к базе данных.  
  
```sql  
USE MyDocumentDatabase;  
  
@root varchar(100)  
SELECT @root = FileTableRootPath();  
@fullPath = varchar(1000);  
  
SELECT @fullPath = @root + file_stream.GetFileNamespacePath()  
FROM DocumentStore  
WHERE Name = N'document.docx';  
```  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 **FileTableRootPath** функции требуется:  
  
-   разрешение SELECT на FileTable, чтобы получить корневой путь конкретной таблицы FileTable;  
  
-   **db_datareader** или выше разрешение, чтобы получить корневой путь для текущей базы данных.  
  
## <a name="examples"></a>Примеры  
 Следующие примеры показывают, как вызывать **FileTableRootPath** функции.  
  
```  
USE MyDocumentDatabase;  
-- returns "\\MYSERVER\MSSQLSERVER\MyDocumentDatabase"  
SELECT FileTableRootPath();  
  
-- returns "\\MYSERVER\MSSQLSERVER\MyDocumentDatabase\MyFileTable"  
SELECT FileTableRootPath(N'dbo.MyFileTable');  
  
-- returns "\\MYSERVER\MSSQLSERVER\MyDocumentDatabase\MyFileTable"  
SELECT FileTableRootPath(N'MyFileTable');  
```  
  
## <a name="see-also"></a>См. также  
 [Работа с каталогами и путями в таблицах FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
