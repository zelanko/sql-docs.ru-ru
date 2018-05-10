---
title: Библиотеки пакета Python и R в SQL Server R и SQL Server машинного обучения по умолчанию | Документы Microsoft
description: Пакеты R и Python, установки SQL Server для служб R, R Server машины обучения служб (в базе данных) и Machine Learning Server (изолированный)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/08/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ee2c8124cf3487ca300c0b08ea113c8e66b114f4
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/08/2018
---
# <a name="default-r-and-python-packages-in-sql-server"></a>По умолчанию R и Python пакетов в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье рассматриваются пакетных библиотек, расположение и версии пакетов R и Python, установленных с SQL Server. 

## <a name="using-the-default-instance-library"></a>С помощью библиотеки экземпляр по умолчанию

При установке машинного обучения с помощью SQL Server на уровне экземпляра для каждого языка, который вы устанавливаете создается библиотека одного пакета. 

Все скрипт или код, что выполняется в базе данных на сервере SQL Server необходимо загрузить функции из библиотеки экземпляра. SQL Server не может получить доступ к пакеты, установленные в других библиотеках. Это относится к удаленным клиентам. При подключении к серверу с удаленного клиента, любой код R или Python, который будет выполняться в контексте сервера можно использовать только пакеты, установленные в библиотеке экземпляра.

Защита ресурсов сервера, имя библиотеки по умолчанию экземпляр устанавливается в безопасной папке, зарегистрированные с SQL Server и может быть изменен только администратором компьютера. Если вы не являетесь владельцем компьютера, может потребоваться получить разрешение от администратора для установки пакетов на эту библиотеку. 

Даже если на вашем компьютере, следует учитывать полезность любой определенный пакет R или Python в серверной среде Добавление пакета в библиотеку экземпляра. Рассмотрите также требует ли пакет сети или Интернету факторов, таких как размер файлов пакета, которые требуют нескольких версий access.

### <a name="in-database-engine-instance-file-paths"></a>Пути к файлам экземпляр ядра базы данных

Следующая таблица показывает расположение файла R и Python для версии и базы данных сочетания экземпляр ядра. 

|Версия | Имя экземпляра|Путь по умолчанию|
|--------|--------------|------------|
| SQL Server 2016 |экземпляр по умолчанию| C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library|
| SQL Server 2016 |именованный экземпляр | C:\Program Files\Microsoft SQL Server\MSSQL13. < имя_экземпляра > \R_SERVICES\library|
| SQL Server 2017 г. с помощью R|экземпляр по умолчанию | C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library |
| SQL Server 2017 г. с помощью R|именованный экземпляр| C:\Program Files\Microsoft SQL Server\MSSQL14. MyNamedInstance\R_SERVICES\library |
| SQL Server 2017 г. с Python |экземпляр по умолчанию | C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\library |
| SQL Server 2017 г. с Python|именованный экземпляр| C:\Program Files\Microsoft SQL Server\MSSQL14. < имя_экземпляра > \PYTHON_SERVICES\library |

### <a name="standalone-server-file-paths"></a>Пути к файлам автономного сервера 

В следующей таблице перечислены пути по умолчанию для двоичных файлов, при установке SQL Server 2016 R Server (автономный) или сервер обучения машины 2017 г. сервер SQL Server (автономный). 

