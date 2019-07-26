---
title: Демонстрационный набор данных рейса авиакомпании для SQL Server учебных материалов по Python и R
Description: Создайте базу данных с набором данных авиакомпании из R и Python. Этот набор данных используется в упражнениях, демонстрирующих создание оболочки языка R или кода Python в SQL Server хранимой процедуре.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/22/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 38e61bcbf3a5ff5ed44f85d5ad28406550e5a726
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469675"
---
#  <a name="airline-flight-arrival-demo-data-for-sql-server-python-and-r-tutorials"></a>Демонстрационные данные о прибытии авиабилетов для SQL Server Python и R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом упражнении вы создадите базу данных SQL Server для хранения импортированных данных из встроенных демонстрационных наборов данных авиакомпании на языке R или Python. Дистрибутивы R и Python предоставляют эквивалентные данные, которые можно импортировать в SQL Server базу данных с помощью Management Studio.

Для выполнения этого упражнения необходимо иметь [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) или другое средство, которое может выполнять запросы T-SQL.

Ниже приведены руководства и краткие руководства, в которых используется этот набор данных.

+  [Создание модели Python с помощью revoscalepy](use-python-revoscalepy-to-create-model.md)

## <a name="create-the-database"></a>Создайте базу данных

1. Запустите SQL Server Management Studio, подключитесь к экземпляру ядра СУБД с интеграцией R или Python.  

2. В обозревателе объектов щелкните правой кнопкой мыши **базы данных** и создайте новую базу данных с именем **флигхтдата**.

3. Щелкните правой кнопкой мыши **флигхтдата**, выберите **задачи**, а затем импорт неструктурированного **файла**.

4. Откройте файл Аирлинедемодата. csv, указанный в дистрибутиве R или Python, в зависимости от установленного языка.

   Для R найдите файл **AirlineDemoSmall. csv** в папке C:\PROGRAM Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library\RevoScaleR\SampleData
   
   Для Python найдите файл **AirlineDemoSmall. csv** в папке C:\PROGRAM Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\revoscalepy\data\sample_data
  
При выборе файла значения по умолчанию заполняются для имени таблицы и схемы.

  ![Мастер импорта неструктурированных файлов, демонстрирующий демо по умолчанию для авиакомпании](media/import-airlinedemosmall.png)

Щелкните остальные страницы, принимая значения по умолчанию, чтобы импортировать данные.


## <a name="query-the-data"></a>Запрос данных

В качестве шага проверки выполните запрос для подтверждения передачи данных.

1. В обозревателе объектов в разделе базы данных щелкните правой кнопкой мыши базу данных **флигхтдата** и запустите новый запрос.

2. Выполните некоторые простые запросы:

    ```sql
    SELECT TOP(10) * FROM AirlineDemoSmall;
    SELECT COUNT(*) FROM AirlineDemoSmall;
    ```

## <a name="next-steps"></a>Следующие шаги

На следующем занятии будет создана модель линейной регрессии на основе этих данных.

+ [Создание модели Python с помощью revoscalepy](use-python-revoscalepy-to-create-model.md)
