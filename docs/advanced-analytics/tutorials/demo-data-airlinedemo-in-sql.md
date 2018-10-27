---
title: Прибытия рейсов авиакомпании "и" задержка демонстрационных версий набора данных для SQL Server Python и R руководств | Документация Майкрософт
Description: Create a database containing the Airline dataset from R and Python. This dataset is used in exercises showing how to wrap R language or Python code in a SQL Server stored procedure.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/22/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2ba431ecbc4f7d63415fdf6b351c5135ed0cdd8d
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947448"
---
#  <a name="airline-flight-arrival-demo-data-for-sql-server-python-and-r-tutorials"></a>Авиакомпания рейсов прибытия демонстрационных данных для SQL Server Python и R руководств
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом упражнении создайте базу данных SQL Server для хранения импортированных данных из R или Python встроенные Airline demo наборов данных. R и Python дистрибутивов предоставляют эквивалентные данные, которые можно импортировать в базу данных SQL Server, с помощью Management Studio.

Для этого упражнения вам понадобится [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) или другого средства, которые могут выполнять запросы T-SQL.

Учебники и примеры использования, с помощью этого набора данных включают следующее:

+  [Создание модели Python с помощью revoscalepy](use-python-revoscalepy-to-create-model.md)

## <a name="create-the-database"></a>Создайте базу данных

1. Запустите SQL Server Management Studio, подключитесь к экземпляру ядра базы данных, с интегрированным R или Python.  

2. В обозревателе объектов щелкните правой кнопкой мыши **баз данных** и создать новую базу данных с именем **flightdata**.

3. Щелкните правой кнопкой мыши **flightdata**, нажмите кнопку **задачи**, нажмите кнопку **импорта неструктурированных файлов**.

4. Откройте файл AirlineDemoData.csv, указанный в дистрибутиве R или Python, в зависимости от того, какой язык вы установили.

   Для R, искать **AirlineDemoSmall.csv** в C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library\RevoScaleR\SampleData
   
   Для Python, найдите **AirlineDemoSmall.csv** в C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Lib\site packages\revoscalepy\data\sample_data
  
При выборе файла по умолчанию заполняются значения для имени таблицы и схемы.

  ![Отображение значения по умолчанию airline demo мастера импорта неструктурированных файлов](media/import-airlinedemosmall.png)

Щелкните на следующих страницах, принимая значения по умолчанию, чтобы импортировать данные.


## <a name="query-the-data"></a>Запрос данных

В качестве шага проверки выполните запрос, чтобы убедиться, что данные были отправлены.

1. В обозревателе объектов в базах данных, щелкните правой кнопкой мыши **flightdata** базы данных, а затем запустите новый запрос.

2. Выполните некоторые простые запросы:

    ```sql
    SELECT TOP(10) * FROM AirlineDemoSmall;
    SELECT COUNT(*) FROM AirlineDemoSmall;
    ```

## <a name="next-steps"></a>Следующие шаги

На следующем занятии вы создадите модель линейной регрессии на основе этих данных.

+ [Создание модели Python с помощью revoscalepy](use-python-revoscalepy-to-create-model.md)
