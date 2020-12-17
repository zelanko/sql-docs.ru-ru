---
title: Повышение производительности с помощью функции профилирования кода R
description: Собирайте полезные сведения, чтобы повысить производительность и быстрее получать результаты вычислений R в SQL Server, с помощью функций профилирования. Функция *rprof* собирает и возвращает сведения о внутренних вызовах функций.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 10/30/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 53c3e7f55fa21d033bfda3f2e660bd1b9a92991f
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470745"
---
# <a name="use-r-code-profiling-functions-to-improve-performance"></a>Использование функций профилирования кода R для повышения производительности
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

В этой статье описываются средства производительности, которые предоставляются пакетами R и позволяют получить сведения о внутренних вызовах функций. Такие сведения вы можете использовать для повышения производительности кода.

> [!TIP]
> В этой статье приводятся основные ресурсы, которые помогут вам приступить к работе. Чтобы ознакомиться с рекомендациями экспертов, мы рекомендуем изучить раздел о *производительности*[книги Хедли Уикема (Hadley Wickham) "Advanced R", посвященной структурам данных R](http://adv-r.had.co.nz).

## <a name="using-rprof"></a>Использование функции rprof

[*rprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/Rprof) — это функция, входящая в базовый пакет [**utils**](https://www.rdocumentation.org/packages/utils/versions/3.5.1), который загружается по умолчанию. 

Обычно функция *rprof* осуществляет выписку стека вызовов в файл через указанные интервалы времени. Затем для обработки выходного файла можно использовать функцию [*summaryRprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/summaryRprof). Одним из преимуществ *rprof* является то, что она выполняет выборку, уменьшая таким образом нагрузку производительности для мониторинга.

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

Установленная по умолчанию документация по Microsoft R Open содержит подробное руководство по разработке расширений языка R, посвященное [профилированию и отладке](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging).

## <a name="next-steps"></a>Дальнейшие шаги

+ Дополнительные сведения об оптимизации скриптов R в SQL Server см. в статье [Настройка производительности и оптимизация данных для R](r-and-data-optimization-r-services.md).
+ Более полные сведения о настройке производительности в SQL Server см. в статье [Центр производительности для Базы данных SQL Azure и ядра СУБД SQL Server](/sql/relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database).
+ Дополнительные сведения о пакете utils для R см. [здесь](https://www.rdocumentation.org/packages/utils/versions/3.5.1).
+ Подробные сведения о программировании на языке R см. в книге [Advanced R](http://adv-r.had.co.nz) (Продвинутое программирование на R) Хэдли Уикхеэма (Hadley Wickham).
