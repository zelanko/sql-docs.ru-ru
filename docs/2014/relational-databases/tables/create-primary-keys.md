---
title: Создание первичных ключей | Документация Майкрософт
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
- primary keys [SQL Server], creating
ms.assetid: 85c623ca-4656-4d70-a9db-ee4d897cd214
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 180dac17cd2aa504c7fd253761fd636e1baa5166
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102388"
---
# <a name="create-primary-keys"></a>Создание первичных ключей
  Определить первичный ключ в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Создание первичного ключа автоматически приводит к созданию соответствующего уникального кластеризованного или некластеризованного индекса.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Создание первичного ключа с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   В таблице возможно наличие только одного ограничения по первичному ключу.  
  
-   Все столбцы с ограничением PRIMARY KEY должны иметь признак NOT NULL. Если допустимость значения NULL не указана, то для всех столбцов c ограничением PRIMARY KEY устанавливается признак NOT NULL.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Создание новой таблицы с первичным ключом требует разрешения CREATE TABLE в базе данных и разрешения ALTER на схему, в которой создается таблица.  
  
 Создание первичного ключа в существующей таблице требует разрешения ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-primary-key"></a>Создание первичного ключа  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши таблицу, в которую необходимо добавить ограничение уникальности, и выберите **Конструктор**.  
  
2.  В **Конструкторе таблиц**щелкните селектор строк для столбца базы данных, который необходимо определить в качестве первичного ключа. Чтобы выделить несколько столбцов, нажмите и удерживайте клавишу CTRL и щелкните селекторы строк для остальных столбцов.  
  
3.  Щелкните правой кнопкой мыши средство выбора строк столбца и выберите команду **Задать первичный ключ**.  
  
> [!CAUTION]  
>  Чтобы переопределить первичный ключ, необходимо удалить все связи с существующим первичным ключом и только после этого создавать новый первичный ключ. Появится сообщение, предупреждающее об автоматическом удалении в ходе процесса всех существующих связей.  
  
 Ключевой столбец-источник идентифицируется символом первичного ключа в соответствующем селекторе строк.  
  
 Если первичный ключ состоит более чем из одного столбца, то в одном столбце могут встречаться дублирующиеся значения, но все сочетания значений изо всех столбцов первичного ключа должны быть уникальными.  
  
 При определении составного ключа порядок столбцов в первичном ключе совпадает с порядком столбцов, показанным в таблице. Однако после создания первичного ключа порядок столбцов можно изменить. Дополнительные сведения см. в разделе [Изменение первичных ключей](modify-primary-keys.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-primary-key-in-an-existing-table"></a>Создание первичного ключа в существующей таблице  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается первичный ключ в столбце `TransactionID`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Production.TransactionHistoryArchive   
    ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID);  
    GO  
  
    ```  
  
#### <a name="to-create-a-primary-key-in-a-new-table"></a>Создание первичного ключа в новой таблице  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается таблица и определяется первичный ключ для столбца `TransactionID`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
    );  
    GO  
  
    ```  
  
     Дополнительные сведения см. в разделах [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) и [table_constraint (Transact-SQL)](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).  
  
###  <a name="TsqlExample"></a>  
