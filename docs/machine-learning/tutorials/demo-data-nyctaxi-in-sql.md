---
title: Демонстрационные данные по работе такси в Нью-Йорке для учебников
description: Создание базы данных, содержащей выборку данных о поездках в такси по Нью-Йорку. Этот набор данных используется в руководствах по Python и R для Служб машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 10/31/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||>=azuresqldb-mi-current'
ms.openlocfilehash: 77bcd682aa8d58437421134a697bcb715efe595d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470475"
---
# <a name="nyc-taxi-demo-data-for-sql-server-python-and-r-tutorials"></a>Демонстрационные данные по работе такси в Нью-Йорке для учебников по Python и R в SQL Server
[!INCLUDE [SQL Server 2016 SQL MI](../../includes/applies-to-version/sqlserver2016-asdbmi.md)]

В этой статье объясняется, как настроить демонстрационную базу данных, состоящую из общедоступных данных [Комиссии по такси и лимузинам Нью-Йорка](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml). Эти данные используются в нескольких учебниках по R и Python для аналитики в базе данных в SQL Server. Чтобы пример кода выполнялся быстрее, была создана репрезентативная выборка в объеме 1 % данных. В вашей системе файл резервной копии базы данных немного превышает 90 МБ и представляет 1,7 млн строк в основной таблице данных.

Для выполнения этого упражнения потребуется [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md?view=sql-server-2017&preserve-view=true) или другое средство, которое может восстанавливать файл резервной копии базы данных и выполнять запросы T-SQL.

Этот набор данных используется в следующих учебниках и кратких руководствах:

+ [Изучение аналитики в базе данных с помощью R в SQL Server](r-taxi-classification-introduction.md)
+ [Изучение аналитики в базе данных с помощью Python в SQL Server](python-taxi-classification-introduction.md)

## <a name="download-files"></a>Загрузка файлов

Демонстрационная база данных — это BAK-файл SQL Server 2016, размещенный корпорацией Майкрософт. Этот файл можно восстановить в SQL Server 2016 и более поздних версий. Скачивание файла начинается сразу же после нажатия ссылки. 

Размер файла составляет приблизительно 90 МБ.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15"
>[!NOTE]
>Чтобы восстановить пример базы данных в [кластерах больших данных SQL Server](../../big-data-cluster/big-data-cluster-overview.md), скачайте файл [NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak) и следуйте указаниям в разделе [Восстановление базы данных на главном экземпляре кластера больших данных SQL Server](../../big-data-cluster/data-ingestion-restore-database.md).
::: moniker-end

::: moniker range=">=azuresqldb-mi-current"
>[!NOTE]
>Чтобы восстановить пример базы данных в [службах машинного обучения в управляемом экземпляре SQL Azure](/azure/azure-sql/managed-instance/machine-learning-services-overview), следуйте инструкциям в [кратком руководстве по восстановлению базы данных в Управляемом экземпляре Azure SQL](/azure/azure-sql/managed-instance/restore-sample-database-quickstart), используя BAK-файл демонстрационной базы данных такси Нью-Йорка: [https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak).
::: moniker-end

1. Щелкните файл [NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak), чтобы скачать файл резервной копии базы данных.

2. Скопируйте этот файл в папку C:\Program files\Microsoft SQL Server\имя_экземпляра_MSSQL\MSSQL\Backup.

3. В Management Studio щелкните правой кнопкой мыши **Базы данных** и выберите **Восстановить файлы и группы файлов**.

4. В качестве имени базы данных задайте *NYCTaxi_Sample*.

5. Щелкните **С устройства**, а затем откройте страницу выбора файла, чтобы выбрать файл резервной копии. Щелкните **Добавить**, чтобы выбрать файл NYCTaxi_Sample.bak.

6. Установите флажок **Восстановить** и нажмите кнопку **ОК**, чтобы восстановить базу данных.

## <a name="review-database-objects"></a>Проверка объектов базы данных
   
Проверьте существование объектов базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Вы должны увидеть базу данных, таблицы, функции и хранимые процедуры.
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

### <a name="objects-in-nyctaxi_sample-database"></a>Объекты в базе данных NYCTaxi_Sample

В следующей таблице перечислены объекты, созданные в демонстрационной базе данных по работе такси в Нью-Йорке.

