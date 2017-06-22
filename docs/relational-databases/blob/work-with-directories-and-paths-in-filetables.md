---
title: "Работа с каталогами и путями в таблицах FileTable | Документация Майкрософт"
ms.custom: 
ms.date: 08/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FileTables [SQL Server], directories
ms.assetid: f1e45900-bea0-4f6f-924e-c11e1f98ab62
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d41410b3da1f823a29da0c5b7bd706dff4ce4584
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="work-with-directories-and-paths-in-filetables"></a>Работа с каталогами и путями в таблицах FileTable
  Описывает структуру каталогов, в которой файлы хранятся в таблицах FileTable.  
  
##  <a name="HowToDirectories"></a> Практическое руководство. Работа с каталогами и путями в таблицах FileTable  
 Следующие 3 функции можно использовать для работы с каталогами FileTable в [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
|Чтобы получить этот результат, выполните следующее.|Воспользуйтесь этой функцией|  
|------------------------|-----------------------|  
|Получите корневой путь UNC для конкретной таблицы FileTable или для текущей базы данных.|[FileTableRootPath (Transact-SQL)](../../relational-databases/system-functions/filetablerootpath-transact-sql.md)|  
|Получите абсолютный или относительный путь UNC к файлу или каталогу в таблице FileTable.|[GetFileNamespacePath (Transact-SQL)](../../relational-databases/system-functions/getfilenamespacepath-transact-sql.md)|  
|Получите значение идентификатора path_locator для заданного файла или каталога в таблице FileTable, указав путь к нему.|[GetPathLocator (Transact-SQL)](../../relational-databases/system-functions/getpathlocator-transact-sql.md)|  
  
##  <a name="BestPracticeRelativePaths"></a> Практическое руководство. Использование относительных путей для переносимого кода  
 Чтобы код и приложения были независимы от текущего компьютера и базы данных, следует избегать создания кода с использованием абсолютных путей. Вместо этого рекомендуется получать полный путь к файлу во время выполнения с помощью функций [FileTableRootPath (Transact-SQL)](../../relational-databases/system-functions/filetablerootpath-transact-sql.md) и [GetFileNamespacePath (Transact-SQL)](../../relational-databases/system-functions/getfilenamespacepath-transact-sql.md), как показано в приведенном ниже примере. По умолчанию функция **GetFileNamespacePath** возвращает относительный путь к файлу, находящемуся внутри корневого пути к базе данных.  
  
```tsql  
USE database_name;  
DECLARE @root nvarchar(100);  
DECLARE @fullpath nvarchar(1000);  
  
SELECT @root = FileTableRootPath();  
SELECT @fullpath = @root + file_stream.GetFileNamespacePath()  
    FROM filetable_name  
    WHERE name = N'document_name';  
  
PRINT @fullpath;  
GO  
```  
  
##  <a name="restrictions"></a> Важные ограничения  
  
###  <a name="nesting"></a> Уровень вложенности  
  
> **ВАЖНО!** Нельзя хранить более 15 уровней вложенных каталогов в каталоге FileTable. Если сохранено 15 уровней вложенных каталогов, каталог самого нижнего уровня не сможет содержать файлы, так как эти файлы представляют собой дополнительный уровень.  
  
###  <a name="fqnlength"></a> Длина полного имени  
  
> **ВАЖНО!** Файловая система NTFS поддерживает пути, намного превышающие ограничение в 260 символов, установленное в оболочке Windows и большинстве других функций Windows API. Поэтому можно создавать файлы в файловой иерархии FileTable с помощью Transact-SQL, которые нельзя будет просмотреть или открыть в Проводнике Windows и многих других приложениях Windows, поскольку полный путь превышает 260 символов. Однако с этими файлами вы можете продолжать работать с помощью инструкций Transact-SQL.  
  
##  <a name="fullpath"></a> Полный путь к элементу, хранящемуся в таблице FileTable  
 Полный путь к файлу или каталогу, сохраненный в таблице FileTable, начинается со следующих элементов.  
  
1.  Общий ресурс с поддержкой доступа файлового ввода-вывода к данным FILESTREAM на уровне экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Имя **DIRECTORY_NAME** на уровне базы данных.  
  
3.  **FILETABLE_DIRECTORY** на уровне таблицы FileTable.  
  
 В итоге иерархия выглядит следующим образом.  
  
 `\\<machine>\<instance-level FILESTREAM share>\<database-level directory>\<FileTable directory>\`  
  
 Данная иерархия каталогов образует корень пространства имен FileTable. В этой иерархии каталогов данные FILESTREAM для FileTable хранятся в виде файлов и в виде вложенных каталогов, которые также могут содержать файлы и вложенные каталоги.  
  
 Важно иметь в виду, что иерархия каталогов, созданная в общем ресурсе FILESTREAM на уровне экземпляра, является виртуальной иерархией каталогов. Иерархия хранится в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не представлена физически в файловой системе NTFS. Все операции, осуществляющие доступ к файлам и каталогам в общем ресурсе FILESTREAM в таблицах FileTable, перехватываются и обрабатываются компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , внедренным в файловую систему.  
  
##  <a name="roots"></a> Семантика корневых каталогов на уровне экземпляра, базы данных и таблицы FileTable  
 Эта иерархия каталогов имеет следующую семантику.  
  
-   Общий ресурс FILESTREAM на уровне экземпляра настраивается администратором и хранится в виде свойства сервера. Этот общий ресурс можно переименовать с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Операция переименования вступает в силу только после перезапуска сервера.  
  
-   Параметр **DIRECTORY_NAME** уровня базы данных при создании базы данных по умолчанию имеет значение null. Администратор может задать или изменить это имя с помощью инструкции **ALTER DATABASE** . Это имя должно быть уникальным (при сравнении без учета регистра) в этом экземпляре.  
  
-   Обычно имя **FILETABLE_DIRECTORY** указывается в составе инструкции **CREATE TABLE** при создании таблицы FileTable. Это имя можно изменить с помощью команды **ALTER TABLE** .  
  
-   Эти корневые каталоги нельзя переименовать с помощью операций файлового ввода-вывода.  
  
-   Эти корневые каталоги нельзя открыть с использованием дескрипторов файлов для монопольного доступа.  
  
##  <a name="is_directory"></a> Столбец is_directory в схеме FileTable  
 В приведенной ниже таблице описывается взаимодействие между столбцом **is_directory** и столбцом **file_stream** , в котором находятся данные FILESTREAM в таблице FileTable.  
  
||||  
|-|-|-|  
|*is_directory* **value**|*file_stream* **value**|**Поведение**|  
|FALSE|NULL|Это недопустимое сочетание, которое будет перехвачено системным ограничением.|  
|FALSE|\<значение>|Этот элемент представляет файл.|  
|TRUE|NULL|Этот элемент представляет каталог.|  
|TRUE|\<значение>|Это недопустимое сочетание, которое будет перехвачено системным ограничением.|  
  
##  <a name="alwayson"></a> Использование имен виртуальной сети для групп доступности AlwaysOn  
 Если база данных, содержащая данные FILESTREAM или FileTable, принадлежит группе доступности:  
  
-   Функции FILESTREAM и FileTable принимают или возвращают имена виртуальной сети, а не имена компьютеров. Дополнительные сведения об этих функциях см. в разделе [Функции Filestream и FileTable (Transact-SQL)](../../relational-databases/system-functions/filestream-and-filetable-functions-transact-sql.md).  
  
-   При осуществлении любого доступа к данным FILESTREAM или FileTable посредством API-интерфейса файловой системы будут использоваться имена виртуальной сети, а не имена компьютеров. Дополнительные сведения см. в разделе [FILESTREAM и FileTable с группами доступности AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Включение необходимых компонентов для таблицы FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)   
 [Создание, изменение и удаление таблиц FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [Доступ к таблицам FileTable с помощью Transact-SQL](../../relational-databases/blob/access-filetables-with-transact-sql.md)   
 [Доступ к таблицам FileTable с помощью API-интерфейсов ввода-вывода файлов](../../relational-databases/blob/access-filetables-with-file-input-output-apis.md)  
  
  

