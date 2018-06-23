---
title: Создание таблицы для хранения данных FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], table storage
ms.assetid: 029c3059-5c83-43e2-a859-9027031b7de1
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 34c7053b878f49be1b3aa3f6c9aee4a7bc2e24e4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193380"
---
# <a name="create-a-table-for-storing-filestream-data"></a>Создание таблицы для хранения данных FILESTREAM
  В этом разделе приводятся сведения о создании таблицы для хранения данных FILESTREAM.  
  
 Если в базе данных имеется файловая группа FILESTREAM, можно создавать или изменять таблицы для хранения данных FILESTREAM. Чтобы указать, что в столбце будут содержаться данные типа FILESTREAM, необходимо создать столбец с типом данных `varbinary(max)` и добавить ему атрибут FILESTREAM.  
  
### <a name="to-create-a-table-to-store-filestream-data"></a>Создание таблицы для хранения данных FILESTREAM  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]нажмите кнопку **Создать запрос** , чтобы открыть редактор запросов.  
  
2.  Скопируйте следующий код [!INCLUDE[tsql](../../includes/tsql-md.md)] и вставьте его в редактор запросов. Этот код [!INCLUDE[tsql](../../includes/tsql-md.md)] создает таблицу с поддержкой FILESTREAM, именуемую Records.  
  
3.  Чтобы создать таблицу, нажмите кнопку **Выполнить**.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как создать таблицу с именем `Records`. Столбец `Id` является столбцом типа `ROWGUIDCOL` и необходим для использования данных FILESTREAM с API Win32. Столбец `SerialNumber` имеет тип `UNIQUE INTEGER`. Столбец `Chart` является столбцом типа `FILESTREAM` и используется для хранения данных `Chart` в файловой системе.  
  
> [!NOTE]  
>  Этот пример ссылается на базу данных Archive, созданную в разделе [Создание базы данных с поддержкой FILESTREAM](create-a-filestream-enabled-database.md).  
  
 [!code-sql[FILESTREAM#FS_CreateTable](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_createtable)]  
  
## <a name="see-also"></a>См. также  
 [CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql)   
 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
