---
title: Новые возможности | Документация Майкрософт
description: Новые объявления о функциях для каждого выпуска SQL Server 2016 R Services, R Server SQL Server 2017 Службы машинного обучения.
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 0e3859cfb1ada6453a353509b68abe34e71d2840
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345779"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Новые возможности SQL Server Службы машинного обучения

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Возможности машинного обучения добавляются в SQL Server в каждом выпуске, так как мы продолжаем расширять, расширять и углубить интеграцию между платформой данных, расширенной аналитикой и обработкой и анализом данных. 

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2019-preview"></a>Новые статьи в предварительной версии SQL Server 2019

В этом выпуске добавляются наиболее востребованные функции для операций машинного обучения R и Python в SQL Server. Дополнительные сведения о всех функциях этого выпуска см. в разделе [новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md) и заметки о [выпуске для SQL Server 2019](../sql-server/sql-server-ver15-release-notes.md).

> [!NOTE]
> Дополнительные сведения о новой документации по Java в SQL Server 2019 см. в разделе [что нового в расширениях языка SQL Server?](https://docs.microsoft.com/sql/language-extensions/language-extensions-whats-new)

| Выпуск | Обновление компонентов |
|---------|----------------|
| CTP 3.0 | Нет изменений. |
| CTP-ВЕРСИЯ 2,5 | Нет изменений. |
| CTP 2.4 | Поддержка Linux для [создания внешней библиотеки (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) для R и Python. |
| CTP 2.3 | Только в Windows доступ к коду Python можно получить во внешней библиотеке с помощью инструкции [CREATE External Library (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) . |
| CTP 2.2 | Нет изменений. |
| CTP 2.1 | Нет изменений. |
| CTP 2.0 | Поддержка платформ Linux для машинного обучения R и Python. Начало работы с [SQL Server установки службы машинного обучения в Linux](../linux/sql-server-linux-setup-machine-learning.md). |
|  | [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) вводит два новых параметра, которые позволяют легко создавать несколько моделей на основе секционированных данных. Дополнительные сведения в этом руководстве см. в статье [Создание моделей на основе секций в R](tutorials/r-tutorial-create-models-per-partition.md). |
|   | Поддержка отказоустойчивого кластера теперь поддерживается в Windows и Linux, предполагая, что панель запуска SQL Server служба запущена на всех узлах. Дополнительные сведения см. в разделе [SQL Server установка отказоустойчивого кластера](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md). |

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2017"></a>Новые SQL Server 2017

В этом выпуске добавлена [Поддержка Python и ведущие в отрасли алгоритмы машинного обучения](https://cloudblogs.microsoft.com/sqlserver/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/). Переименовано в соответствии с новой областью, SQL Server 2017 отмечает введение [SQL Server службы машинного обучения (в базе данных)](what-is-sql-server-machine-learning.md)с поддержкой языка для Python и R. 

Объявления о функциях см. в статье [новые возможности SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

### <a name="r-enhancements"></a>Усовершенствования R

Компонент R SQL Server 2017 Службы машинного обучения является следующим поколением служб SQL Server 2016 R с обновленными версиями базовых R, RevoScaler и других пакетов.

Новые возможности для R включают [**Управление пакетами**](r/install-additional-r-packages-on-sql-server.md)со следующими подсветами. 

+ Роли базы данных помогают администраторам системы управления пакетами и назначать разрешения для установки пакета.
+ [Создание внешней библиотеки](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) помогает администраторам баз данных управлять пакетами на знакомом языке T-SQL.
+ Функции [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md) помогают устанавливать, удалять или перечислять пакеты, принадлежащие пользователям. Дополнительные сведения см. в [статье Использование функций RevoScaleR для поиска или установки пакетов R на SQL Server](r/use-revoscaler-to-manage-r-packages.md).

### <a name="r-libraries"></a>Библиотеки R

| Пакет | Описание |
|---------|-------------|
| [**MicrosoftML**](r/ref-r-microsoftml.md) | В этом выпуске MicrosoftML входит в установку R по умолчанию, устраняя шаг обновления, необходимый в предыдущих SQL Server 2016 служб R. MicrosoftML предоставляет современные алгоритмы машинного обучения и преобразования данных, которые можно масштабировать или запускать в удаленных контекстах вычислений. Алгоритмы включают настраиваемые глубокие нейронные сети, быстрые деревья принятия решений и леса принятия решений, линейную регрессию и логистическую регрессию.  |

### <a name="python-integration-for-in-database-analytics"></a>Интеграция Python для аналитики в базе данных

Python — это язык, обеспечивающий большую гибкость и мощь различных задач машинного обучения. Библиотеки с открытым исходным кодом для Python включают несколько платформ для настраиваемых нейронных сетей, а также популярные библиотеки для обработки на естественном языке. Теперь этот широко используемый язык поддерживается в SQL Server 2017 Машинное обучение.

Поскольку Python интегрирован с ядром СУБД, аналитика может быть близка к данным и устранять расходы и риски безопасности, связанные с перемещением данных. Вы можете развертывать решения машинного обучения на основе Python с помощью таких средств, как Visual Studio. Рабочие приложения могут получать прогнозы, модели или визуальные элементы из среды выполнения Python 3,5 с помощью SQL Server методов доступа к данным.

Интеграция T-SQL и Python поддерживается через системную хранимую процедуру [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) . С помощью этой хранимой процедуры можно вызвать любой код Python. Код выполняется в безопасной и двойной архитектуре, которая позволяет развертывать модели и сценарии Python корпоративного класса, вызываемые из приложения с помощью простой хранимой процедуры. Увеличение производительности достигается путем потоковой передачи данных из SQL в процессы Python и параллелизации MPI Ring.

Функцию [Predict](../t-sql/queries/predict-transact-sql.md) T-SQL можно использовать для выполнения [собственной оценки](sql-native-scoring.md) предварительно обученной модели, которая ранее сохранялась в требуемом двоичном формате.

### <a name="python-libraries"></a>Библиотеки Python

| Пакет | Описание |
|---------|-------------|
|[**revoscalepy**](python/ref-py-revoscalepy.md)| Эквивалент RevoScaleR в Python. Вы можете создавать модели Python для линейных и логистических регрессий, деревьев принятия решений, повышенных деревьев и случайных лесов, всех параллелизуемые и выполнения в удаленных контекстах вычислений. Этот пакет поддерживает использование нескольких источников данных и удаленных контекстов вычислений. Анализу данных или разработчик может выполнять код Python на удаленном SQL Server, чтобы исследовать данные или создавать модели без перемещения данных. |
|[**microsoftml**](python/ref-py-microsoftml.md) |Эквивалент пакета MicrosoftML R в Python. |

### <a name="pre-trained-models"></a>Предварительно обученная модель

[**Предварительно обученные модели**](install/sql-pretrained-models-install.md) доступны как для Python, так и для R. Используйте эти модели для распознавания изображений и положительного отрицательного тональностиного анализа для создания прогнозов на основе собственных данных. 

### <a name="standalone-server-as-a-shared-feature-in-sql-server-setup"></a>Изолированный сервер как общий компонент в SQL Server установки

В этом выпуске также добавляется [SQL Server Machine Learning Server (автономный)](r/r-server-standalone.md), полностью независимый сервер обработки и анализа данных, поддерживающий статистические и прогнозирующие аналитики в R и Python. Как и в случае со службами R, этот сервер является следующей версией SQL Server 2016 R Server (изолированной). С помощью автономного сервера можно распространять и масштабировать решения R или Python без зависимостей от SQL Server.
::: moniker-end

## <a name="new-in-sql-server-2016"></a>Новые SQL Server 2016

В этом выпуске появились возможности машинного обучения в SQL Server с помощью **служб SQL Server 2016 R Services**, подсистемы аналитики в базе данных для обработки скрипта R в резидентных данных в экземпляре ядра СУБД.

Кроме того, **SQL Server 2016 r Server (изолированный)** был выпущен в качестве способа установки r Server на Windows Server. Изначально SQL Server программа установки предоставляет единственный способ установки R Server для Windows. В более поздних выпусках разработчики и специалисты по обработке и анализу данных, которым требовалось R Server в Windows, могут использовать другой автономный установщик для достижения той же цели. Изолированный сервер в SQL Server функционально эквивалентен отдельному серверному продукту [Microsoft R Server для Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

Объявления о функциях см. в статье [новые возможности SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md).

| Выпуск |Обновление компонентов |
|---------|----------------|
| Дополнения CU | [**Оценка в реальном времени**](real-time-scoring.md) основана на собственных C++ библиотеках для чтения модели, хранящейся в оптимизированном двоичном формате, а затем формирует прогнозы без вызова среды выполнения R. Это значительно ускоряет операции оценки. С помощью оценки в реальном времени можно выполнить хранимую процедуру или выполнить оценку кода R в режиме реального времени. Оценка в режиме реального времени также доступна для SQL Server 2016, если экземпляр обновлен до последней версии [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]. |
| Начальный выпуск | [**Интеграция R для аналитики в базе данных**](r/sql-server-r-services.md). <br/><br/> Пакеты r для вызова функций R в T-SQL и наоборот. Функции RevoScaleR предоставляют аналитику R в масштабе путем фрагментирования данных в части компонентов, координации и управления распределенной обработкой, а затем статистической обработки результатов. В SQL Server 2016 служб R (в базе данных) подсистема RevoScaleR интегрирована с экземпляром ядра СУБД, брининг данными и аналитикой вместе в одном контексте обработки. <br/><br/>Интеграция T-SQL и R с помощью [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). Можно вызвать любой код R с помощью этой хранимой процедуры. Эта безопасная инфраструктура позволяет развертывать модели и скрипты RN корпоративного класса, которые можно вызывать из приложения с помощью простой хранимой процедуры. Увеличение производительности достигается за счет потоковой передачи данных из SQL в процессы R и параллелизации MPI. <br/><br/>Функцию [Predict](../t-sql/queries/predict-transact-sql.md) T-SQL можно использовать для выполнения [собственной оценки](sql-native-scoring.md) предварительно обученной модели, которая ранее сохранялась в требуемом двоичном формате.|

## <a name="linux-support-roadmap"></a>План поддержки Linux

SQL Server 2019 CTP 2,3 добавляет поддержку Linux для R и Python при установке пакетов машинного обучения с помощью экземпляра ядра СУБД. Дополнительные сведения см. [в разделе Install SQL Server службы машинного обучения в Linux](../linux/sql-server-linux-setup-machine-learning.md).

В Linux SQL Server 2017 не имеет интеграции R или Python, но вы можете использовать [собственную](sql-native-scoring.md) оценку в Linux, так как эта функция доступна через T-SQL [Predict](../t-sql/queries/predict-transact-sql.md), который работает в Linux. Собственная оценка обеспечивает высокий уровень производительности из предварительно обученной модели без вызова или даже необходимости среды выполнения R.

<a name="azure-sql-database-roadmap"></a>

## <a name="machine-learning-services-in-azure-sql-database"></a>Службы машинного обучения в базе данных SQL Azure

Службы машинного обучения (с R) в базе данных SQL Azure находится в общедоступной предварительной версии. Дополнительные сведения см. в статье [службы машинного обучения базы данных SQL Azure с помощью R (Предварительная версия)](https://docs.microsoft.com/azure/sql-database/sql-database-machine-learning-services-overview).

## <a name="next-steps"></a>Следующие шаги

+ [Установка SQL Server 2017 Службы машинного обучения (в базе данных)](install/sql-machine-learning-services-windows-install.md)
+ [Учебники и примеры машинного обучения](tutorials/machine-learning-services-tutorials.md)
