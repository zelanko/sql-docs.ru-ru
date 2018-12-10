---
title: Занятие 3. Определение набора данных для табличного отчета (службы Reporting Services) | Документы Майкрософт
ms.date: 05/23/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 60f613e075c032faa9e81b30a48b9d6f630c0b5c
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52516985"
---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a>Занятие 3. Определение набора данных для табличного отчета (службы Reporting Services)
После определения источника данных необходимо определить набор данных. В службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]данные, используемые в отчетах, содержатся в *наборе данных*. Набор данных содержит указатель на источник данных и запрос, используемый в отчете, а также вычисляемые поля и переменные.  
  
Чтобы создать набор данных, можно использовать конструктор запросов в конструкторе отчетов. В этом учебнике предстоит создать запрос, получающий из базы данных [!INCLUDE [ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] сведения о заказах на продажу.  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a>Определение запроса Transact-SQL для данных отчета  
  
1.  В области **данных отчета** нажмите кнопку **Создать** и выберите **Набор данных...**. Откроется диалоговое окно **Свойства набора данных** .  
  
2.  В поле **Имя** введите **AdventureWorksDataset**.  
  
3.  Щелкните **Использовать набор данных, внедренный в отчет**.  
  
4.  Выберите источник данных, созданный с помощью предыдущих инструкций ([!INCLUDE [ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)]).   
5. Выберите **Текст** в качестве **типа запроса**.  
  
6.  Введите или скопируйте и вставьте приведенный ниже запрос Transact-SQL в поле **Запрос** .  
  
    ```  
    SELECT   
       soh.OrderDate AS [Date],   
       soh.SalesOrderNumber AS [Order],   
       pps.Name AS Subcat, pp.Name as Product,    
       SUM(sd.OrderQty) AS Qty,  
       SUM(sd.LineTotal) AS LineTotal  
    FROM Sales.SalesPerson sp   
       INNER JOIN Sales.SalesOrderHeader AS soh   
          ON sp.BusinessEntityID = soh.SalesPersonID  
       INNER JOIN Sales.SalesOrderDetail AS sd   
          ON sd.SalesOrderID = soh.SalesOrderID  
       INNER JOIN Production.Product AS pp   
          ON sd.ProductID = pp.ProductID  
       INNER JOIN Production.ProductSubcategory AS pps   
          ON pp.ProductSubcategoryID = pps.ProductSubcategoryID  
       INNER JOIN Production.ProductCategory AS ppc   
          ON ppc.ProductCategoryID = pps.ProductCategoryID  
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,   
       soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'  
    ```  
  
7.  Нажмите кнопку **Конструктор запросов** (необязательно). В текстовом конструкторе запросов будет отображен запрос. Вы можете переключиться к графическому конструктору запросов, нажав кнопку **Изменить как текст**. Чтобы просмотреть результаты выполнения запроса, нажмите кнопку выполнения ![ssrs_querydesigner_run](../reporting-services/media/ssrs-querydesigner-run.png)  на панели инструментов конструктора запросов.  
  
    Будут показаны данные из шести полей четырех различных таблиц из базы данных [!INCLUDE [ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] . В запросе используется возможность псевдонимов языка Transact-SQL. Например, таблица SalesOrderHeader называется *soh*.  
  
8.  Нажмите кнопку **ОК** для выхода из конструктора запросов.  
  
9.  Нажмите кнопку **ОК** для выхода из диалогового окна **Свойства набора данных** .  
  
    Поля и набор данных **AdventureWorksDataset** появятся в области данных отчета.  
    ![ssrs_adventureworksdataset](../reporting-services/media/ssrs-adventureworksdataset.png)  
  
## <a name="next-task"></a>Следующая задача  
Определен запрос, получающий данные для отчета. Далее предстоит создать макет отчета. См. [Занятие 4. Добавление таблицы в отчет (службы Reporting Services)](../reporting-services/lesson-4-adding-a-table-to-the-report-reporting-services.md).  
  
## <a name="see-also"></a>См. также:  
[Средства проектирования запросов (службы SSRS)](../reporting-services/report-data/query-design-tools-ssrs.md)  
[Тип соединения SQL Server (службы SSRS)](../reporting-services/report-data/sql-server-connection-type-ssrs.md)  
[Учебник. Составление инструкций Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
  

