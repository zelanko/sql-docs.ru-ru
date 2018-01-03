---
title: "GetFileNamespacePath (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetFileNamespacePath
- GetFileNamespacePath_TSQL
dev_langs: TSQL
helpviewer_keywords: GetFileNamespacePath function
ms.assetid: b393ecef-baa8-4d05-a268-b2f309fce89a
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3e7ba6d9582a0eb3660f206dc68087f4fa4852a8
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="getfilenamespacepath-transact-sql"></a>GetFileNamespacePath (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает путь UNC к файлу или каталогу в таблице FileTable.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<column-name>.GetFileNamespacePath(is_full_path, @option)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Имя столбца*  
 Имя столбца VARBINARY(MAX) **file_stream** столбца в таблице FileTable.  
  
 *Имя столбца* значение должно быть допустимое имя столбца. Это не может быть выражение или значение, преобразованное или приведенное из столбца другого типа данных.  
  
 *is_full_path*  
 Целочисленное выражение, указывающее, какой путь возвращать: относительный или абсолютный. *is_full_path* может иметь одно из следующих значений:  
  
|Значение|Description|  
|-----------|-----------------|  
|**0**|Возвращает относительный путь внутри каталога уровня базы данных.<br /><br /> Это значение по умолчанию.|  
|**1**|Возвращает полный путь UNC, начиная с `\\computer_name`.|  
  
 *@option*  
 Целочисленное выражение, определяющее способ форматирования серверных компонентов пути. *@option*может принимать одно из следующих значений:  
  
|Значение|Description|  
|-----------|-----------------|  
|**0**|Возвращает имя сервера, преобразованное в формат NetBIOS, например<br /><br /> `\\SERVERNAME\MSSQLSERVER\MyDocumentDB`<br /><br /> Это значение по умолчанию.|  
|**1**|Возвращает имя сервера без преобразования, например:<br /><br /> `\\ServerName\MSSQLSERVER\MyDocumentDB`|  
|**2**|Возвращает полный путь сервера, например:<br /><br /> `\\ServerName.MyDomain.com\MSSQLSERVER\MyDocumentDB`|  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **nvarchar(max)**  
  
 Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является кластеризованным экземпляром в отказоустойчивом кластере, то имя компьютера, возвращаемое в качестве части этого пути, совпадает с именем виртуального узла для кластеризованного экземпляра.  
  
 Если база данных принадлежит к группе доступности Always On, то **FileTableRootPath** функция возвращает имя виртуальной сети (VNN) вместо имени компьютера.  
  
## <a name="general-remarks"></a>Общие замечания  
 Путь, **GetFileNamespacePath** функция возвращает логический путь файла или каталога в следующем формате:  
  
 `\\<machine>\<instance-level FILESTREAM share>\<database-level directory>\<FileTable directory>\...`  
  
 Этот логический путь не соответствует физическому пути NTFS. Он преобразуется в физический путь драйвером фильтра FILESTREAM файловой системы и агентом FILESTREAM. Возможность отделить логический путь от физического позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реорганизовать внутренние данные таким образом, чтобы пути остались действительными.  
  
## <a name="best-practices"></a>Рекомендации  
 Чтобы код и приложения были независимы от текущего компьютера и базы данных, следует избегать создания кода с использованием абсолютных путей. Вместо этого рекомендуется получать полный путь для файла во время выполнения с помощью **FileTableRootPath** и **GetFileNamespacePath** функций, как показано в следующем примере. По умолчанию функция **GetFileNamespacePath** возвращает относительный путь к файлу, находящемуся внутри корневого пути к базе данных.  
  
```sql  
USE MyDocumentDB;  
@root varchar(100)  
SELECT @root = FileTableRootPath();  
  
@fullPath = varchar(1000);  
SELECT @fullPath = @root + file_stream.GetFileNamespacePath() FROM DocumentStore  
WHERE Name = N’document.docx’;  
```  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Примеры  
 В следующих примерах демонстрируется вызов **GetFileNamespacePath** функцию для получения UNC-путь для файла или каталога в таблице FileTable.  
  
```  
-- returns the relative path of the form “\MyFileTable\MyDocDirectory\document.docx”  
SELECT file_stream.GetFileNamespacePath() AS FilePath FROM DocumentStore  
WHERE Name = N’document.docx’;  
  
-- returns “\\MyServer\MSSQLSERVER\MyDocumentDB\MyFileTable\MyDocDirectory\document.docx”  
SELECT file_stream.GetFileNamespacePath(1, Null) AS FilePath FROM DocumentStore  
WHERE Name = N’document.docx’;  
```  
  
## <a name="see-also"></a>См. также:  
 [Работа с каталогами и путями в таблицах FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
