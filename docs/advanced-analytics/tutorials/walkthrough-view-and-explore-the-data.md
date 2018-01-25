---
title: "Просмотр и изучение данных с помощью SQL (Пошаговое руководство) | Документы Microsoft"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: d3835d6d-e68b-486d-81a0-81b717cc6134
caps.latest.revision: "33"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 49b3174910ca8b5ce1b590f1205bc3d134b76f4b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="view-and-explore-the-data-using-sql-walkthrough"></a>Просмотр и изучение данных с помощью SQL (Пошаговое руководство)

Изучение данных — важный этап моделирования. Он включает в себя просмотр сводок по объектам данных, которые будут использоваться при анализе, а также визуализацию данных. На этом занятии просмотра объектов данных и создавать диаграммы, с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] и функций R, включенных в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

Затем создание диаграмм для визуализации данных, с помощью новых функций, предоставляемых пакеты, установленные с [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

> [!TIP]
> Хорошо владеете языком R?
>   
> Скачав все данные и подготовив среду, вы сможете выполнить скрипт R в RStudio или любой другой среде, чтобы изучить его возможности самостоятельно. Просто откройте файл RSQL_Walkthrough.R, а затем выделите и выполните отдельные строки или запустите весь скрипт в целях демонстрации.
>   
> Чтобы получить дополнительное описание функций RevoScaleR и советы по работе с данными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в R, продолжайте выполнение учебника. В нем используется тот же скрипт.

## <a name="verify-downloaded-data-using-sql-server"></a>Проверка загруженных данных, с помощью SQL Server

Сначала проверьте, правильно ли были загружены данные.

1. Подключиться к вашей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра с помощью вашего любимого средство управления базами данных, таких как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], обозреватель серверов в Visual Studio или Visual Studio Code.

2. Выберите базу данных был создан и разверните, чтобы увидеть новую базу данных, таблицы и функции.
  
    ![rsql_e2e_ssms_newobjects](media/rsql-e2e-ssms-newobjects.PNG)
  
3.  Чтобы убедиться, что данные загружены правильно, щелкните правой кнопкой мыши таблицу и выберите **выделить 1000 ВЕРХНИХ строк**. Пункт меню в выполнении этого запроса:

    ```SQL
    SELECT TOP 1000 * FROM [dbo].[nyctaxi_sample]
    ```
    Если в таблице не отображаются данные, см. раздел [Устранение неполадок](walkthrough-prepare-the-data.md) в предыдущей статье.

4. Эта таблица данных оптимизирована для вычислений с использованием наборов путем добавления [индекса columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md). Выполните следующую инструкцию для создания краткую сводку для таблицы.

    ```SQL
    SELECT DISTINCT [passenger_count]
        , ROUND (SUM ([fare_amount]),0) as TotalFares
        , ROUND (AVG ([fare_amount]),0) as AvgFares
    FROM [dbo].[nyctaxi_sample]
    GROUP BY [passenger_count]
    ORDER BY  AvgFares DESC
    ````
    На следующем занятии вы создадите более сложные сводки с помощью языка R.

## <a name="next-lesson"></a>Следующее занятие

[Сведение данных с помощью R](walkthrough-view-and-summarize-data-using-r.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Подготовка данных с помощью PowerShell](walkthrough-prepare-the-data.md)
