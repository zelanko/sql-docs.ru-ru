---
title: Использование функций - службы машинного обучения SQL Server профилирования кода R
description: Повысьте производительность и получить результаты быстрее на вычисления R на SQL Server с помощью R, функциями профилирования для возврата сведений о внутренних вызовах функций.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: c9195a6c2b9a2192e9d8fd04ce3e5d2592b1b23e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62642255"
---
# <a name="use-r-code-profiling-functions-to-improve-performance"></a>Использование функций профилирования кода R для повышения производительности
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Помимо использования средств и ресурсов SQL Server для отслеживания выполнения скрипта R можно использовать средства обеспечения производительности, входящие в другие пакеты R, чтобы получить дополнительные сведения о внутренних вызовах функций. 

> [!TIP]
> Эта статья содержит основные ресурсы для начала работы. Экспертов, мы рекомендуем *производительности* статьи [«Advanced R», (Hadley Wickham)](http://adv-r.had.co.nz).

## <a name="using-rprof"></a>Использование функции rprof

[*rprof* ](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/Rprof) — это функция, включенные в базовый пакет [ **utils**](https://www.rdocumentation.org/packages/utils/versions/3.5.1), который загружается по умолчанию. 

Обычно функция *rprof* осуществляет выписку стека вызовов в файл через указанные интервалы времени. Затем можно использовать [ *summaryRprof* ](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/summaryRprof) функции для обработки выходного файла. Одним из преимуществ *rprof* является то, что она выполняет выборку, уменьшая таким образом нагрузку производительности для мониторинга.

Чтобы использовать профилирование R в коде, вызовите эту функцию и укажите ее параметры, включая расположение записываемого файла журнала. Вы можете включить и отключить профилирование кода. Следующий синтаксис иллюстрирует основные сценарии использования: 

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

Документация для Microsoft R Open, которая будет установлена по умолчанию, включает в себя руководство по разработке расширений языка R, посвященное [профилирования и отладки](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging) подробно. Же документацию можно найти на локальном компьютере в папке C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\doc\manual.

## <a name="see-also"></a>См. также

+ [пакет utils R](https://www.rdocumentation.org/packages/utils/versions/3.5.1)
+ [«Дополнительно» R по (Hadley Wickham)](http://adv-r.had.co.nz)
