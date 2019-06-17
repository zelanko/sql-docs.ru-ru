---
title: Урок 10. Создание секций | Документация Майкрософт
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dce53a4b4ae5a64a898eec2b30921fe7a7f2e242
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65404256"
---
# <a name="lesson-10-create-partitions"></a>Урок 10. Создание секций
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии вы создадите секции, чтобы разделить таблицу FactInternetSales на более мелкие логические части, которые могут обрабатываться (обновляться) независимо от других секций. По умолчанию каждая таблица, включенная в модель имеет одну секцию, которая включает все столбцы и строки таблицы. Для таблицы FactInternetSales нам необходимо разделить данные по годам; одной секции на каждые пять лет таблицы. После этого каждую секцию можно обработать независимо. Дополнительные сведения см. в разделе [Секции](../tabular-models/partitions-ssas-tabular.md).  
  
Предполагаемое время для выполнения этого занятия: **15 минут**  
  
## <a name="prerequisites"></a>предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач на этом занятии, необходимо завершить предыдущее занятие: [Занятие 9. Создание иерархий](lesson-9-create-hierarchies.md).  
  
## <a name="create-partitions"></a>Создание секций  
  
#### <a name="to-create-partitions-in-the-factinternetsales-table"></a>Чтобы создать секции в таблице FactInternetSales  
  
1.  В обозревателе табличных моделей разверните **таблиц**, щелкните правой кнопкой мыши **FactInternetSales** > **секций**.  
  
2.  В диалоговом окне диспетчера секций щелкните **копирования**.  
  
3.  В **имя секции**, измените имя на **FactInternetSales2010**.  
  
    > [!TIP]  
    > Обратите внимание, что имена столбцов в окне предварительного просмотра таблицы отображают столбцы, включенные в таблицу модели (checked) с именами столбцов из источника. Это происходит, потому что окно «Предварительный просмотр таблицы» отображает столбцы из исходной таблицы, а не из таблицы модели.  
  
4.  Выберите **SQL** кнопка просто выше в правой части окна предварительного просмотра, чтобы открыть редактор инструкции SQL.  
  
    Поскольку необходимо, чтобы секция включала только строки из определенного периода, используйте предложение WHERE. Предложение WHERE можно создать только с помощью инструкции SQL.  
  
5.  В **инструкции SQL** поле, замените существующую инструкцию, скопируйте и вставьте следующую инструкцию:  
  
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
  
1.  В списке секций щелкните **FactInternetSales2010** секции вы только что создали, а затем нажмите кнопку **копирования**.  
  
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
  
#### <a name="to-create-a-partition-for-the-2014-year"></a>Создание секции для 2014 года  
  
- Следуйте указаниям, используя следующее предложение WHERE. 
  
    ```  
    WHERE (([OrderDate] >= N'2014-01-01 00:00:00') AND ([OrderDate] < N'2015-01-01 00:00:00'))  
    ```  

## <a name="delete-the-factinternetsales-partition"></a>Удаление секции FactInternetSales
Теперь, когда у вас есть секции для каждого года, можно удалить секцию FactInternetSales. Это предотвращает перекрытие при выборе всех процессов, при обработке секций.
#### <a name="to-delete-the-factinternetsales-partition"></a>Для удаления секции FactInternetSales
-  Щелкните секцию FactInternetSales и нажмите кнопку **удалить**.



## <a name="process-partitions"></a>Обработка секций  
В диспетчере секций Обратите внимание, что **последняя обработка** столбца для каждой новой секции показан только что создали, эти секции никогда не будут обработаны. Во время создания новых секций нужно запустить операцию обработки секций или обработки таблиц для обновления данных в этих секциях.  
  
#### <a name="to-process-the-factinternetsales-partitions"></a>Для обработки секций FactInternetSales  
  
1.  Нажмите кнопку **ОК** чтобы закрыть диалоговое окно диспетчера секций.  
  
2.  Нажмите кнопку **FactInternetSales** таблицы, а затем щелкните **модели** меню > **процесс** > **обработать секции**.  
  
3.  В диалоговом окне Обработка секций проверьте **режим** присваивается **обработка по умолчанию**.  
  
4.  Установите флажок в столбце **Обработка** для каждой из пяти созданных секций и нажмите кнопку **OK**.  

    ![как табличных lesson10-Обработка секций](media/as-tabular-lesson10-process-partitions.png)
  
    Если будет предложено ввести учетные данные олицетворения, введите имя пользователя Windows и пароль, указанные на занятии 2.  
  
    Откроется диалоговое окно **Обработка данных** со сведениями обработки для каждой секции. Обратите внимание, что для каждой секции передается различное количество строк. Это происходит, потому что каждая секция включает только строки для года, указанного с помощью предложения WHERE в инструкции SQL. По завершении обработки закройте диалоговое окно "Обработка данных".  
  
    ![как табличные lesson10-процесс — завершение](media/as-tabular-lesson10-process-complete.png)
  
 ## <a name="whats-next"></a>Дальнейшие действия
Перейдите к следующему занятию: [Занятие 11. Создание ролей](lesson-11-create-roles.md). 
