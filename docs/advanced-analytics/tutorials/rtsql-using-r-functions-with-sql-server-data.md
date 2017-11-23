---
title: "С помощью функций R с данными SQL Server (R в быстрый запуск SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
- SQL
ms.assetid: e2fe5d90-eee9-4daf-9eae-21d17b3ef320
caps.latest.revision: "8"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 919f29c8d96324f21dde2e87bb861f3e76f8241d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="using-r-functions-with-sql-server-data-r-in-sql-quickstart"></a>С помощью функций R с данными SQL Server (R в быстрый запуск SQL Server)

Теперь, когда вы знакомы с базовыми операциями, пришло время поработать с расширенными функциями R. Например, многие дополнительные статистические функции сложно реализовать с помощью T-SQL, а при использовании R для них требуется только одна строка кода.  Службы R упрощают внедрение служебных скриптов R в хранимую процедуру.

Используя приведенные здесь примеры, вы научитесь внедрять служебные и математические функции R в хранимую процедуру SQL Server.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Создание хранимой процедуры для формирования случайных чисел

Для простоты используем R `stats` пакет, который установлен и загружен по умолчанию со службами R Services. Он содержит сотню функций для общих статистических задач, в том числе функцию `rnorm`, которая формирует указанное количество случайных чисел с нормальным распределением при заданном среднем значении и стандартном отклонении.

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

Это просто в сочетании с SQL Server: определение хранимой процедуры, которая возвращает аргументы от пользователя. Затем передайте эти аргументы в скрипт R в виде переменных.

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

## <a name="related-resources"></a>Связанные ресурсы

+ Вы действительно хотите установить дополнительные пакеты R, чтобы получить более дополнительные статистические функции? В разделе [Установка и управление пакеты R](../r/installing-and-managing-r-packages.md).

+ Чтобы преобразовать код автономный R в формате, который можно легко параметризовать с помощью хранимых процедур SQL Server, Microsoft R team предоставил новый R-пакет **sqlrutils**. Дополнительные сведения см. в разделе [Создание хранимой процедуры, с помощью sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md).

## <a name="use-r-utility-functions-for-troubleshooting"></a>Использование служебных функций R для устранения неполадок

По умолчанию включает установленного экземпляра R `utils` пакет, который предоставляет широкий набор служебных функций для изучения текущей среде R. Они могут оказаться полезными, если вы нашли несоответствия в выполнении кода R в SQL Server и внешних средах.

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

Многие пользователи предпочитают использовать системные функции синхронизации в R, например `system.time` и `proc.time`, для отслеживания времени, используемая процессами R и анализировать проблемы производительности.

Пример см. в руководстве [Занятие 3. Создание характеристик данных (пошаговое руководство по обработке и анализу данных)](../tutorials/walkthrough-create-data-features.md). В этом пошаговом руководстве функции времени R внедряются в решение, чтобы сравнить производительность двух методов для формирования признаков на основе данных: с помощью функций R и функций T-SQL.

## <a name="next-lesson"></a>Следующее занятие

Далее вы создадите модель прогнозирования с помощью R в SQL Server.

[Создание модели прогнозирования](../tutorials/rtsql-create-a-predictive-model-r.md)
