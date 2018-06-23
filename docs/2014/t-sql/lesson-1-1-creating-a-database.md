---
title: Создание базы данных (учебник) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tutorial creating a database
ms.assetid: e1e2c83f-dfad-4bb8-aa7a-09d3f69517ae
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 71b57935e3add7bc6121968b7b1d4f3fb9531ac6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102132"
---
# <a name="creating-a-database-tutorial"></a>Создание базы данных (учебник)
  Как и у многих инструкций языка [!INCLUDE[tsql](../includes/tsql-md.md)] , у инструкции CREATE DATABASE имеется обязательный параметр: имя базы данных. Кроме этого, у инструкции CREATE DATABASE имеется ряд необязательных параметров, таких как расположение на диске, где требуется хранить файлы базы данных. При выполнении инструкции CREATE DATABASE без дополнительных параметров, для многих из них [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует значения по умолчанию. В этом учебнике используются лишь некоторые дополнительные синтаксические параметры.  
  
### <a name="to-create-a-database"></a>Создание базы данных  
  
1.  В окне редактора запросов введите, но не выполняйте, следующий код:  
  
    ```  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  С помощью указателя выделите слова `CREATE DATABASE`и нажмите клавишу **F1**. Должен открыться раздел CREATE DATABASE электронной документации по SQL Server. Таким же способом можно найти полный синтаксис инструкции CREATE DATABASE и других инструкций, используемых в данном учебнике.  
  
3.  В редакторе запросов нажмите клавишу **F5** , чтобы выполнить инструкцию и создать базу данных с именем `TestData`.  
  
 При создании базы данных сервер [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] создает копию базы данных **model** и присваивает ей указанное имя базы данных. Эта операция обычно занимает несколько секунд, если только с помощью дополнительного параметра не указан большой исходный размер базы данных.  
  
> [!NOTE]  
>  Когда в одном пакете представлено несколько инструкций, они разделяются с помощью ключевого слова GO. Ключевое слово GO является необязательным, если в пакете содержится только одна инструкция.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Создание таблицы &#40;учебника&#41;](lesson-1-2-creating-a-table.md)  
  
## <a name="see-also"></a>См. также  
 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
