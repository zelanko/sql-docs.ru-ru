---
title: Библиотеки пакетов R и Python по умолчанию
description: Пакеты R и Python, устанавливаемые SQL Server для служб R, R Server, Службы машинного обучения (в базе данных) и Machine Learning Server (автономные)
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e49b843b0b32969bd440177cf445916487ad2670
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715205"
---
# <a name="default-r-and-python-packages-in-sql-server"></a>Пакеты R и Python по умолчанию в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье перечислены пакеты R и Python, установленные с помощью SQL Server и где можно найти библиотеку пакетов.  

## <a name="r-package-list-for-sql-server"></a>Список пакетов R для SQL Server

Пакеты r устанавливаются со [службами SQL Server 2016 R](../install/sql-r-services-windows-install.md) и [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) при выборе компонента R во время установки. 

|Пакеты         | 2016 | 2017 | Описание |
|----------------|--------------|--------------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | 9,2 | Используется для удаленных контекстов вычислений, потоковой передачи, параллельного выполнения функций Rx для импорта и преобразования данных, моделирования, визуализации и анализа. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | 9,2 |Используется для включения скрипта R в хранимые процедуры. |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| н.а. | 9,2 | Добавляет алгоритмы машинного обучения в R. | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | н.а.  | 9,2 | Используется для написания инструкций многомерных выражений в R. |

MicrosoftML и OLAP доступны по умолчанию в SQL Server Службы машинного обучения. В экземпляре служб R SQL Server 2016 эти пакеты можно добавить с помощью [обновления компонента](../install/upgrade-r-and-python.md). Обновление компонента также получает более новые версии пакетов (например, более новые версии RevoScaleR включают функции для управления пакетами в SQL Server).

## <a name="python-package-list-for-sql-server"></a>Список пакетов Python для SQL Server

Пакеты Python доступны только в SQL Server 2017 при установке [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) и выборе компонента Python.

| Пакеты         | 2017    |  Описание |
| -----------------|-------------|------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9,2 | Используется для удаленных контекстов вычислений, потоковой передачи, параллельного выполнения функций Rx для импорта и преобразования данных, моделирования, визуализации и анализа. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9,2 | Добавляет алгоритмы машинного обучения в Python. |

## <a name="open-source-r-in-your-installation"></a>С открытым исходным кодом R в установке

Поддержка r включает в себя открытый исходный код, позволяющий вызывать базовые функции R и устанавливать дополнительные пакеты с открытым кодом и сторонними производителями. Языковая поддержка R включает в себя базовые функциональные возможности, такие как **базовый**, **Статистика**, **Служебные**программы и другие. В базовую установку R также входят многочисленные образцы наборов данных и стандартные инструменты R, такие как **RGui** (упрощенный интерактивный редактор) и **RTerm** (Командная строка r). 

