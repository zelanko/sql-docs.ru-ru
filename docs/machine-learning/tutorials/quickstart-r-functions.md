---
title: Краткое руководство. Функции R
description: В этом кратком руководстве вы узнаете, как внедрять математические и служебные функции R в Службах машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2020
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fd3c3326fe0b186ade24cbcf95f587abba1cb6bc
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487291"
---
# <a name="quickstart-r-functions-with-sql-server-machine-learning-services"></a>Краткое руководство. Функции R в Службах машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве вы узнаете, как внедрять математические и служебные функции R в Службах машинного обучения SQL Server. Зачастую статистические функции, которые сложно реализовать в T-SQL, выполняются в R всего парой строк кода.

## <a name="prerequisites"></a>Предварительные требования

- Для этого краткого руководства требуется доступ к экземпляру SQL Server со [службами машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md) и с установленным языком R.

  Экземпляр SQL Server может находиться в виртуальной машине Azure или на локальном компьютере. Обратите внимание, что функция внешних сценариев по умолчанию отключена, поэтому перед началом работы вам может потребоваться [включить ее](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) и убедиться, что **служба панели запуска SQL Server** выполняется.

- Вам также понадобится средство для выполнения SQL-запросов, содержащих сценарии R. Эти сценарии можно выполнять с помощью любого средства управления базами данных или запросов, которые могут подключаться к экземпляру SQL Server и выполнять запросы T-SQL или хранимые процедуры. В этом кратком руководстве используется среда [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Создание хранимой процедуры для формирования случайных чисел

Для простоты мы будем использовать пакет R `stats`, который по умолчанию устанавливается и загружается в службы машинного обучения SQL Server при установке R. Он содержит сотню функций для общих статистических задач, в том числе функцию `rnorm`, которая формирует указанное количество случайных чисел с нормальным распределением при заданном среднем значении и стандартном отклонении.

Например, следующий код R возвращает 100 чисел со средним значением 50 и стандартным отклонением 3.

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

Чтобы вызвать строку кода R из T-SQL, добавьте функцию R в параметр скрипта R `sp_execute_external_script`, как показано ниже:

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

Как упростить формирование другого набора случайных чисел?

С помощью SQL Server это несложно. Вы определяете хранимую процедуру, которая получает предоставленные пользователем аргументы и передает их в качестве переменных в скрипт R.

```sql
CREATE PROCEDURE MyRNorm (
    @param1 INT
    , @param2 INT
    , @param3 INT
    )
AS
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynumbers, mymean, mysd));'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
WITH RESULT SETS(([Density] FLOAT NOT NULL));
```

- В первой строке определяется каждый из входных параметров SQL, необходимых при выполнении хранимой процедуры.

- Строка, начинающаяся с `@params`, определяет все переменные, используемые в коде R, и соответствующие типы данных SQL.

- Следующие строки сопоставляют имена параметров SQL с соответствующими именами переменных R.

Теперь, когда функция R упакована в хранимой процедуре, вы можете легко вызвать функцию и передать различные значения, как показано ниже.

```sql
EXECUTE MyRNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-r-utility-functions-for-troubleshooting"></a>Использование служебных функций R для устранения неполадок

Установленный по умолчанию пакет **utils** предоставляет широкий набор служебных функций для изучения текущей среды R. Они могут оказаться полезными, если вы нашли несоответствия в выполнении кода R в SQL Server и внешних средах.

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

> [!TIP]
> Многие пользователи предпочитают использовать функции системного времени в R, такие как `system.time` и `proc.time`, чтобы фиксировать время, затрачиваемое процессами R, и анализировать проблемы производительности. Например, см. руководство [Создание характеристик данных](../tutorials/walkthrough-create-data-features.md), где функции времени R внедрены в решение.

## <a name="next-steps"></a>Дальнейшие действия

Инструкции по созданию модели машинного обучения с использованием R в SQL Server см. в следующем кратком руководстве:

> [!div class="nextstepaction"]
> [Создание и оценка модели прогнозов в R с помощью служб машинного обучения SQL Server](quickstart-r-train-score-model.md)

Дополнительные сведения о службах машинного обучения SQL Server см. в следующей статье:

- [Что такое службы машинного обучения SQL Server (Python и R)?](../sql-server-machine-learning-services.md)
