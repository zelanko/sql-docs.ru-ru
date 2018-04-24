---
title: Изменение столбцов (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying data types
- column data types [SQL Server]
- data types [SQL Server], columns
ms.assetid: b67b95c5-61ef-4bd8-9a3e-1640eb7583ac
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7ffdd8c6eaa007b0b06b69c02f37ef54a9299f92
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="modify-columns-database-engine"></a>Изменение столбцов (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Изменить тип данных столбца в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или в [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!WARNING]  
>  Изменение типа данных столбца, в котором уже есть данные, может привести к полной потере данных при преобразовании существующих данных в новый тип. Кроме того, код и приложения, которые используют измененный столбец, могут завершиться сбоем. Это касается запросов, представлений, хранимых процедур, определяемых пользователем функций и клиентских приложений. Следует иметь в виду, что возникновение ошибок происходит каскадом. Например, может произойти сбой хранимой процедуры, которая вызывает определяемую пользователем функцию, зависящую от изменяемого столбца. Внимательно рассмотрите любые изменения, которые необходимо сделать со столбцом таблицы.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Изменение типа данных столбца с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-the-data-type-of-a-column"></a>Изменение типа данных столбца  
  
1.  В **Обозревателе объектов**щелкните правой кнопкой мыши таблицу со столбцами, масштаб которых необходимо изменить, и выберите пункт **Конструктор**.  
  
2.  Выберите столбец, тип данных которого планируется изменить.  
  
3.  На вкладке **Свойства столбца** выберите ячейку сетки для свойства **Тип данных** и выберите новый тип данных из раскрывающегося списка.  
  
4.  В меню **Файл** выберите пункт **Сохранить***имя_таблицы*.  
  
> [!NOTE]  
>  При изменении типа данных столбца конструктор таблиц применяет длину типа данных, определенную по умолчанию для выбранного типа данных, даже если была указана другая длина. Всегда устанавливайте необходимое значение длины типа данных после того, как был указан тип данных.  
  
> [!WARNING]  
>  При попытке изменения типа данных столбца, связанного с другими таблицами, конструктор таблиц запрашивает подтверждение на внесение изменений и в столбцы других таблиц.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-modify-the-data-type-of-a-column"></a>Изменение типа данных столбца  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    CREATE TABLE dbo.doc_exy (column_a INT ) ;  
    GO  
    INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
    GO  
    ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
    GO  
  
    ```  
  
 Дополнительные сведения см. в разделе [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md).  
  
  
