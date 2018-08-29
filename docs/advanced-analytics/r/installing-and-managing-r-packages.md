---
title: Библиотеки пакетов R и Python в SQL Server R и машинного обучения SQL Server по умолчанию | Документация Майкрософт
description: Пакетов R и Python, SQL Server для служб машинного обучения для служб R, R Server (в базе данных) и сервер машинного обучения (автономный)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7f5c51e9b93aca5d52858417667865633a0c4151
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118312"
---
# <a name="default-r-and-python-packages-in-sql-server"></a>По умолчанию R и Python пакетов в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье перечислены пакеты R и Python, установленные с SQL Server и где можно найти в библиотеке пакетов.  

## <a name="r-package-list-for-sql-server"></a>Список пакетов R для SQL Server

Пакеты R устанавливаются вместе с [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) и [службы машинного обучения SQL Server 2017](../install/sql-machine-learning-services-windows-install.md) при выборе компонента R во время установки. 

Пакеты         | 2016 | 2017 | Описание |
|----------------|--------------|--------------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | 9.2 | Используется для удаленных контекстов вычислений, потоковой передачи, параллельное выполнение функций rx для импорта данных и преобразования, моделирования, визуализации и анализа. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | 9.2 |Используется для включения сценария R в хранимые процедуры. |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.2 | Добавляет алгоритмов машинного обучения на R. | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a.  | 9.2 | Используется для написания инструкций многомерных Выражений в R. |

MicrosoftML и olapR доступны по умолчанию в службах машинного обучения SQL Server 2017. На экземпляре SQL Server 2016 R Services, можно добавить эти пакеты с помощью [обновления компонента](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). Обновления компонентов также позволяет более новые версии пакетов (например, более новые версии RevoScaleR включать функции для управления пакетами на сервере SQL Server).

## <a name="python-package-list-for-sql-server"></a>Список пакетов Python для SQL Server

Пакеты Python, доступны только в SQL Server 2017, при установке [службы машинного обучения SQL Server 2017](../install/sql-machine-learning-services-windows-install.md) и выберите компонент Python.

| Пакеты         | 2017    |  Описание |
| -----------------|-------------|------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2 | Используется для удаленных контекстов вычислений, потоковой передачи, параллельное выполнение функций rx для импорта данных и преобразования, моделирования, визуализации и анализа. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2 | Добавляет алгоритмов машинного обучения на языке Python. |

## <a name="open-source-r-in-your-installation"></a>В установке R с открытым кодом

Поддержка R включает в себя открытый, так что можно вызвать базовых функций R и установить дополнительные пакеты с открытым исходным кодом и сторонних поставщиков. Поддержка языка R содержит основные функциональные возможности, такие как **базового**, **stats**, **utils**и другие. Базовой установке R также включает множество примеров наборов данных и стандартные средства R, такие как **RGui** (упрощенные интерактивный редактор) и **RTerm** (командную строку R). 

