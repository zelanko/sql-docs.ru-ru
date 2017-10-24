---
title: "Занятие 11: Создание секций | Документы Microsoft"
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 57ed4f364bcc7ca144c6e963c7b550a5dcc1831d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-10-create-partitions"></a>Занятие 10. Создание секций
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии вы создадите секций, чтобы разделить таблицу FactInternetSales на более мелкие логические части, которые могут обрабатываться (обновляться) независимо от других секций. По умолчанию каждая таблица, включенная в модель, имеет одну секцию, включающую все столбцы и строки таблицы. Для таблицы FactInternetSales нам необходимо разделить данные по годам; одну секцию для каждой таблицы пять лет. После этого каждую секцию можно обработать независимо. Дополнительные сведения см. в разделе [Секции](../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
Предполагаемое время выполнения этого занятия: **15 минут**  
  
## <a name="prerequisites"></a>Предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [занятии 9: создание иерархий](../analysis-services/lesson-9-create-hierarchies.md).  
  
## <a name="create-partitions"></a>Создание секций  
  
#### <a name="to-create-partitions-in-the-factinternetsales-table"></a>Чтобы создать секции в таблицу FactInternetSales  
  
1.  В табличной модели обозревателе разверните **таблиц**, щелкните правой кнопкой мыши **FactInternetSales** > **секций**.  
  
2.  В диалоговом окне диспетчера секций щелкните **копирования**.  
  
3.  В **имя секции**, измените имя на **FactInternetSales2010**.  
  
    > [!TIP]  
    > Обратите внимание, что имена столбцов в окне предварительного просмотра таблица отображает столбцы, включенные в таблицу модели (флажок установлен) с именами столбцов из источника. Это происходит, потому что окно «Предварительный просмотр таблицы» отображает столбцы из исходной таблицы, а не из таблицы модели.  
  
4.  Выберите **SQL** кнопку над правой части окна предварительного просмотра, чтобы открыть редактор инструкции SQL.  
  
    Поскольку необходимо, чтобы секция включала только строки из определенного периода, используйте предложение WHERE. Предложение WHERE можно создать только с помощью инструкции SQL.  
  
5.  В **инструкции SQL** замените существующую инструкцию, скопировав и вставив следующую инструкцию:  
  
    ```  
    SELECT   
    [dbo].[FactInternetSales].[ProductKey],  
    [dbo].[FactInternetSales].[CustomerKey],  
    [dbo].[FactInternetSales].[PromotionKey],  
    [dbo].[FactInternetSales].[CurrencyKey],  
    [dbo].[FactInternetSales].[SalesTerritoryKey],  
    [dbo].[FactInternetSales].[SalesOrderNumber],  
    [dbo].[FactInternetSales].[SalesOrderLineNumber],  
    [dbo].[FactInternetSales].[RevisionNumber],  
    [dbo].[FactInternetSales].[OrderQuantity],  
    [dbo].[FactInternetSales].[UnitPrice],  
    [dbo].[FactInternetSales].[ExtendedAmount],  
    [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
    [dbo].[FactInternetSales].[DiscountAmount],  
    [dbo].[FactInternetSales].[ProductStandardCost],  
    [dbo].[FactInternetSales].[TotalProductCost],  
    [dbo].[FactInternetSales].[SalesAmount],  
    [dbo].[FactInternetSales].[TaxAmt],  
    [dbo].[FactInternetSales].[Freight],  
    [dbo].[FactInternetSales].[CarrierTrackingNumber],  
    [dbo].[FactInternetSales].[CustomerPONumber],  
    [dbo].[FactInternetSales].[OrderDate],  
    [dbo].[FactInternetSales].[DueDate],  
    [dbo].[FactInternetSales].[ShipDate]   
    FROM [dbo].[FactInternetSales]  
    WHERE (([OrderDate] >= N'2010-01-01 00:00:00') AND ([OrderDate] < N'2011-01-01 00:00:00'))  
    ```  
  
    Эта инструкция указывает, что секция должна включать все данные из строк, в которых OrderDate относится к 2010 календарному году, согласно предложению WHERE.  
  
6.  Нажмите кнопку **Проверить**.  
  
  
#### <a name="to-create-a-partition-for-the-2011-year"></a>Создание секции для 2011 года  
  
1.  В списке секций выберите **FactInternetSales2010** секции вы только что создали и нажмите кнопку **копирования**.  
  
2.  В **имя секции**, тип **FactInternetSales2011**.  
  
3.  Для того чтобы секция включала только строки для 2011 года, замените предложение WHERE в инструкции SQL на следующее:  
  
    ```  
    WHERE (([OrderDate] >= N'2011-01-01 00:00:00') AND ([OrderDate] < N'2012-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2012-year"></a>Создание секции для 2012 года  
  
- Следуйте указаниям, используя следующее предложение WHERE. 
  
    ```  
    WHERE (([OrderDate] >= N'2012-01-01 00:00:00') AND ([OrderDate] < N'2013-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2013-year"></a>Создание секции для 2013 года  
  
- Следуйте указаниям, используя следующее предложение WHERE. 
  
    ```  
    WHERE (([OrderDate] >= N'2013-01-01 00:00:00') AND ([OrderDate] < N'2014-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2014-year"></a>Чтобы создать раздел 2014 года  
  
- Следуйте указаниям, используя следующее предложение WHERE. 
  
    ```  
    WHERE (([OrderDate] >= N'2014-01-01 00:00:00') AND ([OrderDate] < N'2015-01-01 00:00:00'))  
    ```  

## <a name="delete-the-factinternetsales-partition"></a>Удалить раздел FactInternetSales
Теперь, когда у вас есть секции для каждого года, можно удалить раздел FactInternetSales. Это предотвращает перекрытие при выборе всех процесс при обработке секций.
#### <a name="to-delete-the-factinternetsales-partition"></a>Для удаления раздела FactInternetSales
-  Щелкните секцию FactInternetSales и нажмите кнопку **удалить**.



## <a name="process-partitions"></a>Обработка секций  
Обратите внимание, в диспетчере секций **последней обработки** столбца для каждой новой секции, созданную показаны эти разделы никогда не будут обработаны. Во время создания новых секций нужно запустить операцию обработки секций или обработки таблиц для обновления данных в этих секциях.  
  
#### <a name="to-process-the-factinternetsales-partitions"></a>Обработка секций FactInternetSales  
  
1.  Нажмите кнопку **ОК** чтобы закрыть диалоговое окно диспетчера секций.  
  
2.  Нажмите кнопку **FactInternetSales** , а затем нажмите кнопку **модели** меню > **процесс** > **Обработка секций**.  
  
3.  В диалоговом окне Обработка секций проверьте **режим** задано значение **обработка по умолчанию**.  
  
4.  Установите флажок в столбце **Обработка** для каждой из пяти созданных секций и нажмите кнопку **OK**.  

    ![как табличных lesson10-Обработка секций](../analysis-services/media/as-tabular-lesson10-process-partitions.png)
  
    Если появится предложение ввести учетные данные олицетворения, введите имя пользователя Windows и пароль, которые указаны в занятии 2.  
  
    Откроется диалоговое окно **Обработка данных** со сведениями обработки для каждой секции. Обратите внимание, что для каждой секции передается различное количество строк. Это происходит, потому что каждая секция включает только строки для года, указанного с помощью предложения WHERE в инструкции SQL. По завершении обработки закройте диалоговое окно "Обработка данных".  
  
    ![как табличных lesson10-процесса — завершение](../analysis-services/media/as-tabular-lesson10-process-complete.png)
  
 ## <a name="whats-next"></a>Дальнейшие действия
Перейдите к следующему занятию: [занятие 11: Создание ролей](../analysis-services/lesson-11-create-roles.md). 

