---
title: Создание таблиц (ядро СУБД) | Документация Майкрософт
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
- table creation [SQL Server], Visual Database Tools
ms.assetid: 6f7c6ac5-e6d3-4dca-831e-b28442ba535b
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e4a25a40c2af9d5c5d636a8576ee487135009a24
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102159"
---
# <a name="create-tables-database-engine"></a>Создание таблиц (компонент Database Engine)
  Предусмотрена возможность создавать новые таблицы, присваивать им имена и добавлять к существующим базам данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , используя [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  При подключении к базе данных SQL Azure новый параметр таблицы запускает скрипт создания шаблона таблицы. Измените параметры, затем запустите скрипт для создания новой таблицы. Дополнительные сведения см. в разделе [Общие сведения о SQL Azure](http://go.microsoft.com/fwlink/?LinkId=163948).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Чтобы создать таблицу, с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требует разрешения CREATE TABLE в базе данных и разрешения ALTER на схему, в которой создается таблица.  
  
 Если какие-либо столбцы в инструкции CREATE TABLE определены как принадлежащие к определяемому пользователем типу данных CLR, необходимо быть владельцем данного типа либо иметь разрешение REFERENCES на него.  
  
 Если какие-либо столбцы в инструкции CREATE TABLE имеют связанную коллекцию схем XML, необходимо быть владельцем этого набора схем или иметь разрешение REFERENCES на него.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-table-with-table-designer"></a>Создание таблицы в конструкторе таблиц  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , который содержит изменяемую базу данных.  
  
2.  В **обозревателе объектов**разверните узел **Базы данных** , а затем базу данных, в которой будет размещена новая таблица.  
  
3.  В обозревателе объектов щелкните правой кнопкой мыши узел **Таблицы** базы данных и выберите **Создать таблицу**.  
  
4.  Введите имена столбцов, выберите типы данных и определите для каждого столбца, могут ли в нем присутствовать значения NULL, как показано на следующей иллюстрации.  
  
     ![AddColumnsinTableDesigner](../../database-engine/media/addcolumnsintabledesigner.gif "AddColumnsinTableDesigner")  
  
5.  Вы также можете задать другие свойства столбца, например является ли этот столбец столбцом идентификаторов или вычисляемым столбцом. Для этого щелкните столбец на вкладке свойств столбцов. Дополнительные сведения о свойствах столбцов см. в разделе [Свойства столбца таблицы (среда SQL Server Management Studio)](table-column-properties-sql-server-management-studio.md).  
  
6.  Чтобы указать, что столбец является столбцом первичного ключа, щелкните его правой кнопкой мыши и выберите **Задать первичный ключ**. Дополнительные сведения см. в статье [Create Primary Keys](../tables/create-primary-keys.md).  
  
7.  Чтобы создать связи по внешнему ключу, проверочные ограничения или индексы, щелкните правой кнопкой мыши панель конструктора таблиц и выберите из списка объект, как показано на следующей иллюстрации.  
  
     ![AddTableObjects](../../database-engine/media/addtableobjects.gif "AddTableObjects")  
  
     Дополнительные сведения об этих объектах см. в разделах [Create Foreign Key Relationships](../tables/create-foreign-key-relationships.md), [Create Check Constraints](../tables/create-check-constraints.md) и [Indexes](../indexes/indexes.md).  
  
8.  По умолчанию таблица содержится в схеме **dbo** . Чтобы указать другую схему для таблицы, щелкните правой кнопкой мыши панель конструктора таблиц и выберите **Свойства** , как показано на следующей иллюстрации. Выберите нужную схему из раскрывающегося списка **Схема** .  
  
     ![Specifyatableschema](../../database-engine/media/specifyatableschema.gif "Specifyatableschema")  
  
     Дополнительные сведения о схемах см. в разделе [Create a Database Schema](../security/authentication-access/create-a-database-schema.md).  
  
9. В меню **Файл** выберите команду **Сохранить** *table name*.  
  
10. В диалоговом окне **Выбор имени** введите имя таблицы и нажмите кнопку **OK**.  
  
11. Чтобы просмотреть новую таблицу, в **обозревателе объектов**разверните узел **Таблицы** , а затем нажмите клавишу **F5** , чтобы обновить список объектов. Новая таблица будет отображена в списке таблиц.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-table-in-the-query-editor"></a>Создание таблицы в редакторе запросов  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    CREATE TABLE dbo.PurchaseOrderDetail  
    (  
        PurchaseOrderID int NOT NULL  
        ,LineNumber smallint NOT NULL  
        ,ProductID int NULL  
        ,UnitPrice money NULL  
        ,OrderQty smallint NULL  
        ,ReceivedQty float NULL  
        ,RejectedQty float NULL  
        ,DueDate datetime NULL  
    );  
    ```  
  
 Дополнительные сведения см. в разделе [CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql).  
  
  
