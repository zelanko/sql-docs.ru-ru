---
title: Урок 3. Определение набора данных для табличного отчета (службы Reporting Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f57ec59753e7539107c652d60f7a00959f95cbb
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56009676"
---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a>Урок 3. Определение набора данных для табличного отчета (службы Reporting Services)
  После определения источника данных необходимо определить набор данных. В службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]данные, используемые в отчетах, содержатся в *наборе данных*. Набор данных содержит указатель на источник данных и запрос, используемый в отчете, а также вычисляемые поля и переменные.  
  
 Чтобы создать запрос, можно использовать «Конструктор запросов». В этом руководстве вы создадите запрос, возвращающий данные заказов на продажу из [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] **2008** базы данных.  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a>Определение запроса Transact-SQL для данных отчета  
  
1.  В области **данных отчета** нажмите кнопку **Создать** и выберите **Набор данных...**. Откроется диалоговое окно **Свойства набора данных** .  
  
2.  В поле **Имя** введите **AdventureWorksDataset**.  
  
3.  Щелкните **Использовать набор данных, внедренный в отчет**.  
  
4.  Убедитесь, что имя источника данных AdventureWorks2012, находится в **источника данных** текстовое поле и что **тип запроса** — **текст**.  
  
5.  Введите или скопируйте и вставьте приведенный ниже запрос Transact-SQL в поле **Запрос** .  
  
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
  
6.  Нажмите кнопку **Конструктор запросов** (необязательно). В текстовом конструкторе запросов будет отображен запрос. Вы можете переключиться к графическому конструктору запросов, нажав кнопку **Изменить как текст**. Просмотреть результаты запроса, нажав кнопку запуска **(!)**  кнопку на панели инструментов конструктора запросов.  
  
     Будут показаны данные из шести полей четырех различных таблиц из базы данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] . В запросе используется возможность псевдонимов языка Transact-SQL. Например, таблица SalesOrderHeader называется soh.  
  
     Нажмите кнопку **ОК** для выхода из конструктора запросов.  
  
7.  Нажмите кнопку **ОК** для выхода из диалогового окна **Свойства набора данных** .  
  
     Поля и набор данных **AdventureWorksDataset** появятся в области данных отчета.  
  
## <a name="next-task"></a>Следующая задача  
 Определен запрос, получающий данные для отчета. Далее предстоит создать макет отчета. См. в разделе [урок 4: Добавление таблицы в отчет &#40;службы Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md).  
  
## <a name="see-also"></a>См. также  
 [Средства проектирования в отчет конструктора SQL Server Data Tools запросов &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md)   
 [Тип соединения SQL Server (службы SSRS)](report-data/sql-server-connection-type-ssrs.md)   
 [Учебник. Составление инструкций Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