|**Имя объекта**|**Тип объекта**|**Описание**|
|----------|------------------------|---------------|
|**NYCTaxi_Sample** | База данных | Создает базу данных и две таблицы:<br /><br />Таблица dbo.nyctaxi_sample: содержит основной набор данных по работе такси в Нью-Йорке. К таблице добавляется кластеризованный индекс columnstore для оптимизации хранения данных и производительности запросов. В таблицу вставлена выборка, содержащая 1 % от общего набора данных по работе такси в Нью-Йорке.<br /><br />Таблица dbo.nyc_taxi_models: используется для сохранения обученной модели расширенной аналитики.|
|**fnCalculateDistance** |скалярная функция | Вычисляет прямое расстояние между местами посадки и высадки. Эта функция используется в занятиях [Создание компонентов данных](r-taxi-classification-create-features.md), [Обучение и сохранение модели](r-taxi-classification-train-model.md) и [Ввод модели R в эксплуатацию](r-taxi-classification-deploy-model.md).|
|**fnEngineerFeatures** |функция с табличным значением | Создает новые характеристики данных для обучения модели. Эта функция используется в занятиях [Создание характеристик данных](r-taxi-classification-create-features.md) и [Ввод модели R в эксплуатацию](r-taxi-classification-deploy-model.md).|


Хранимые процедуры создаются с помощью скриптов R и Python, которые можно найти в разных учебниках. В следующей таблице перечислены хранимые процедуры, которые при необходимости можно добавить в демонстрационную базу данных по работе такси в Нью-Йорке при выполнении скриптов из разных занятий.

|**Хранимая процедура**|**Язык**|**Описание**|
|-------------------------|------------|---------------|
|**RxPlotHistogram** |R | Вызывает функцию RevoScaleR rxHistogram для построения гистограммы на основе переменной, а затем возвращает диаграмму в виде двоичного объекта. Эта хранимая процедура используется в занятии [Анализ и визуализация данных](r-taxi-classification-explore-data.md).|
|**RPlotRHist** |R| Создает график с помощью функции Hist, а затем сохраняет результат в виде локального PDF-файла. Эта хранимая процедура используется в занятии [Анализ и визуализация данных](r-taxi-classification-explore-data.md).|
|**RxTrainLogitModel**  |R| Обучает модель логистической регрессии путем вызова пакета R. Модель прогнозирует значение для столбца tipped и обучается на основе случайной выборки, содержащей 70 % данных. Выходными данными хранимой процедуры является обученная модель, которая сохраняется в таблице nyc_taxi_models. Эта хранимая процедура используется в занятии [Обучение и сохранение модели](r-taxi-classification-train-model.md).|
|**RxPredictBatchOutput**  |R | Вызывает обученную модель для составления прогнозов с ее помощью. Хранимая процедура принимает запрос в качестве входного параметра и возвращает столбец числовых значений, представляющих оценки для входных строк. Эта хранимая процедура используется в занятии [Прогнозирование возможных результатов](r-taxi-classification-deploy-model.md).|
|**RxPredictSingleRow**  |R| Вызывает обученную модель для составления прогнозов с ее помощью. Эта хранимая процедура принимает новое наблюдение в качестве входных данных, причем отдельные значения характеристик передаются как встроенные параметры, и возвращает значение, представляющее прогнозируемый результат для нового наблюдения. Эта хранимая процедура используется в занятии [Прогнозирование возможных результатов](r-taxi-classification-deploy-model.md).|

## <a name="query-the-data"></a>Запрос данных

Для проверки выполните запрос и убедитесь, что данные были отправлены.

1. В разделе "Базы данных" обозревателя объектов щелкните правой кнопкой мыши базу данных **NYCTaxi_Sample** и запустите новый запрос.

2. Выполните несколько простых запросов:

    ```sql
    SELECT TOP(10) * FROM dbo.nyctaxi_sample;
    SELECT COUNT(*) FROM dbo.nyctaxi_sample;
    ```
База данных содержит 1,7 млн строк.

3. В базе данных имеется таблица **nyctaxi_sample**, содержащая набор данных. Эта таблица оптимизирована для вычислений с использованием наборов путем добавления [индекса columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md). Выполните эту инструкцию, чтобы создать краткую сводку для этой таблицы.

    ```sql
    SELECT DISTINCT [passenger_count]
        , ROUND (SUM ([fare_amount]),0) as TotalFares
        , ROUND (AVG ([fare_amount]),0) as AvgFares
    FROM [dbo].[nyctaxi_sample]
    GROUP BY [passenger_count]
    ORDER BY  AvgFares DESC
    ````
Результаты должны быть аналогичны показанным на следующем снимке экрана.

  ![Сводные данные по таблице](media/nyctaxidatatablesummary.png "Результаты запроса")

## <a name="next-steps"></a>Дальнейшие действия

Теперь выборка данных по работе такси в Нью-Йорке готова для использования в практическом обучении.

+ [Изучение аналитики в базе данных с помощью R в SQL Server](r-taxi-classification-introduction.md)
+ [Изучение аналитики в базе данных с помощью Python в SQL Server](python-taxi-classification-introduction.md)