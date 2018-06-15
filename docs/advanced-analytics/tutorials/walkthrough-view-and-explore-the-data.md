---
title: Просмотр и изучение данных с помощью SQL (Пошаговое руководство) | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b933337c1234f09f0a8963c1979a86a9ab61db53
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31201736"
---
# <a name="view-and-explore-the-data-using-sql-walkthrough"></a>Просмотр и изучение данных с помощью SQL (Пошаговое руководство)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

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
