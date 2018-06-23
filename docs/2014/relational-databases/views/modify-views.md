---
title: Изменение представлений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-views
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- views [SQL Server], renaming
- views [SQL Server], modifying
- modifying views
- renaming views
ms.assetid: 2d3c14dc-43e5-4324-b8fb-f2692d330b16
caps.latest.revision: 22
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3fe3a0c782ef3e4fadd93139f4c4e00b56bb86bb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099250"
---
# <a name="modify-views"></a>Изменение представлений
  После определения представления это определение можно изменить в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] без удаления и повторного создания представления с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Изменение представления с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Изменение представлений не влияет ни на какие зависимые объекты, например хранимые процедуры или триггеры, до тех пор пока определение представления не будет изменено таким образом, что зависимый объект станет недопустимым.  
  
-   При изменении текущего представления с помощью инструкции ALTER VIEW компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] осуществляет монопольную блокировку схемы представления. Если блокировка предоставлена, и с представлением в настоящий момент не работает ни один пользователь, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] удаляет все копии представления из кэша процедур. Существующие планы, ссылающиеся на представление, остаются в кэше, но при обращении к ним выполняется повторная компиляция.  
  
-   Инструкцию ALTER VIEW можно выполнять для индексированных представлений, однако она удаляет все индексы представления.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для выполнения инструкции ALTER VIEW необходимо как минимум разрешение ALTER на объект.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-a-view"></a>Изменение представления  
  
1.  В **обозревателе объектов**щелкните знак «плюс» рядом с базой данных, в которой содержится представление, а затем щелкните знак «плюс» рядом с папкой **Представления** .  
  
2.  Щелкните правой кнопкой мыши представление, которое нужно изменить, и выберите пункт **Конструктор**.  
  
3.  На панели диаграмм конструктора запросов внесите изменения в представление одним из следующих способов.  
  
    1.  Установите или снимите флажки элементов, которые необходимо добавить или удалить.  
  
    2.  Щелкните правой кнопкой мыши на панели диаграмм, выберите **Добавить таблицу…**, а затем выберите дополнительные столбцы, которые необходимо добавить к представлению в диалоговом окне **Добавить таблицу** .  
  
    3.  Щелкните правой кнопкой мыши строку заголовка таблицы, которую необходимо удалить, и выберите **Удалить**.  
  
4.  В меню **Файл** выберите команду **Сохранить***имя представления*.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-modify-a-view"></a>Изменение представления  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере сначала создается представление, а затем оно изменяется с помощью инструкции ALTER VIEW. Предложение WHERE добавляется к определению представления.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    -- Create a view.  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
  
    -- Modify the view by adding a WHERE clause to limit the rows returned.  
    ALTER VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID  
    WHERE HireDate < CONVERT(DATETIME,'20020101',101) ;   
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [ALTER VIEW (Transact-SQL)](/sql/t-sql/statements/alter-view-transact-sql).  
  
  