Распределение включен в установку R с открытым кодом [откройте Microsoft R (MRO)](https://mran.microsoft.com/open). MRO добавляет значение базового R, включая дополнительные пакеты с открытым исходным кодом, такие как [библиотека математического ядра Intel](https://en.wikipedia.org/wiki/Math_Kernel_Library).

В следующей таблице перечислены версии R, предоставляемые MRO с помощью программы установки SQL Server.

|Выпуск             | Версии R       |
|--------------------|-----------------|
| [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) | 3.2.2   | 
| [SQL Server 2017 службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) | 3.3.3 |

Следует вручную никогда не переписывать версию R устанавливается программой установки SQL Server, более новой версии в Интернете. Пакеты Microsoft R основаны на конкретные версии R. изменения установки может вызвать нестабильность его.

## <a name="open-source-python-in-your-installation"></a>Python с открытым исходным кодом в установке

SQL Server 2017 добавляет компоненты Python. При выборе параметра языка Python устанавливается распространения Anaconda 4.2. В дополнение к библиотек кода Python Стандартная установка включает образцы данных, модульные тесты и примеры сценариев. 

SQL Server 2017 машинного обучения — это первая версия, R и Python, которые поддерживают.

|Выпуск             | Версия anaconda| Пакеты Microsoft    |
|--------------------|-----------------|-----------------------|
| Службы машинного обучения SQL Server 2017  | 4.2 по Python 3.5 | revoscalepy, microsoftml |

Следует вручную никогда не перезаписать версию Python, установленной программой установки SQL Server с более поздними версиями в Интернете. Пакеты Microsoft Python основаны на конкретные версии Anaconda. Изменении установки могут дестабилизировать его.

## <a name="component-upgrades"></a>Обновления компонентов

После первоначальной установки пакетов R и Python обновляются через пакеты обновления и накопительные пакеты обновления, но полная версия обновления возможны только с *привязки* политику поддержки современного жизненного цикла. Привязки изменяет модель обслуживания. По умолчанию после первоначальной установки, пакеты R обновляются через пакеты обновления и накопительные пакеты обновления. Дополнительные пакеты и обновления полной версии компонентов R, возможны только через обновления продукта (из SQL Server 2016 до SQL Server 2017) или путем привязки R поддержки для Microsoft Machine Learning Server. Дополнительные сведения см. в разделе [обновления R и Python компоненты SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="package-library-location"></a>Расположение библиотеки пакета

При установке машинного обучения с помощью SQL Server, библиотеку один пакет создается на уровне экземпляра для каждого языка, который вы устанавливаете. В Windows библиотека экземпляр является защищенной папке регистрации SQL Server.

Все скрипта или кода, выполняется в базе данных на сервере SQL Server необходимо загрузить функции из библиотеки экземпляра. SQL Server не может получить доступ к пакеты, установленные на другие библиотеки. Это относится к удаленным клиентам. При подключении к серверу с удаленного клиента, любой код R или Python, который вы хотите запустить в контексте вычислений server можно использовать только пакеты, установленные в библиотеке экземпляра.

Чтобы защитить серверные ресурсы, библиотеку экземпляр по умолчанию можно изменить только администратором компьютера. Если вы не являетесь владельцем компьютера, может потребоваться получить разрешение из администратором, чтобы установить пакеты в эту библиотеку. 

#### <a name="file-path-for-in-database-engine-instances"></a>Путь к файлу для экземпляров ядра в базе данных

Следующая таблица показывает расположение файла R и Python для версии и базы данных сочетания экземпляр ядра. MSSQL13 указывает SQL Server 2016 и является доступным только для R. MSSQL14 указывает SQL Server 2017 и содержит папки R и Python. 

Путь к файлу также содержит имена экземпляров. SQL Server устанавливает [экземпляры компонента database engine](../../database-engine/configure-windows/database-engine-instances-sql-server.md) как экземпляр по умолчанию (MSSQLSERVER) или как именованный экземпляр, определяемые пользователем. Если SQL Server установлен как именованный экземпляр, вы увидите это имя, добавляются следующим образом: `MSSQL13.<instance_name>`.

|Версия и язык  | Путь по умолчанию|
|----------------------|------------|
| SQL Server 2016 |C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library|
| SQL Server 2017 с помощью R|C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library |
| SQL Server 2017 с помощью Python |C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Lib\site пакетов |


#### <a name="file-path-for-standalone-server-installations"></a>Путь к файлу для установок отдельного сервера

В следующей таблице перечислены пути по умолчанию двоичных файлов, при установке SQL Server 2016 R Server (изолированный) или сервера SQL Server 2017 Machine Learning Server (изолированную версию). 

|Версия| Установка|Путь по умолчанию|
|-------|-------------|------------|
| SQL Server 2016|R Server (Standalone)| C:\Program Files\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Machine Learning Server, с помощью R |C:\Program Files\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning Server, с помощью Python |C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Если вы найдете другие папки аналогичные названия этих вложенных папок и файлов, возможно, на автономную установку Microsoft R Server или [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/). Эти серверные продукты имеют разные установщики и путей (а именно: C:\Program Files\Microsoft\R Server\R_SERVER или C:\Program Files\Microsoft\ML SERVER\R_SERVER). Дополнительные сведения см. в разделе [установите Machine Learning Server для Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) или [Установка R Server 9.1 для Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="next-steps"></a>Следующие шаги

+ [Получение сведений о пакете](determine-which-packages-are-installed-on-sql-server.md)
+ [Установка новых пакетов R](install-additional-r-packages-on-sql-server.md)
+ [Установка новых пакетов Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Включение удаленного управления пакетами R](r-package-how-to-enable-or-disable.md)
+ [Функции RevoScaleR для управления пакетами R](use-revoscaler-to-manage-r-packages.md)
+ [Синхронизация пакетов R](package-install-uninstall-and-sync.md)
+ [miniCRAN для локального репозитория пакетов R](create-a-local-package-repository-using-minicran.md)
