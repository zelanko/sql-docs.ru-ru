---
title: Совместимость R в службах R SQL Server | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 59196e0569ac9cc683b3affa68fc17f068e74994
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203176"
---
# <a name="r-interoperability-in-sql-server"></a>Взаимодействие R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом разделе основное внимание уделяется механизм для запуска для R в SQL Server и описываются различия между Microsoft R и открытым исходным кодом R.

Применяется к: службы R SQL Server 2016, SQL Server 2017 г машинного обучения служб

Сведения о дополнительных компонентах см. в разделе [новых компонентов в SQL Server](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r.md).

### <a name="open-source-r-components"></a>Компоненты R с открытым кодом

Службы [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] включают полный дистрибутив базовых пакетов и средств R. Дополнительные сведения о компонентах базового дистрибутива см. в документации, установленной во время установки в папке по умолчанию: `C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES\doc\manual`

При установке [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] вы должны согласиться с условиями открытой лицензии GNU. После этого можно выполнять стандартные пакеты R без изменений так же, как и в других дистрибутивах R с открытым кодом.

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] не меняет среду выполнения R. Среда выполнения R выполняется за пределами процесса [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Ее можно выполнять независимо от [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Однако во избежание конфликта ресурсов мы не рекомендуем запускать эти средства, если [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] использует R.

Базовый дистрибутив пакета R, связанный с конкретным экземпляром [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], можно найти в связанной с ним папке. Например при установке служб R в экземпляре по умолчанию библиотек R, находятся в этой папке по умолчанию:

    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library

Аналогичным образом средства R, связанные с экземпляром по умолчанию будет находиться в этом папки по умолчанию:

    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin

Дополнительные сведения о том, как Microsoft R отличается от базового дистрибутив R, который можно получить из CRAN см. в разделе [взаимодействие с языка R и Microsoft R продукты и компоненты](https://docs.microsoft.com/en-us/r-server/what-is-r-server-interoperability)

### <a name="additional-r-packages-from-microsoft-r"></a>Дополнительных пакетов R от Microsoft R

В дополнение к базовым распределения R [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] включает некоторые собственные пакеты R, а также является платформой для параллельного выполнения R, который также поддерживает выполнение R в контекстах удаленных вычислений.

Этот объединенный набор компонентов R (базовый дистрибутив R, а также улучшенные компоненты и пакеты R) называется **Microsoft R**. При установке Microsoft R Server (изолированная версия) вы получаете те же пакеты, что и при установке служб R SQL Server (в базе данных). Отличается только папка установки.

Microsoft R включает дистрибутив Intel Math Kernel Library, который используется по возможности для ускоренной обработки математических операций. Например, библиотека базовой линейной алгебры (BLAS) используется для множества пакетов надстроек, а также для R. Дополнительные сведения см. в следующих статьях:

+ [How the Intel Math Kernel Speeds up R](http://blog.revolutionanalytics.com/2014/10/revolution-r-open-mkl.html) (Как Intel Math Kernel ускоряет выполнение R)
+ [Performance benefits of linking R to multithreaded math libraries](http://blog.revolutionanalytics.com/2010/06/performance-benefits-of-multithreaded-r.html) (Повышение производительности при связывании R с многопоточными математическими библиотеками).

Среди наиболее важных дополнений Microsoft R можно выделить пакеты **RevoScaleR** и **RevoPemaR**. Это пакеты R, написанные в основном на C или C++ для повышения производительности.

+ **RevoScaleR.** Включает различные интерфейсы API для анализа и обработки данных. API-интерфейсы оптимизированы для анализа наборов данных, которые слишком велики для размещения в памяти, и для выполнения вычислений, распределенных по нескольким ядрам или процессорам.

   API-интерфейсы RevoScaleR также поддерживают работу с подмножествами данных для повышения масштабируемости. Другими словами, большинство функций RevoScaleR может обрабатывать блоки данных и использовать алгоритмы обновления для статистической обработки результатов. Таким образом, решения R на основе функций RevoScaleR могут работать с очень большими наборами данных, и они не ограничены локальной памятью.

  Пакеты RevoScaleR также поддерживают формат файлов XDF для быстрого перемещения и сохранения данных, используемых для анализа. XDF-файлы используют хранилище столбцов, их можно переносить и использовать для загрузки и обработки данных из различных источников, включая текст, SPSS или подключения ODBC. 

+ **RevoPemaR.** PEMA (от английского Parallel External Memory Algorithm) расшифровывается как параллельный алгоритм внешней памяти. Пакет **RevoPemaR** предоставляет интерфейсы API, которые можно использовать для разработки собственных параллельных алгоритмов. Дополнительные сведения см. в [руководстве по началу работы с RevoPemaR](https://docs.microsoft.com/r-server/r/how-to-developer-pemar).

Кроме того, рекомендуется сначала ознакомиться [MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package), создания пакета из Microsoft R, которая поддерживает удаленное выполнение кода R и масштабируемых, распределенную обработку, улучшенная алгоритмов машинного обучения с помощью разработана Microsoft Research.

## <a name="next-steps"></a>Следующие шаги

[Обзор архитектуры](../../advanced-analytics/r/architecture-overview-sql-server-r.md)

[Компоненты SQL Server для поддержки R](../../advanced-analytics/r/new-components-in-sql-server-to-support-r.md)

[Общие сведения о безопасности](../../advanced-analytics/r/security-overview-sql-server-r.md)

