---
title: Доступ к таблицам FileTable с помощью Transact-SQL | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], accessing files with T-SQL
ms.assetid: 3c4a5ffb-c521-4696-99cb-2b03cffc9c02
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c47751ef34747e1b3742accf5040846ecde074f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84955874"
---
# <a name="access-filetables-with-transact-sql"></a>Доступ к таблицам FileTable с помощью Transact-SQL
  Описывает, как команды языка обработки данных DML [!INCLUDE[tsql](../../includes/tsql-md.md)] работают c таблицами FileTable.  
  
##  <a name="insert-operations-on-filetables"></a><a name="BasicsInsert"></a> Операции INSERT в таблицах FileTable  
 С операциями **INSERT** в таблицах FileTable связаны следующие моменты:  
  
-   Все столбцы атрибутов файла имеют ограничения NO NULL. Если значения не заданы явным образом, предоставляются соответствующие значения по умолчанию.  
  
-   Если инструкция INSERT задает значения для параметров **name**, **path_locator**, **parent_path_locator**или атрибуты файлов, то применяются системные ограничения.  
  
-   Приложение может получить **path_locator** для файла или каталога, указав путь файловой системы для функции [GetPathLocator (Transact-SQL)](/sql/relational-databases/system-functions/getpathlocator-transact-sql).  
  
##  <a name="update-operations-on-filetables"></a><a name="BasicsUpdate"></a> Операции UPDATE в таблицах FileTable  
 С операциями UPDATE в таблицах **FileTable** связаны следующие моменты:  
  
-   Разрешается обновлять любые данные, определяемые пользователем.  
  
-   Если инструкция INSERT задает значения для параметров **name**, **path_locator**, **parent_path_locator**или атрибуты файлов, то применяются системные ограничения.  
  
-   Обновления данных FILESTREAM в столбце **file_stream** не влияют ни на какие другие столбцы, включая отметки времени.  
  
##  <a name="delete-operations-on-filetables"></a><a name="BasicsDelete"></a> Операции DELETE в таблицах FileTable  
 С операциями **DELETE** в таблицах FileTable связаны следующие моменты.  
  
-   При удалении строки удаляется соответствующий файл или каталог из файловой системы.  
  
-   Невозможно удалить строку, если она относится к каталогу, который содержит другие файлы или каталоги.  
  
##  <a name="constraints-that-are-enforced-for-dml-operations-on-filetables"></a><a name="BasicsConstraints"></a> Ограничения, необходимые для операций DML в таблицах FileTable  
 Определяемые системой ограничения обеспечивают сохранение целостности иерархии пространства имен файлов во время операций DML. Принудительно применяются следующие ограничения.  
  
-   При установке или изменении **name** файла или каталога:  
  
    -   Поддерживаются обозначения имен файлов и каталогов Windows.  
  
    -   Обеспечивается уникальность имени в родительском каталоге.  
  
-   При установке или изменении расположения файла или каталога путем назначения или редактирования **path_locator** или **parent_path_locator**:  
  
    -   Обеспечивается уникальность.  
  
    -   Обеспечивается согласованность иерархического дерева каталогов и файлов, включая согласованность значений **path_locator** и **parent_path_locator** .  
  
-   Значение **is_directory** не может быть задано как true для ненулевого столбца **file_stream** . Данные в столбце **file_stream** показывают, что строка соответствует файлу, а не каталогу.  
  
-   Столбцы атрибутов файлов не могут иметь значение NULL. Ограничения NOT NULL применяются со значениями по умолчанию.  
  
-   Значение **last_access_time** не может быть меньше (раньше), чем **last_write_time** и **creation_time**.  
  
## <a name="see-also"></a>См. также:  
 [выполнить загрузку файлов в таблицу FileTables](load-files-into-filetables.md)   
 [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md)   
 [Доступ к таблицам FileTable с помощью API-интерфейсов ввода-вывода файлов](access-filetables-with-file-input-output-apis.md)   
 [Инструкции FileTable языка DDL, функции, хранимые процедуры и представления](../views/views.md)  
  
  
