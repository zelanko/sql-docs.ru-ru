---
title: "Учебник: Составление инструкций Transact-SQL | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Transact-SQL statements, tutorials
- Transact-SQL tutorials
- tutorials [Transact-SQL]
ms.assetid: 2addc9be-67d0-423d-a457-192fe9d7d058
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 22ddf6026a91dbbc2f7f1919497fa796b76ecc34
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="tutorial-writing-transact-sql-statements"></a>Учебник. Составление инструкций Transact-SQL
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]Добро пожаловать в записи [!INCLUDE[tsql](../includes/tsql-md.md)] инструкций учебника. Этот учебник предназначен для пользователей, не умеющих составлять инструкции SQL. Он поможет новым пользователям начать обучение с просмотра некоторых простых инструкций по созданию таблиц и вставке данных. Этот учебник использует язык [!INCLUDE[tsql](../includes/tsql-md.md)], [!INCLUDE[msCoName](../includes/msconame-md.md)] -реализацию стандарта SQL. Он представляет собой краткое введение в язык [!INCLUDE[tsql](../includes/tsql-md.md)] и не заменяет обучение языку [!INCLUDE[tsql](../includes/tsql-md.md)] . Инструкции в учебнике намеренно простые и не представляют всей сложности типичной производственной базы данных.  
  
>**ПРИМЕЧАНИЕ** . Если вы новичок, то, возможно, вам будет проще использовать [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , а не создавать инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] .  
  
## <a name="finding-more-information"></a>Дополнительные сведения  
Дополнительные сведения об отдельных инструкциях см. в электронной документации по SQL Server либо по имени инструкции, либо используя вкладку "Содержание" для просмотра 1800 языковых элементов, перечисленных в алфавитном порядке в разделе [Справочник по Transact-SQL (компонент Database Engine)](../t-sql/transact-sql-reference-database-engine.md). Еще одной хорошей стратегией нахождения информации является ее поиск по ключевым словам, относящимся к интересующей вас тематике. Например, чтобы узнать, как возвратить часть даты (например, месяц), выполните поиск в индексе по **датам [SQL Server]**, а затем используйте **функции извлечения частей даты**. Это приведет к разделу [DATEPART (Transact-SQL)](../t-sql/functions/datepart-transact-sql.md). В качестве другого примера, чтобы выяснить, как работать со строками, ищите **строковые функции**. Это приведет к разделу [Строковые функции (Transact-SQL)](../t-sql/functions/string-functions-transact-sql.md).  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
В этом учебнике показано, как создать базу данных и таблицу в ней, вставить данные в таблицу, обновить их, прочитать и удалить данные, удалить таблицу. Будут созданы представления и хранимые процедуры, а для базы данных и данных будет настроен пользователь.  
  
Учебник разделен на три занятия.  
  
[Урок 1. Создание объектов базы данных](../t-sql/lesson-1-creating-database-objects.md)  
В этом занятии будет создана база данных, таблица в ней, вставлены данные в таблицу, затем данные будут обновлены и прочитаны.  
  
[Занятие 2. Настройка разрешений на объекты базы данных](../t-sql/lesson-2-configuring-permissions-on-database-objects.md)  
В этом занятии будут созданы имя входа и пользователь. Также будут созданы представление и хранимая процедура, и пользователю будет предоставлено разрешение на нее.  
  
[Урок 3. Удаление объектов базы данных](../t-sql/lesson-3-deleting-database-objects.md)  
В этом занятии доступ к данным будет запрещен, данные из таблицы удалены, сама таблица тоже удалена вместе с базой данных.  
  
## <a name="requirements"></a>Требования  
Чтобы завершить этот учебник, не нужно обладать знаниями языка SQL, но нужно иметь основные понятия о базах данных, таких как таблицы. С помощью этого учебника будут созданы база данных и пользователь Windows. Эти задачи требуют высокого уровня разрешений, так что следует войти в систему в качестве администратора.  
  
В системе должно быть установлено следующее.  
  
-   Любой выпуск [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-  [Среда Среда SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)  
  

 
  
  
  

