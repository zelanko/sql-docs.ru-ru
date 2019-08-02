---
title: Использование функций профилирования кода R
description: Повышение производительности и быстрое получение результатов вычислений R на SQL Server с помощью функций профилирования R, возвращающих сведения о внутренних вызовах функций.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e03ae1a8c4cdab87f46f63da6271886b4518b5e3
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715015"
---
# <a name="use-r-code-profiling-functions-to-improve-performance"></a>Использование функций профилирования кода R для повышения производительности
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Помимо использования средств и ресурсов SQL Server для отслеживания выполнения скрипта R можно использовать средства обеспечения производительности, входящие в другие пакеты R, чтобы получить дополнительные сведения о внутренних вызовах функций. 

> [!TIP]
> В этой статье приводятся основные ресурсы, которые помогут вам приступить к работе. Для экспертов мы рекомендуем раздел " *производительность* " в разделе ["Advanced R" (Hadley Wickham](http://adv-r.had.co.nz)).

## <a name="using-rprof"></a>Использование функции rprof

[*rprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/Rprof) — это функция, входящая в базовый пакет [**utils**](https://www.rdocumentation.org/packages/utils/versions/3.5.1), которая загружается по умолчанию. 

Обычно функция *rprof* осуществляет выписку стека вызовов в файл через указанные интервалы времени. Затем можно использовать функцию [*суммарирпроф*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/summaryRprof) для обработки выходного файла. Одним из преимуществ *rprof* является то, что она выполняет выборку, уменьшая таким образом нагрузку производительности для мониторинга.

Чтобы использовать профилирование R в коде, вызовите эту функцию и укажите ее параметры, включая расположение записываемого файла журнала. Вы можете включить и отключить профилирование кода. Следующий синтаксис иллюстрирует базовое использование: 

```R
# Specify profiling output file.
varOutputFile <- "C:/TEMP/run001.log")
Rprof(varOutputFile)

# Turn off profiling
Rprof(NULL)
    
# Restart profiling
Rprof(append=TRUE)
```

> [!NOTE]
> Чтобы использовать эту функцию, установите Windows Perl на компьютер, где выполняется код. Таким образом, мы советуем выполнить профилирование кода во время его разработки в среде R, а затем развернуть отлаженный код в SQL Server.  


## <a name="r-system-functions"></a>Системные функции R

Язык R содержит множество базовых функций пакета для возврата содержимого системных переменных. Например, в качестве части кода R можно использовать `Sys.timezone` для получения сведений о текущем часовом поясе или `Sys.Time` для получения системного времени из R. 

Чтобы получить сведения об отдельных системных функциях R, введите имя функции в качестве аргумента для функции R `help()` в командной строке R.

```R
help("Sys.time")
```

## <a name="debugging-and-profiling-in-r"></a>Отладка и профилирование в R

Документация по Microsoft R Open, которая устанавливается по умолчанию, включает руководство по разработке расширений для языка R, в котором подробно обсуждается [Профилирование и отладка](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging) . Эту же документацию можно найти на компьютере в папке C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\doc\manual.

## <a name="see-also"></a>См. также

+ [пакет R для utils](https://www.rdocumentation.org/packages/utils/versions/3.5.1)
+ ["Advanced R", Hadley Wickham](http://adv-r.had.co.nz)
