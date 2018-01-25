---
title: "Копирование столбцов из одной таблицы в другую (ядро СУБД) | Документация Майкрософт"
ms.custom: 
ms.date: 09/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- copying columns
- columns [SQL Server], copying
ms.assetid: 5f5e70dc-69f9-44b8-bc48-b5d51ac20d77
caps.latest.revision: "23"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: ab6c5c510e8f1d13c5212f316d27dabcdedd1009
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="copy-columns-from-one-table-to-another-database-engine"></a>Копирование столбцов из одной таблицы в другую (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  В этом разделе описывается копирование столбцов из одной таблицы в другую, когда копируется либо только определение столбца, либо определение и данные из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Копирование столбцов с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 При копировании из одной базы данных в другую столбца, имеющего псевдоним типа данных, исходный тип данных в целевой базе данных может оказаться недоступным. В этом случае столбцу будет назначен ближайший подходящий базовый тип данных, доступный в целевой базе данных.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a>Копирование определения столбца из одной таблицы в другую  
  
1.  Щелкнув правой кнопкой мыши, откройте таблицу со столбцами, предназначенными к копированию, и таблицу, в которую необходимо выполнить копирование, затем нажмите кнопку **Разработка**.  
  
2.  Выберите вкладку исходной таблицы и выделите нужные столбцы.  
  
3.  В меню **Правка** выберите **Копировать**.  
  
4.  Выберите вкладку таблицы, в которую требуется скопировать столбцы.  
  
5.  Выделите столбец, после которого нужно поместить вставляемые столбцы, и в меню **Правка** выберите **Вставить**.  
  
#### <a name="to-copy-data-from-one-table-to-another"></a>Копирование данных из одной таблицы в другую  
  
1.  Следуйте приведенным выше инструкциям для копирования определения столбцов.  
  
    > [!NOTE]  
    >  Прежде чем скопировать данные из одной таблицы в другую, убедитесь, что типы данных целевых столбцов совместимы с типами данных исходных.  
  
2.  Откройте новое окно редактора запросов. 

3.  Щелкните редактор запросов правой кнопкой мыши и выберите **Создать запрос в редакторе**. 

4.  В диалоговом окне **Добавление таблицы** выберите исходную и целевую таблицы, нажмите кнопку **Добавить**, а затем закройте диалоговое окно **Добавление таблицы** . 

5.  Щелкните правой кнопкой мыши пустую область редактора запросов, наведите указатель на пункт **Изменить тип**и выберите **Вставить результаты**.  

6.  В диалоговом окне **Выбор целевой таблицы для инструкции Insert Results** выберите целевую таблицу. 

7.  В верхней части конструктора запросов щелкните исходный столбец исходной таблицы.

8. Конструктор запросов создал запрос INSERT. Нажмите кнопку "ОК", чтобы поместить запрос в исходное окно редактора запросов.  

9.  Выполните запрос, чтобы вставить данные из исходной таблицы в целевую.

  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a>Копирование определения столбца из одной таблицы в другую  
  
1.  Нельзя копировать отдельные столбцы из одной таблицы в другую (существующую) с использованием инструкций Transact-SQL. Однако можно создать новую таблицу в файловой группе по умолчанию и вставить в нее результирующие строки из запроса с помощью инструкции SELECT INTO. Дополнительные сведения см. в разделе [Предложение INTO (Transact-SQL)](../../t-sql/queries/select-into-clause-transact-sql.md).  
  
#### <a name="to-copy-data-from-one-table-to-another"></a>Копирование данных из одной таблицы в другую  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.EmployeeSales  
    ( BusinessEntityID   varchar(11) NOT NULL,  
      SalesYTD money NOT NULL  
    );  
    GO  
    INSERT INTO dbo.EmployeeSales  
        SELECT BusinessEntityID, SalesYTD   
        FROM Sales.SalesPerson;  
    GO  
    ```  
  
  
