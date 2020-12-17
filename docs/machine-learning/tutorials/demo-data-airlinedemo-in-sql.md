---
description: Демонстрационные данные по прибытию авиарейсов для учебников по SQL Server Python и R
title: Демонстрационные данные по авиарейсам для учебников
Description: Создание базы данных, содержащей набор данных по авиарейсам из R и Python. Этот набор данных используется в руководствах по Python и R для Служб машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 10/22/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 3b19e905d68d53764a496ab5ee7745e3529484cf
ms.sourcegitcommit: 3bd188e652102f3703812af53ba877cce94b44a9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97489904"
---
#  <a name="airline-flight-arrival-demo-data-for-sql-server-python-and-r-tutorials"></a>Демонстрационные данные по прибытию авиарейсов для учебников по SQL Server Python и R
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

В этом упражнении мы создадим базу данных SQL Server для хранения данных, импортированных из встроенных демонстрационных наборов данных по авиарейсам R или Python. В дистрибутивах для R и Python представлены одинаковые данные, которые можно импортировать в базу данных SQL Server с помощью Management Studio.

Для выполнения этого упражнения вам потребуется [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) или другое средство, поддерживающее выполнение запросов T-SQL.

Этот набор данных используется в следующих учебниках и кратких руководствах:

+  [Создание модели Python с помощью revoscalepy](use-python-revoscalepy-to-create-model.md)

## <a name="create-the-database"></a>Создание базы данных

1. Запустите SQL Server Management Studio и установите подключение к экземпляру ядра СУБД, обеспечивающего интеграцию с R или Python.  

2. В обозревателе объектов щелкните правой кнопкой мыши элемент **Базы данных** и создайте новую базу данных с названием **flightdata**.

3. Щелкните правой кнопкой мыши объект **flightdata**, а затем выберите **Задачи** и **Импортировать неструктурированный файл**.

4. Откройте файл AirlineDemoData.csv, входящий в состав дистрибутива R или Python, в зависимости от используемого языка.

   Для R вам потребуется файл **AirlineDemoSmall.csv** из каталога C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR\SampleData
   
   Для Python найдите файл **AirlineDemoSmall.csv** в каталоге C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\revoscalepy\data\sample_data
  
При выборе файла автоматически заполняются значениями по умолчанию поля, определяющие имя таблицы и схему.

  ![Мастер импорта неструктурированных файлов со значениями по умолчанию для демонстрационных данных по авиарейсам](media/import-airlinedemosmall.png)

Перейдите по всем оставшимся страницам, принимая заданные по умолчанию значения, чтобы импортировать данные.


## <a name="query-the-data"></a>Запрос данных

Для проверки выполните запрос и убедитесь, что данные были отправлены.

1. В разделе "Базы данных" обозревателя объектов щелкните правой кнопкой мыши базу **flightdata** и запустите новый запрос.

2. Выполните несколько простых запросов:

    ```sql
    SELECT TOP(10) * FROM AirlineDemoSmall;
    SELECT COUNT(*) FROM AirlineDemoSmall;
    ```

## <a name="next-steps"></a>Дальнейшие действия

В рамках следующего занятия вы создадите модель линейной регрессии на основе этих данных.

+ [Создание модели Python с помощью revoscalepy](use-python-revoscalepy-to-create-model.md)
