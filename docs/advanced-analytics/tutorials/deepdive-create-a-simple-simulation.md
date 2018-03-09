---
title: "Создание простого моделирования (SQL и R глубокое погружение) | Документы Microsoft"
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs:
- R
ms.assetid: f420b816-ddab-4a1a-89b9-c8285a2d33a3
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: cc613d303fa3200c3460face71399223e00272e6
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2018
---
# <a name="create-a-simple-simulation-sql-and-r-deep-dive"></a>Создание простого моделирования (SQL и R глубокое погружение)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья содержит последний шаг в учебнике глубокое погружение обработки и анализа данных об использовании [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

До сих пор вы уже использовали функций R, разработанных специально для перемещения данных между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и локального контекста вычислений. Однако предположим, что вы написали пользовательскую функцию R и хотите выполнить ее в контексте сервера.

Вы можете вызвать произвольную функцию в контексте компьютера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функции [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) . Можно также использовать **rxExec** для явно распределения работы между ядрами на одном сервере.

На этом занятии удаленного сервера используется для создания простого моделирования. Моделирование не требует данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В примере просто демонстрируется разработка пользовательской функции и ее вызов с помощью функции **rxExec** .

Более сложный пример использования **rxExec**, см. в статье: [крупной гранулярности параллелизм с foreach и rxExec](http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)

## <a name="create-the-custom-function"></a>Создание пользовательской функции

Популярная азартная игра заключается в бросании двух кубиков, причем действуют указанные ниже правила.

- Если при первом броске выпала сумма очков 7 или 11, вы выигрываете.
- Если выпала сумма очков 2, 3 или 12, вы проигрываете.
- Если выпала сумма 4, 5, 6, 8, 9 или 10, это число становится "пойнтом", и нужно продолжать бросать кости, пока снова не выпадет "пойнт" (выигрыш) или сумма 7 (проигрыш).

Эту игру легко смоделировать в R, создав пользовательскую функцию, которую затем можно выполнять много раз.

1.  Создайте пользовательскую функцию, используя следующий код R:
  
    ```R
    rollDice <- function()
    {
        result <- NULL
        point <- NULL
        count <- 1
            while (is.null(result))
            {
                roll <- sum(sample(6, 2, replace=TRUE))
  
                if (is.null(point))
                { point <- roll }
                if (count == 1 && (roll == 7 || roll == 11))
                {  result <- "Win" }
                else if (count == 1 && (roll == 2 || roll == 3 || roll == 12))
                { result \<- "Loss" }
                else if (count > 1 && roll == 7 )
                { result \<- "Loss" }
                else if (count > 1 && point == roll)
                { result <- "Win" }
                else { count <- count + 1 }
            }
            result
    }
    ```
  
2.  Для имитации в одном игру поперечные срезы данных, выполнения функции.
  
    ```R
    rollDice()
    ```
  
    Выиграли вы или проиграли?
  
Теперь давайте посмотрим, как можно использовать **rxExec** для выполнения функции несколько раз, чтобы создать моделирования, которая помогает определить вероятность win.

## <a name="create-the-simulation"></a>Создать имитации

Чтобы выполнить произвольную функцию в контексте компьютера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , следует вызвать функцию **rxExec** . Несмотря на то что **rxExec** также поддерживает распределенные выполнение функции в параллельном режиме между узлами или ядер в контексте сервера, здесь он выполняется пользовательскую функцию на сервере SQL Server.

1. Вызов пользовательской функции в качестве аргумента **rxExec**вместе с другими параметрами, изменяющие моделирование.
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    - Аргумент *timesToRun* позволяет указать, сколько раз должна выполняться функция.  В этом случае кости бросаются 20 раз.
  
    - Аргументы *RNGseed* и *RNGkind* позволяют управлять генерацией случайных чисел. Если параметр *RNGseed* имеет значение **auto**, в каждом рабочем процессе инициализируется параллельный поток случайных чисел.
  
2. Функция **rxExec** создает список с одним элементом для каждого запуска, однако, пока список не заполнится, практически ничего происходить не будет. Когда все итерации будут завершены, строка, начинающаяся с `length` , вернет значение.
  
    После этого можно перейти к следующему шагу, чтобы получить сводку по выигрышам и проигрышам.
  
3. Преобразуйте полученный список в вектор с помощью функции R `unlist` и обобщите результаты с помощью функции `table` .
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    Результаты должны выглядеть примерно так:
  
     *Потеря Win* *12 8*

## <a name="conclusions"></a>Заключение

В этом учебнике вы научились выполнять следующие задачи:
  
-   получать данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для использования при анализе;
  
-   создавать и изменять источники данных в R;
  
-   передавать модели, данные и диаграммы между рабочей станцией и сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  

При желании поэкспериментировать с этих методов, с помощью набора данных большего размера 10 миллионов наблюдений, файлы данных будут доступны на веб-сайте Revolution analytics: [индекса наборов данных](http://packages.revolutionanalytics.com/datasets)

Чтобы повторно использовать в данном пошаговом руководстве с большими файлами данных, загрузить данные, а затем измените каждый источник данных следующим образом:

1. Замените переменные `ccFraudCsv` и `ccScoreCsv` для указания новых файлов данных
2. Изменить имя таблицы, на которые ссылается *sqlFraudTable* для`ccFraud10`
3. Изменить имя таблицы, на которые ссылается *sqlScoreTable* для`ccFraudScore10`

## <a name="additional-samples"></a>Дополнительные примеры

Теперь, когда Вы овладели использование контекстов вычислений и функции RevoScaler для передачи и преобразования данных, см. в этих учебниках.

[R учебники по службам машин обучения](machine-learning-services-tutorials.md)
## <a name="previous-step"></a>Предыдущий шаг

[Перенос данных между SQL Server и файлом XDF](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
