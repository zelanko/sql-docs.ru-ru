---
title: Создание базы данных с поддержкой FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: blob
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FILESTREAM-enabled databases
ms.assetid: 0fc16356-76f7-44b8-a58b-f0b7c43694ec
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e9da6625b53d1640b5568b506734918cbaae51a1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32922929"
---
# <a name="create-a-filestream-enabled-database"></a>Создание базы данных с поддержкой FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе показано, как создать базу данных с поддержкой FILESTREAM. Поскольку хранилище FILESTREAM использует особый тип файловой группы, при создании базы данных необходимо указать предложение CONTAINS FILESTREAM хотя бы для одной файловой группы.  
  
 Файловая группа FILESTREAM может содержать более одного файла. Пример кода, демонстрирующий создание файловой группы FILESTREAM из нескольких файлов, см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
### <a name="to-create-a-filestream-enabled-database"></a>Создание базы данных с поддержкой FILESTREAM  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]нажмите кнопку **Создать запрос** , чтобы открыть редактор запросов.  
  
2.  Скопируйте следующий код [!INCLUDE[tsql](../../includes/tsql-md.md)] и вставьте его в редактор запросов. Этот код [!INCLUDE[tsql](../../includes/tsql-md.md)] создает базу данных с поддержкой FILESTREAM, именуемую Archive.  
  
    > [!NOTE]  
    >  Для этого скрипта должен существовать каталог C:\Data.  
  
3.  Чтобы построить базу данных, нажмите кнопку **Выполнить**.  
  
## <a name="example"></a>Пример  
 В следующем примере кода создается база данных с именем `Archive`. В этой базе данных содержатся три файловые группы: `PRIMARY`, `Arch1`и `FileStreamGroup1`. `PRIMARY` и `Arch1` — это обычные файловые группы, которые не могут содержать данные FILESTREAM. `FileStreamGroup1` — это файловая группа `FILESTREAM` .  
  
 [!code-sql[FILESTREAM#FS_CreateDB](../../relational-databases/blob/codesnippet/tsql/create-a-filestream-enab_1.sql)]  
  
 Для файловой группы `FILESTREAM` параметр `FILENAME` содержит путь. Должен существовать путь вплоть до последнего каталога, но последний каталог существовать не должен. В этом примере `c:\data` должен существовать. Но вложенная папка `filestream1` не может существовать, если выполняется инструкция `CREATE DATABASE` . Дополнительные сведения о синтаксисе см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
 После запуска предыдущего примера в папке «c:\Data\filestream1» появится файл filestream.hdr и папка $FSLOG. Файл filestream.hdr является файлом заголовка контейнера FILESTREAM.  
  
> [!IMPORTANT]  
>  Файл filestream.hdr является важным системным файлом. Он содержит данные заголовка FILESTREAM. Не перемещайте и не изменяйте этот файл.  
  
 Для существующих баз данных файловую группу FILESTREAM можно добавить с помощью инструкции [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) .  
  
## <a name="see-also"></a>См. также:  
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)  
  
  
