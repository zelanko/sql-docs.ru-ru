---
title: "Создание первичных ключей | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- primary keys [SQL Server], creating
ms.assetid: 85c623ca-4656-4d70-a9db-ee4d897cd214
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: bc2034ac69dee1a72429e94841aec1763703de7c
ms.openlocfilehash: 182d85111f05cf2162084fade0a5a86078efbad5
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="create-primary-keys"></a>Создание первичных ключей
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

 > Материалы по предыдущим версиям SQL Server см. в разделе [Создание первичных ключей](https://msdn.microsoft.com/en-US/library/ms189039(SQL.120).aspx).

  Определить первичный ключ в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Создание первичного ключа автоматически приводит к созданию соответствующего уникального кластеризованного или некластеризованного индекса.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Создание первичного ключа с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   В таблице возможно наличие только одного ограничения по первичному ключу.  
  
-   Все столбцы с ограничением PRIMARY KEY должны иметь признак NOT NULL. Если допустимость значения NULL не указана, то для всех столбцов c ограничением PRIMARY KEY устанавливается признак NOT NULL.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
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
  
 При определении составного ключа порядок столбцов в первичном ключе совпадает с порядком столбцов, показанным в таблице. Однако после создания первичного ключа порядок столбцов можно изменить. Дополнительные сведения см. в разделе [Изменение первичных ключей](../../relational-databases/tables/modify-primary-keys.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-primary-key-in-an-existing-table"></a>Создание первичного ключа в существующей таблице  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
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
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
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
  
     Дополнительные сведения см. в разделах [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md), [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md) и [table_constraint (Transact-SQL)](../../t-sql/statements/alter-table-table-constraint-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  