Дистрибутив R с открытым исходным кодом, включенный в установку, — это [Microsoft R Open (MRO)](https://mran.microsoft.com/open). MRO добавляет значение в базовый R, включая дополнительные пакеты с открытым исходным кодом, например [библиотеку Intel Math Kernel](https://en.wikipedia.org/wiki/Math_Kernel_Library).

В следующей таблице перечислены версии R, предоставляемые MRO с помощью программы установки SQL Server.

|Выпуск             | Версия R       |
|--------------------|-----------------|
| [Службы SQL Server 2016 R](../install/sql-r-services-windows-install.md) | 3.2.2   | 
| [Изучение служб машины SQL Server](../install/sql-machine-learning-services-windows-install.md) | 3.3.3 |

Никогда не следует вручную перезаписывать версию R, установленную SQL Server установки, с более новыми версиями в Интернете. Пакеты Microsoft R основаны на конкретных версиях R. изменение установки может привести к его дестабилизации.

## <a name="open-source-python-in-your-installation"></a>Открытый исходный код Python в установке

SQL Server 2017 добавляет компоненты Python. При выборе варианта язык Python устанавливается дистрибутив Anaconda 4,2. В дополнение к библиотекам кода Python Стандартная установка включает примеры данных, модульные тесты и примеры сценариев. 

SQL Server 2017 Машинное обучение — это первый выпуск с поддержкой R и Python.

|Выпуск             | Версия Anaconda| Пакеты Майкрософт    |
|--------------------|-----------------|-----------------------|
| Изучение служб машины SQL Server  | 4,2 по Python 3,5 | revoscalepy, microsoftml |

Никогда не следует вручную перезаписывать версию Python, установленную SQL Server установки с более поздними версиями в Интернете. Пакеты Microsoft Python основаны на конкретных версиях Anaconda. Изменение установки может привести к его дестабилизации.

## <a name="component-upgrades"></a>Обновление компонентов

После первоначальной установки пакеты R и Python обновляются с помощью пакетов обновления и накопительных обновлений, но обновление полной версии возможно только путем *привязки* к современной политике поддержки жизненного цикла. Привязка изменяет модель обслуживания. По умолчанию после первоначальной установки пакеты R обновляются с помощью пакетов обновления и накопительных обновлений. Дополнительные пакеты и обновление полных версий компонентов R можно выполнять только при обновлении продукта (от SQL Server 2016 до SQL Server 2017) или путем привязки поддержки R к Microsoft Machine Learning Server. Дополнительные сведения см. [в статье обновление компонентов R и Python в SQL Server](../install/upgrade-r-and-python.md).

## <a name="package-library-location"></a>Расположение библиотеки пакетов

При установке машинного обучения с помощью SQL Server на уровне экземпляра создается отдельная библиотека пакетов для каждого устанавливаемого языка. В Windows библиотека экземпляров является защищенной папкой, зарегистрированной в SQL Server.

Все скрипты или код, выполняемые в базе данных на SQL Server, должны загружать функции из библиотеки экземпляров. SQL Server не может получить доступ к пакетам, установленным в других библиотеках. Это относится и к удаленным клиентам. При подключении к серверу с удаленного клиента любой код R или Python, который должен выполняться в контексте вычислений сервера, может использовать только пакеты, установленные в библиотеке экземпляров.

Для защиты серверных ресурсов Библиотека экземпляров по умолчанию может быть изменена только администратором компьютера. Если вы не являетесь владельцем компьютера, может потребоваться получить от администратора разрешение на установку пакетов в эту библиотеку. 

#### <a name="file-path-for-in-database-engine-instances"></a>Путь к файлу для экземпляров компонента ядра СУБД

В следующей таблице показано расположение файлов R и Python для сочетаний версий и экземпляров ядра СУБД. MSSQL13 указывает SQL Server 2016 и только R. MSSQL14 указывает SQL Server 2017 и содержит папки R и Python. 

Пути к файлам также содержат имена экземпляров. SQL Server устанавливает [экземпляры ядра](../../database-engine/configure-windows/database-engine-instances-sql-server.md) СУБД в качестве экземпляра по умолчанию (MSSQLSERVER) или как определенный пользователем именованный экземпляр. Если SQL Server устанавливается как именованный экземпляр, вы увидите, что имя добавляется следующим образом: `MSSQL13.<instance_name>`.

|Версия и язык  | Путь по умолчанию|
|----------------------|------------|
| SQL Server 2016 |C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library|
| SQL Server 2017 с R|C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library |
| SQL Server 2017 с Python |C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages |


#### <a name="file-path-for-standalone-server-installations"></a>Путь к файлу для установки изолированного сервера

В следующей таблице перечислены пути к двоичным файлам по умолчанию при установке SQL Server 2016 R Server (изолированный) или SQL Server 2017 Machine Learning Server (автономный) Server. 

|Version| Установка|Путь по умолчанию|
|-------|-------------|------------|
| SQL Server 2016|R Server (Standalone)| C:\Program Files\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Machine Learning Server с R |C:\Program Files\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning Server с Python |C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Если другие папки имеют похожие имена и файлы вложенных папок, возможно, у вас есть автономная установка Microsoft R Server или [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/). Эти серверные продукты имеют разные установщики и пути (а именно, C:\Program Филес\микрософт\р Server\R_SERVER или C:\Program Филес\микрософт\мл SERVER\R_SERVER). Дополнительные сведения см. в [статье установка Machine Learning Server для Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) или [установка R Server 9,1 для Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="next-steps"></a>Следующие шаги

+ [Получение сведений о пакете](installed-package-information.md)
+ [Установка новых пакетов R](../r/install-additional-r-packages-on-sql-server.md)
+ [Установка новых пакетов Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Включение удаленного управления пакетами R](../r/r-package-how-to-enable-or-disable.md)
+ [Функции RevoScaleR для управления пакетами R](../r/use-revoscaler-to-manage-r-packages.md)
+ [Синхронизация пакетов R](../r/package-install-uninstall-and-sync.md)
+ [miniCRAN для локального репозитория пакетов R](../r/create-a-local-package-repository-using-minicran.md)
