---
title: Библиотеки пакета Python и R в SQL Server R и SQL Server машинного обучения по умолчанию | Документы Microsoft
description: Пакеты R и Python, установки SQL Server для служб R, R Server машины обучения служб (в базе данных) и Machine Learning Server (изолированный)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9362d6e9dc98f80beabc301f43e755b205b40a10
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707292"
---
# <a name="default-r-and-python-packages-in-sql-server"></a>По умолчанию R и Python пакетов в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье перечислены пакеты R и Python, установленные с SQL Server и где найти библиотеки пакета.  

## <a name="r-package-list-for-sql-server"></a>Список пакетов R для SQL Server

R-пакеты устанавливаются вместе с [служб R SQL Server 2016](../install/sql-r-services-windows-install.md) и [служб SQL Server 2017 г машины обучения](../install/sql-machine-learning-services-windows-install.md) при выборе компонентов R во время установки. 

Пакеты         | 2016 | 2017 | Описание |
|----------------|--------------|--------------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | 9.2 | Используется для контекстах удаленных вычислений, потоковой передачи, параллельное выполнение по функциям rx для импорта данных и преобразования, моделирования, визуализации и анализа. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | 9.2 |Используется для включения сценария R в хранимые процедуры. |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.2 | Добавляет алгоритмов машинного обучения на R. | 
| [OlapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a.  | 9.2 | Используется для написания инструкций многомерных Выражений в R. |

По умолчанию в службах SQL Server 2017 г машины обучения доступны MicrosoftML и olapR. На экземпляре служб SQL Server 2016 R, можно добавить эти пакеты через [обновления компонента](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). Обновления компонентов также позволяет более новых версий пакетов (например, более новые версии RevoScaleR относятся функции для пакета управления на сервере SQL Server).

## <a name="python-package-list-for-sql-server"></a>Список пакетов Python для SQL Server

Пакеты Python, доступны только в SQL Server 2017 г., при установке [служб SQL Server 2017 г машины обучения](../install/sql-machine-learning-services-windows-install.md) и выберите компонент Python.

| Пакеты         | 2017    |  Описание |
| -----------------|-------------|------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2 | Используется для контекстах удаленных вычислений, потоковой передачи, параллельное выполнение по функциям rx для импорта данных и преобразования, моделирования, визуализации и анализа. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2 | Добавляет алгоритмов машинного обучения на Python. |

## <a name="open-source-r-in-your-installation"></a>R с открытым исходным кодом в установке

Поддержка R включает открытым исходным кодом, чтобы можно было вызвать базовых функций R и установка дополнительных пакетов с открытым исходным кодом и сторонних разработчиков. Поддержка языка R содержит основные возможности, такие как **базового**, **stats**, **utils**и др. Базовой установки R также включает многочисленные образцы наборов данных и стандартные средства R, такие как **RGui** (упрощенных интерактивный редактор) и **RTerm** (Командная строка R). 

Распределение открытым исходным кодом R, включенных в установку [откройте Microsoft R (MRO)](https://mran.microsoft.com/open). MRO добавляет значение базового R, включая дополнительных пакетов с открытым исходным кодом, такие как [библиотека математического ядра Intel](https://en.wikipedia.org/wiki/Math_Kernel_Library).

В следующей таблице перечислены версии R, предоставляемые MRO, программа установки SQL Server.

|Выпуск             | Версии R       |
|--------------------|-----------------|
| [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) | 3.2.2   | 
| [SQL Server 2017 г машинного обучения служб](../install/sql-machine-learning-services-windows-install.md) | 3.3.3. |

Следует вручную никогда не перезаписи версии R установлен программой установки SQL Server с более новой версии в Интернете. Пакеты Microsoft R основаны на конкретных версий р. Изменение установки может вызвать нестабильность при его.

## <a name="open-source-python-in-your-installation"></a>Python с открытым исходным кодом в установке

2017 г. SQL Server добавляет компоненты Python. При выборе параметра языка Python устанавливается распространения Anaconda 4.2. Помимо библиотеки кода Python Стандартная установка включает образцы данных, модульных тестов и сценариев. 

SQL Server 2017 г машинного обучения — это первая версия R и поддержки Python.

|Выпуск             | Версия anaconda| Пакеты Microsoft    |
|--------------------|-----------------|-----------------------|
| Службы машинного обучения SQL Server 2017  | 4.2 через Python 3.5 | revoscalepy microsoftml |

Следует вручную никогда не перезаписать версию Python устанавливается программой установки SQL Server вместе с более новой версии в Интернете. Пакеты Microsoft Python основаны на конкретных версий Anaconda. Изменение установки может вызвать нестабильность при его.

## <a name="component-upgrades"></a>Обновление компонентов

После первоначальной установки, пакеты R и Python обновляются через пакеты обновления и накопительные обновления, но полную версию обновления возможны только с *привязки* политику современных жизненного цикла поддержки. Привязка изменяется модели обслуживания. По умолчанию после начальной установки, пакеты R обновляются через пакеты обновления и накопительные обновления. Дополнительные пакеты и обновления полной версии компонентов R, возможны только через обновления продукта (из SQL Server 2016 2017 г. SQL Server) или путем привязки R поддерживает Microsoft Server обучения машины. Дополнительные сведения см. в разделе [обновление R и Python компоненты SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="package-library-location"></a>Расположение библиотеки пакета

При установке машинного обучения с помощью SQL Server на уровне экземпляра для каждого языка, который вы устанавливаете создается библиотека одного пакета. В Windows библиотека экземпляра является безопасной папке, зарегистрированные с SQL Server.

Все скрипт или код, что выполняется в базе данных на сервере SQL Server необходимо загрузить функции из библиотеки экземпляра. SQL Server не может получить доступ к пакеты, установленные в других библиотеках. Это относится к удаленным клиентам. При подключении к серверу с удаленного клиента, любой код R или Python, который будет выполняться в контексте сервера можно использовать только пакеты, установленные в библиотеке экземпляра.

Защита ресурсов сервера, можно изменить имя библиотеки по умолчанию экземпляра только администратором компьютера. Если вы не являетесь владельцем компьютера, может потребоваться получить разрешение от администратора для установки пакетов на эту библиотеку. 

#### <a name="file-path-for-in-database-engine-instances"></a>Путь к файлу для экземпляров ядра в базе данных

Следующая таблица показывает расположение файла R и Python для версии и базы данных сочетания экземпляр ядра. MSSQL13 указывает SQL Server 2016 и представляет R-только. MSSQL14 указывает 2017 г. SQL Server и содержит папки R и Python. 

Путь к файлу также содержит имена экземпляров. SQL Server устанавливает [экземпляры ядра базы данных](../../database-engine/configure-windows/database-engine-instances-sql-server.md) как экземпляр по умолчанию (MSSQLSERVER) или как именованный экземпляр, определяемой пользователем. Если SQL Server установлен как именованный экземпляр, вы увидите этого имени будет добавлена следующим образом: `MSSQL13.<instance_name>`.

|Версии и языка  | Путь по умолчанию|
|----------------------|------------|
| SQL Server 2016 |C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library|
| SQL Server 2017 г. с помощью R|C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library |
| SQL Server 2017 г. с Python |C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Lib\site пакетов |


#### <a name="file-path-for-standalone-server-installations"></a>Путь к файлу для установок отдельного сервера

В следующей таблице перечислены пути по умолчанию для двоичных файлов, при установке SQL Server 2016 R Server (автономный) или сервер обучения машины 2017 г. сервер SQL Server (автономный). 

|Версия| Установка|Путь по умолчанию|
|-------|-------------|------------|
| SQL Server 2016|R Server (Standalone)| C:\Program Files\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Машинное обучение сервера с помощью R |C:\Program Files\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Машинное обучение сервера с Python |C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Если найти другие папки с похожими именами вложенную папку, а также файлы, возможно, на автономную установку Microsoft R Server или [server машинного обучения](https://docs.microsoft.com/machine-learning-server/). Эти серверные продукты имеют разных установщики и пути (а именно, C:\Program Files\Microsoft\R Server\R_SERVER или C:\Program Files\Microsoft\ML SERVER\R_SERVER). Дополнительные сведения см. в разделе [Установка машины обучения сервера для Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) или [установить 9.1 R Server для Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="next-steps"></a>Следующие шаги

+ [Получение сведений о пакете](determine-which-packages-are-installed-on-sql-server.md)
+ [Установка новых пакетов R](install-additional-r-packages-on-sql-server.md)
+ [Установка новых пакетов Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Включение удаленного управления пакетами R](r-package-how-to-enable-or-disable.md)
+ [Функции RevoScaleR для управления пакетами R](use-revoscaler-to-manage-r-packages.md)
+ [Синхронизация пакетов R](package-install-uninstall-and-sync.md)
+ [miniCRAN для локального репозитория пакетов R](create-a-local-package-repository-using-minicran.md)
