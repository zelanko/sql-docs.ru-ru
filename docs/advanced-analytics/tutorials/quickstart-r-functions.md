---
title: Краткое руководство, в котором функции R — SQL Server Машинное обучение
description: В этом кратком руководстве вы узнаете, как написать функцию R для расширенных статистических вычислений.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c8c8f69391db2e1028a0da33dbaf77fd60eafd8f
ms.sourcegitcommit: 75fe364317a518fcf31381ce6b7bb72ff6b2b93f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2019
ms.locfileid: "70909200"
---
# <a name="quickstart-use-r-functions"></a>Краткое руководство. Использование функций R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Если вы выполнили предыдущие примеры, вы знакомы с основными операциями и готовы к более сложной, например статистическим функциям. Расширенные статистические функции, которые сложно реализовать в T-SQL, можно выполнять в R с помощью одной строки кода.

В этом кратком руководстве мы внедряем математические и служебные функции в SQL Server хранимую процедуру.

## <a name="prerequisites"></a>Предварительные требования

Предыдущее краткое руководство, [Проверка наличия R в SQL Server](quickstart-r-verify.md), содержит сведения и ссылки для настройки среды R, необходимой для этого краткого руководства.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Создание хранимой процедуры для формирования случайных чисел

Для простоты давайте будем использовать пакет R `stats` , который устанавливается и загружается по умолчанию при установке поддержки функций R в SQL Server. Он содержит сотню функций для общих статистических задач, в том числе функцию `rnorm`, которая формирует указанное количество случайных чисел с нормальным распределением при заданном среднем значении и стандартном отклонении.

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

Это легко в сочетании с SQL Server: Определите хранимую процедуру, которая получает аргументы от пользователя. Затем передайте эти аргументы в скрипт R в виде переменных.

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

По умолчанию установка R включает `utils` пакет, который предоставляет разнообразные служебные функции для изучения текущей среды R. Они могут оказаться полезными, если вы нашли несоответствия в выполнении кода R в SQL Server и внешних средах.

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

Многие пользователи, например, используют системные функции времени в r, такие как `system.time` и `proc.time`, для записи времени, используемого процессами r, и анализа проблем производительности.

Пример см. в этом руководстве: [Создание функций данных](../tutorials/walkthrough-create-data-features.md). В этом пошаговом руководстве функции времени R внедряются в решение для сравнения производительности двух методов создания функций из данных: Сравнение функций R и и функций T-SQL.

## <a name="next-steps"></a>Следующие шаги

Далее вы создадите модель прогнозирования с помощью R в SQL Server.

> [!div class="nextstepaction"]
> [Краткое руководство Создание прогнозной модели](quickstart-r-create-predictive-model.md)
