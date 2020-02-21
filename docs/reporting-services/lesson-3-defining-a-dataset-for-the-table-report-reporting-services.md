---
title: Урок 3. Определение набора данных для табличного отчета | Документация Майкрософт
description: После определения источника данных для отчета с разбивкой на страницы необходимо определить набор данных. В SQL Server Reporting Services используемые для отчетов данные содержатся в наборе данных.
ms.date: 05/01/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 25c62e0cd615748a764937d6dc2b8e4c952e59a1
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75244307"
---
# <a name="lesson-3-define-a-dataset-for-the-table-report---sql-server-reporting-services"></a>Урок 3. Определение набора данных для табличного отчета (SQL Server Reporting Services)

После определения источника данных для отчета с разбивкой на страницы необходимо определить набор данных. В службах [!INCLUDE[ssrsnoversion](../includes/ssrsnoversion-md.md)]данные, используемые в отчетах, содержатся в *наборе данных*. Набор данных содержит указатель на источник данных и запрос, который будет использоваться в отчете, вычисляемых полях и переменных.

Чтобы определить набор данных, используйте конструктор запросов в конструкторе отчетов. В этом учебнике вы создадите запрос, который возвращает данные о заказах на продажу из базы данных AdventureWorks2016.

## <a name="define-a-transact-sql-query-for-report-data"></a>Определение запроса Transact-SQL для данных отчета  

1. В области **Данные отчета** выберите **Создать** > **Набор данных...** Откроется диалоговое окно **Свойства набора данных** с отображенным разделом **Запрос**.

    ![vs-data_set_properties_dialog](media/lesson-3-defining-a-dataset-for-the-table-report-reporting-services/vs-dataset-properties-dialog.png)

2. В текстовом поле **Имя** введите AdventureWorksDataset.

3. Ниже выберите переключатель **Использовать набор данных, внедренный в отчет**.

4. Из раскрывающегося списка **Источник данных** выберите AdventureWorks2016.

5. В наборе переключателей **Тип запроса** выберите вариант **Текст**.

6. Введите или скопируйте и вставьте следующий запрос Transact-SQL в текстовое поле **Запрос**.

    ```T-SQL
    SELECT
       soh.OrderDate AS [Date],
       soh.SalesOrderNumber AS [Order],
       pps.Name AS [Subcat],
       pp.Name as [Product],
       SUM(sd.OrderQty) AS [Qty],
       SUM(sd.LineTotal) AS [LineTotal]
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
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'
    ```

7. (Необязательный шаг.) Нажмите кнопку **Конструктор запросов**. Запрос отобразится в текстовом *конструкторе запросов*. Чтобы просмотреть результат выполнения запроса, нажмите кнопку ![ssrs_querydesigner_run](media/ssrs-querydesigner-run.png) **запуска** на панели инструментов **Конструктор запросов**. Отображаемый здесь набор данных содержит шесть полей из четырех таблиц базы данных AdventureWorks2016. В запросе используется возможность псевдонимов языка Transact-SQL. Например, таблица SalesOrderHeader называется *soh*.

8. Щелкните **ОК**, чтобы выйти из **конструктора запросов**.

9. Щелкните **ОК**, чтобы выйти из диалогового окна **Свойства набора данных**.

Панель **Данные отчета** теперь отображает набор данных AdventureWorksDataset и его поля.

   ![ssrs_adventureworksdataset](media/ssrs-adventureworksdataset.png)

## <a name="next-steps"></a>Дальнейшие действия

Итак, вы успешно определили запрос, получающий данные для отчета. Теперь вам нужно создать макет отчета. Переходите к статье [Занятие 4. Добавление таблицы в отчет (службы Reporting Services)](lesson-4-adding-a-table-to-the-report-reporting-services.md).

## <a name="see-also"></a>См. также раздел

[Средства проектирования запросов](../reporting-services/report-data/query-design-tools-ssrs.md)
[Тип соединения SQL Server (службы SSRS)](../reporting-services/report-data/sql-server-connection-type-ssrs.md)
[Руководство. Составление инструкций Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md)
