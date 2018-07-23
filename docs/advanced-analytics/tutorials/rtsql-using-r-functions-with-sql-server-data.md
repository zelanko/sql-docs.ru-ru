---
title: Краткое R работает с данными SQL Server (машинного обучения SQL Server) | Документация Майкрософт
description: В этом кратком руководстве вы научитесь напишите функцию R, использующей данные SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5785b8b8162fdde25dea13eb3aead55c10dbfc3b
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086676"
---
# <a name="quickstart-using-r-functions-with-sql-server-data"></a>Краткое руководство: Использование функций R с данными SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Если вы выполнили предыдущие краткие руководства, вы знакомы с базовыми операциями и готовы для более сложной, например статистические функции. Статистических функций, которые сложно реализовать в T-SQL может выполняться в R с помощью одной строки кода.

В этом кратком руководстве вы научитесь внедрять R математических и служебных функций в SQL Server хранимой процедуры.

## <a name="prerequisites"></a>предварительные требования

Предыдущего краткого руководства, [Hello World в R и SQL](rtsql-using-r-code-in-transact-sql-quickstart.md), сведения и ссылки по настройке среды R, необходимые для этого краткого руководства.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Создание хранимой процедуры для формирования случайных чисел

Для простоты используем R `stats` пакет, который устанавливается и загружается по умолчанию при установке поддержка функций R в SQL Server. Он содержит сотню функций для общих статистических задач, в том числе функцию `rnorm`, которая формирует указанное количество случайных чисел с нормальным распределением при заданном среднем значении и стандартном отклонении.

Например, код R возвращает 100 чисел со средним значением 50 и стандартным отклонением 3.

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

Чтобы вызвать строку кода R из T-SQL, выполните процедуру sp_execute_external_script и добавьте функцию R в параметр скрипта R, как показано ниже.

```sql
EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

Как упростить формирование другого набора случайных чисел?

Это просто, в сочетании с SQL Server: Определите хранимую процедуру, которая получает аргументы от пользователя. Затем передайте эти аргументы в скрипт R в виде переменных.

```sql
CREATE PROCEDURE MyRNorm (@param1 int, @param2 int, @param3 int)
AS
    EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynumbers, mymean, mysd));'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
    WITH RESULT SETS (([Density] float NOT NULL));
```

+ В первой строке определяется каждый из входных параметров SQL, необходимых при выполнении хранимой процедуры.

+ Строка, начинающаяся с `@params`, определяет все переменные, используемые в коде R, и соответствующие типы данных SQL.

+ Следующие строки сопоставляют имена параметров SQL с соответствующими именами переменных R.

Теперь, когда функция R упакована в хранимой процедуре, вы можете легко вызвать функцию и передать различные значения, как показано ниже.

```sql
EXEC MyRNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-r-utility-functions-for-troubleshooting"></a>Использование служебных функций R для устранения неполадок

По умолчанию включает установки R `utils` пакет, который предоставляет широкий набор служебных функций для изучения текущей среды r. Они могут оказаться полезными, если вы нашли несоответствия в выполнении кода R в SQL Server и внешних средах.

Например, можно использовать функцию R `memory.limit()`, чтобы получить память для текущей среды R. По умолчанию пакет `utils` устанавливается, но не загружается, поэтому сначала необходимо использовать функцию `library()`, чтобы его загрузить.

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N'
        library(utils);
        mymemory <- memory.limit();
        OutputDataSet <- as.data.frame(mymemory);'
    , @input_data_1 = N' ;'
WITH RESULT SETS (([Col1] int not null));
```

Многие пользователи хотели использовать функции системного времени в R, например `system.time` и `proc.time`, чтобы фиксировать время, затрачиваемое процессами R и анализировать проблемы производительности.

Пример см. в руководстве [Занятие 3. Создание характеристик данных (пошаговое руководство по обработке и анализу данных)](../tutorials/walkthrough-create-data-features.md). В этом пошаговом руководстве функции времени R внедряются в решение, чтобы сравнить производительность двух методов для формирования признаков на основе данных: с помощью функций R и функций T-SQL.

## <a name="next-steps"></a>Следующие шаги

Далее вы создадите модель прогнозирования с помощью R в SQL Server.

> [!div class="nextstepaction"]
> [Краткое руководство: Создание модели прогнозирования](rtsql-create-a-predictive-model-r.md)
