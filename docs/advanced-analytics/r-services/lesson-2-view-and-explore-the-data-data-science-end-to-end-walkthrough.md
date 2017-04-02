---
title: "Занятие&#160;2. Просмотр и изучение данных (пошаговое руководство по обработке и анализу данных) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: d3835d6d-e68b-486d-81a0-81b717cc6134
caps.latest.revision: 32
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 26
---
# Занятие&#160;2. Просмотр и изучение данных (пошаговое руководство по обработке и анализу данных)
Изучение данных — важный этап моделирования. Он включает в себя просмотр сводок по объектам данных, которые будут использоваться при анализе, а также визуализацию данных. На этом занятии вы изучите объекты данных и построите графики как с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] , так и с помощью функций R, входящих в состав служб [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
Затем вы создадите графики для визуализации данных с помощью новых функций из пакетов, устанавливаемых вместе с [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
> [!TIP]  
> Хорошо владеете языком R?  
>   
> Скачав все данные и подготовив среду, вы сможете выполнить скрипт R в RStudio или любой другой среде, чтобы изучить его возможности самостоятельно. Просто откройте файл RSQL_Walkthrough.R, а затем выделите и выполните отдельные строки или запустите весь скрипт в целях демонстрации.  
>   
> Чтобы получить дополнительное описание функций RevoScaleR и советы по работе с данными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в R, продолжайте выполнение учебника. В нем используется тот же скрипт.  
  
## <a name="verify-downloaded-data-using-sql"></a>Проверка скачанных данных с помощью SQL  
Сначала проверьте, правильно ли были загружены данные.  
  
1.  Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    Для подключения к базам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их просмотра можно использовать различные средства.  
  
    -   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]    
    -   Обозреватель сервера в Visual Studio  
  
2.  Разверните созданную базу данных. На рисунке ниже показана новая база данных, таблицы и функции в **обозревателе сервера**.  
  
    ![new database objects created by script](../../advanced-analytics/r-services/media/rsql-e2e-ssms-newobjects.PNG "new database objects created by script")  
  
3.  Вы также можете выполнять простые запросы к данным. Например, в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]щелкните таблицу правой кнопкой мыши и выберите пункт **Выделить 1000 верхних строк** , чтобы создать и выполнить следующий запрос:  
  
    ```  
    SELECT TOP 1000 * FROM [dbo].[nyctaxi_sample]  
    ```  
    Если в таблице не отображаются данные, см. раздел [Устранение неполадок](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md) в предыдущей статье.
      
4.  Для просмотра схемы и типов данных можно использовать системные административные управления в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```  
    SELECT TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME, COLUMN_DEFAULT  
    FROM [TaxiSample].INFORMATION_SCHEMA.COLUMNS  
    WHERE TABLE_NAME = N'nyctaxi_sample';  
    ```  
  
    > [!TIP]  
    > Чтобы получить подробные сведения о том, как была создана таблица данных, можно также просмотреть скрипт `create-db-tb-upload-data.sql`.  
  
### <a name="generate-summaries-using-sql"></a>Создание сводок с помощью SQL  
Одним из преимуществ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , делающих его использование в сочетании с языком R эффективным, является возможность выполнять вычисления на основе наборов очень быстро.  Код, с помощью которого была создана таблица в этом пошаговом руководстве, также можно использовать для [индекса columnstore](../Topic/Columnstore%20Indexes%20Guide.md), чтобы еще больше ускорить вычисления.   
  
```  
SELECT DISTINCT [passenger_count]  
    , ROUND (SUM ([fare_amount]),0) as TotalFares   
    , ROUND (AVG ([fare_amount]),0) as AvgFares  
FROM [dbo].[nyctaxi_sample]  
GROUP BY [passenger_count]   
ORDER BY  AvgFares desc  
```  

В следующем шаге вы используете язык R для создания более сложных сводок и диаграмм с помощью данных на сервере SQL Server.  
  
## <a name="next-steps"></a>Следующие шаги  
[Просмотр и обобщение данных с помощью языка R (пошаговое руководство по обработке и анализу данных)](../../advanced-analytics/r-services/view-and-summarize-data-using-r-data-science-end-to-end-walkthrough.md)  
  
[Создание диаграмм и графиков с помощью R (пошаговое руководство по обработке и анализу данных)](../../advanced-analytics/r-services/create-graphs-and-plots-using-r-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Предыдущее занятие  
[Занятие 1. Подготовка данных (пошаговое руководство по обработке и анализу данных)](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
## <a name="see-also"></a>См. также:  
[Руководство по индексам columnstore](../Topic/Columnstore%20Indexes%20Guide.md)  
  
  
  