|Версия| Установка|Путь по умолчанию|
|------|------|------|
| SQL Server 2016|R Server (Standalone)| C:\Program Files\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Машинное обучение сервера с помощью R |C:\Program Files\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Машинное обучение сервера с Python |C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Если найти другие папки с похожими именами вложенную папку, а также файлы, возможно, на автономную установку Microsoft R Server или [server машинного обучения](https://docs.microsoft.com/machine-learning-server/). Эти серверные продукты имеют разных установщики и пути (а именно, C:\Program Files\Microsoft\R Server\R_SERVER или C:\Program Files\Microsoft\ML SERVER\R_SERVER). Дополнительные сведения см. в разделе [Установка машины обучения сервера для Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) или [установить 9.1 R Server для Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="what-is-included-in-a-default-installation"></a>Что входит в установку по умолчанию

В этом разделе перечислены компоненты R и Python, включенные в установку по умолчанию.

### <a name="r-components"></a>Компоненты R

Компоненты включают распределение корпорации Майкрософт R с открытым исходным кодом как [Microsoft R Open](https://mran.microsoft.com/open). Base R-пакеты содержат основные функциональные возможности, такие как **stats** и **utils**. Можно запустить `installed.packages(priority = "base")` для получения списка пакетов. Базовой установки R также включает многочисленные образцы наборов данных и стандартными средствами R, такими как RGui (упрощенных интерактивный редактор) и RTerm (Командная строка R).

В пакетах Microsoft [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) для контекстах удаленных вычислений, потоковой передачи, параллельного выполнения по функциям rx для импорта данных и преобразования данных, моделирования, визуализации и анализа. [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package) добавляет машинного обучения на R. моделирования Другие пакеты содержат [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) для написания инструкций многомерных Выражений в R, и [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) для включения сценария R в хранимые процедуры.


|Выпуск             | Версии R       | Пакеты Microsoft    |
|--------------------|-----------------|-----------------------|
| SQL Server 2016 R Services | 3.2.2   | RevoScaleR sqlrutil  |
| Службы машинного обучения SQL Server 2017| 3.4.3 | RevoScaleR, MicrosoftML, olapR, sqlrutil|

Можно добавить пакеты и предварительно установленные модели для служб SQL Server 2016 R путем привязки к политике современных жизненного цикла поддержки. Привязка изменяется модели обслуживания. По умолчанию после начальной установки, пакеты R обновляются через пакеты обновления и накопительные обновления. Дополнительные пакеты и обновления полной версии компонентов R, возможны только через обновления продукта (из SQL Server 2016 2017 г. SQL Server) или путем привязки R поддерживает Microsoft Server обучения машины. Дополнительные сведения см. в разделе [обновление R и Python компоненты SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="python-components"></a>Компоненты Python

2017 г. SQL Server добавляет компоненты Python. Дистрибутив Anaconda устанавливается при выборе параметра языка Python. Помимо библиотеки кода Python Стандартная установка включает образцы данных, модульных тестов и сценариев. 

В пакетах Microsoft [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) как эквиваленты Python RevoScaleR, при потоковой передаче параллельного выполнения по функциям rx для импорта данных и преобразования, моделирования, визуализации и анализа. Другой пакет Python — [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) для обучения и преобразования, оценки, text и image анализа и извлечения признаков для извлечения значений из существующих данных.

SQL Server 2017 г машинного обучения — это первая версия R и поддержки Python.

|Выпуск             | Версия anaconda| Пакеты Microsoft    |
|--------------------|-----------------|-----------------------|
| Службы машинного обучения SQL Server 2017  | 4.2 через Python 3.5 | revoscalepy microsoftml |

После первоначальной установки пакеты Python обновляются через пакеты обновления и накопительные обновления, но полную версию обновления возможны только путем привязки к Microsoft Server обучения машины поддержка Python. Дополнительные сведения см. в разделе [обновление R и Python компоненты SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="administrative-permissions-for-package-installation"></a>Административные разрешения для установки пакета

Между SQL Server 2016 и 2017 г. SQL Server были изменены разрешения, необходимые для установки пакета.

+ В SQL Server 2016 для установки новых пакетов R требуется административный доступ.
+ В 2017 г. SQL Server можно продолжать установки пакетов от имени администратора R и Python, и возможно, это самый простой способ. 

    Инструкции DDL, создать ВНЕШНИЕ БИБЛИОТЕКИ, позволяет администратору базы данных для установки пакетов без использования средств R. 

    При использовании функции пакета управления для компьютера сервера обучения RevoScaleR можно использовать для установки пакетов R на уровне базы данных. Администратор базы данных необходимо включить функцию и предоставьте пользователям возможность устанавливать собственные пакеты отдельно для каждой базы данных. Дополнительные сведения см. в разделе [пакета управления с помощью библиотеки DDL](r-package-how-to-enable-or-disable.md).

### <a name="user-libraries-are-not-supported"></a>Библиотек пользователей не поддерживаются.

Пользователи, не может установить пакет в надежном месте часто прибегать к установке пакета в библиотеку пользователя. Однако это невозможно в среде SQL Server. Обычно доступ к файловой системе ограничен на сервере и даже при наличии прав администратора и доступ в папку документов пользователя на сервере среды выполнения внешнего сценария, выполняющегося в SQL Server не может получить доступ к все пакеты, установленные за пределами экземпляра по умолчанию Библиотека. Однако возможны обходные пути. Советы по устранению неполадок, связанных с библиотек пользователей см. в разделе [обходные пути для библиотек пользователей R](packages-installed-in-user-libraries.md).

## <a name="next-steps"></a>Следующие шаги

+ [Получить сведения о пакете](determine-which-packages-are-installed-on-sql-server.md)
+ [Установка нового R-пакетов](install-additional-r-packages-on-sql-server.md)
+ [Установить новые пакеты Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Включение удаленного управления пакета R](r-package-how-to-enable-or-disable.md)
+ [Функции RevoScaleR для управления пакетами R](use-revoscaler-to-manage-r-packages.md)
+ [Синхронизация пакета R](package-install-uninstall-and-sync.md)
+ [miniCRAN для локальный репозиторий пакетов R](create-a-local-package-repository-using-minicran.md)
