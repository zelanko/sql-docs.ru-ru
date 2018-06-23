---
title: Создание базы данных с поддержкой FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], FILESTREAM-enabled databases
ms.assetid: 0fc16356-76f7-44b8-a58b-f0b7c43694ec
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ea0ab6c8c418b3ea2e3d286f38b382c7e73794eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193382"
---
# <a name="create-a-filestream-enabled-database"></a>Создание базы данных с поддержкой FILESTREAM
  В этом разделе показано, как создать базу данных с поддержкой FILESTREAM. Поскольку хранилище FILESTREAM использует особый тип файловой группы, при создании базы данных необходимо указать предложение CONTAINS FILESTREAM хотя бы для одной файловой группы.  
  
 Файловая группа FILESTREAM может содержать более одного файла. Пример кода, демонстрирующий создание файловой группы FILESTREAM из нескольких файлов, см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql).  
  
### <a name="to-create-a-filestream-enabled-database"></a>Создание базы данных с поддержкой FILESTREAM  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]нажмите кнопку **Создать запрос** , чтобы открыть редактор запросов.  
  
2.  Копировать [!INCLUDE[tsql](../../includes/tsql-md.md)] кода создает базу поддержкой FILESTREAM, именуемую Archive.  
  
    > [!NOTE]  
    >  Для этого скрипта должен существовать каталог C:\Data.  
  
3.  Чтобы построить базу данных, нажмите кнопку **Выполнить**.  
  
## <a name="example"></a>Пример  
 В следующем примере кода создается база данных с именем `Archive`. В этой базе данных содержатся три файловые группы: `PRIMARY`, `Arch1`и `FileStreamGroup1`. `PRIMARY` и `Arch1` — это обычные файловые группы, которые не могут содержать данные FILESTREAM. `FileStreamGroup1` — это файловая группа `FILESTREAM` .  
  
```tsql  
CREATE DATABASE Archive   
ON  
PRIMARY ( NAME = Arch1,  
    FILENAME = 'c:\data\archdat1.mdf'),  
FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
    FILENAME = 'c:\data\filestream1')  
LOG ON  ( NAME = Archlog1,  
    FILENAME = 'c:\data\archlog1.ldf')  
GO  
```  
  
 Для файловой группы `FILESTREAM` параметр `FILENAME` содержит путь. Должен существовать путь вплоть до последнего каталога, но последний каталог существовать не должен. В этом примере `c:\data` должен существовать. Но вложенная папка `filestream1` не может существовать, если выполняется инструкция `CREATE DATABASE` . Дополнительные сведения о синтаксисе см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql).  
  
 После запуска предыдущего примера в папке «c:\Data\filestream1» появится файл filestream.hdr и папка $FSLOG. Файл filestream.hdr является файлом заголовка контейнера FILESTREAM.  
  
> [!IMPORTANT]  
>  Файл filestream.hdr является важным системным файлом. Он содержит данные заголовка FILESTREAM. Не перемещайте и не изменяйте этот файл.  
  
 Для существующих баз данных файловую группу FILESTREAM можно добавить с помощью инструкции [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) .  
  
## <a name="see-also"></a>См. также  
 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
