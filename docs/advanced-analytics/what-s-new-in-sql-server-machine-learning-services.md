---
title: Новые возможности - служб машинного обучения SQL Server | Документация Майкрософт
description: Объявления новых функций для каждого выпуска SQL Server 2016 R Services, R Server, службы машинного обучения SQL Server 2017.
ms.date: 02/28/2019
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 64e98073dabd490965fb5d582102a6eb962c5a13
ms.sourcegitcommit: 11ab8a241a6d884b113b3cf475b2b9ed61ff00e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161832"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>Новые возможности в службах машинного обучения SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Возможности обучения машины будут добавлены к SQL Server в каждом выпуске, как мы продолжаем развернуть, расширить и улучшить интеграцию между платформой данных, расширенной аналитики и обработки и анализа данных. 

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2019-preview"></a>Возможности предварительной версии SQL Server 2019

В этом выпуске добавлена наиболее часто запрашиваемых функций для операций обучения машины R и Python в SQL Server. Дополнительные сведения обо всех функциях в этом выпуске см. в разделе [новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md) и [заметки о выпуске для SQL Server 2019](../sql-server/sql-server-ver15-release-notes.md).

| Выпуск | Обновления компонентов |
|---------|----------------|
| CTP 2.3 | Новых поддерживаемых [типами данных Java](java/java-sql-datatypes.md). |
| | В Windows, код Java может осуществляться в внешнюю библиотеку при помощи [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) инструкции. Функциональные возможности, аналогичные будут доступны на платформе Linux в следующей CTP-версии. Дополнительные сведения: [Как вызвать Java из SQL Server](java/howto-call-java-from-sql.md). |
| | В Windows, код Python может осуществляться внешнюю библиотеку, используя [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) инструкции. Функциональные возможности, аналогичные будут доступны на платформе Linux в следующей CTP-версии. |
| CTP 2.2 | Нет изменений. |
| CTP 2.1 | Нет изменений. |
| CTP 2.0 | Поддержка платформы Linux для машинного обучения R и Python. Начало работы с [установить SQL Server служб машинного обучения на платформе Linux](../linux/sql-server-linux-setup-machine-learning.md). |
|   | [Расширение языка Java](java/extension-java.md) в Windows и Linux возможности в SQL Server 2019 предварительной версии. Вы можете предоставить скомпилированный Java кода для SQL Server, назначение разрешений и задав путь. Клиентские приложения с доступом к SQL Server можно использовать данные и выполнять код путем вызова [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), ту же процедуру, используемый для интеграции R и Python на сервере SQL Server. | 
|  | [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) представлены два новых параметра, которые позволяют легко создать несколько моделей из секционированных данных. Дополнительные сведения в этом руководстве [создавать модели на основе секций в R](tutorials/r-tutorial-create-models-per-partition.md). |
|   | Поддержка кластера отработки отказа теперь поддерживается в Windows и Linux, предполагая, что запущена служба панели запуска SQL Server на всех узлах. Дополнительные сведения см. в разделе [Установка отказоустойчивого кластера SQL Server](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md). |

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2017"></a>В SQL Server 2017

В этом выпуске добавлена [поддержка Python и ведущими в отрасли алгоритмов машинного обучения](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/). Переименован в соответствии с новой областью, SQL Server 2017 помечает появлением [службы машинного обучения из состава SQL Server (в базе данных)](what-is-sql-server-machine-learning.md), поддержка языка Python и R. 

Функция объявлений комплексная, см. в разделе [новые возможности в SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

### <a name="r-enhancements"></a>Усовершенствования R

Компонент прокрутки на R для службы машинного обучения SQL Server 2017 является следующим поколением SQL Server 2016 R Services, и обновленных версий базовый R, RevoScaler и других пакетов.

Новые возможности для R включают [ **управление пакетами**](r/install-additional-r-packages-on-sql-server.md), с помощью следующие моменты: 

+ Роли базы данных помогают администраторам баз данных управления пакетами и назначение разрешений для установки пакета.
+ [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) помогает администраторам баз данных управления пакетами в знакомый язык T-SQL.
+ [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md) функции помогают установка, удаление или перечисление пакетов, принадлежащие пользователям. Дополнительные сведения см. в разделе [пакетов как использовать функции RevoScaleR для поиска или установки R на SQL Server](r/use-revoscaler-to-manage-r-packages.md).

### <a name="r-libraries"></a>Библиотеки R

| Пакет | Описание |
|---------|-------------|
| [**MicrosoftML**](r/ref-r-microsoftml.md) | В этом выпуске MicrosoftML включается при установке R по умолчанию, устраняя шаг обновления, необходимые в предыдущем SQL Server 2016 R Services. MicrosoftML обеспечивает состояние современные алгоритмы машинного обучения и преобразования данных, которые можно масштабировать и запустить в контексте удаленных вычислений. Алгоритмы включают настраиваемые глубоких нейронных сетей, быстрые деревья и леса принятия решений, Линейная регрессия и логистической регрессии.  |

### <a name="python-integration-for-in-database-analytics"></a>Интеграция Python для анализа в базе данных

Python — это язык, который предлагает большую гибкость и возможности для различных задач машинного обучения. Библиотек с открытым кодом для Python включают несколько платформ для настраиваемых нейронных сетей, а также популярные библиотеки для обработки естественного языка. Теперь этот широко применяемый язык поддерживается в SQL Server 2017 машинного обучения.

Так как Python интегрирована с ядром СУБД, можно поддерживать аналитикой рядом с данными и избежав затрат и рисков, связанных с перемещением данных. Вы можете развернуть решения машинного обучения, основанный на Python с помощью таких средств, как Visual Studio. Рабочие приложения могут получить прогнозы, моделей, или визуальные элементы из среды выполнения Python 3.5, с помощью данных SQL Server получить доступ к методам.

Поддерживается интеграция T-SQL и Python с помощью [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) системной хранимой процедуры. Можно вызвать любой код Python, с помощью этой хранимой процедуры. Код выполняется в безопасной, двойной архитектуру, которая обеспечивает развертывание корпоративного уровня модели Python и сценарии, вызываемые из приложения с использованием простой хранимой процедуры. Повышает производительность достигается путем потоковой передачи данных из SQL в процессы Python и параллелизацию кольца MPI.

Вы можете использовать T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) функцию для выполнения [собственной оценки](sql-native-scoring.md) на предварительно обученной модели, который был ранее сохранен в требуемом двоичном формате.

### <a name="python-libraries"></a>Библиотеки Python

| Пакет | Описание |
|---------|-------------|
|[**revoscalepy**](python/ref-py-revoscalepy.md)| Python — эквивалент RevoScaleR. Можно создавать модели Python для линейных и логистических регрессий, деревьев принятия решений, усиленных деревьев и случайные леса, все параллельно и обрабатывать выполняются в контексте удаленных вычислений. Этот пакет поддерживает использование нескольких источников данных и контексты удаленных вычислений. Специалист по обработке данных или разработчик могут выполнять код Python на удаленном сервере SQL, для просмотра данных или построения моделей без перемещения данных. |
|[**microsoftml**](python/ref-py-microsoftml.md) |Python — эквивалент MicrosoftML R-пакет. |

### <a name="pre-trained-models"></a>Предварительно обученная модель

[**Предварительно обученных моделей** ](install/sql-pretrained-models-install.md) , доступных для Python и R. использовать эти модели для распознавания изображений и анализ тональности неотрицательным положительный результат, для создания прогнозов по собственным данным. 

### <a name="standalone-server-as-a-shared-feature-in-sql-server-setup"></a>Изолированный сервер в качестве общего компонента в программе установки SQL Server

Этот выпуск также добавлена [SQL Server Machine Learning Server (изолированный)](r/r-server-standalone.md), сервер обработки и анализа данных полностью независимы, поддерживающий статистические и прогнозной аналитики в R и Python. Как со службами R, этот сервер является следующей версии SQL Server 2016 R Server (изолированную версию). С автономным сервером можно распределять и масштабировать решения R или Python без зависимостей на сервере SQL Server.
::: moniker-end

## <a name="new-in-sql-server-2016"></a>В SQL Server 2016

Этом выпуске представлены возможности машинного обучения в SQL Server с помощью **SQL Server 2016 R Services**, модуль аналитики в базе данных для скрипта обработки R на данных, находящихся в экземпляр ядра СУБД.

Кроме того **SQL Server 2016 R Server (изолированный)** был выпущен как способ установки R Server на сервере Windows. Первоначально программа установки SQL Server содержит единственный способ установить R Server для Windows. В последующих выпусках разработчиков и специалистов по анализу данных, которым было R Server в Windows использовать другой автономный установщик для достижения той же цели. Автономный сервер в SQL Server является функциональным эквивалентом автономная Серверная система [Microsoft R Server для Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

Функция объявлений комплексная, см. в разделе [новые возможности в SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md).

| Выпуск |Обновления компонентов |
|---------|----------------|
| Накопительное обновление дополнения | [**Оценки в реальном времени** ](real-time-scoring.md) полагается на собственные библиотеки C++ для чтения модели, сохраненной в оптимизированный двоичный формат и создавать прогнозы без вызова среды выполнения R. В результате оценки операции гораздо быстрее. С помощью оценки в реальном времени, можно выполнить хранимую процедуру или выполнять оценки в реальном времени из кода R. Оценки в реальном времени также доступна для SQL Server 2016, если экземпляр обновляется до последней версии [!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]. |
| Начальный выпуск | [**Интеграция R для аналитики в базе данных**](r/sql-server-r-services.md). <br/><br/> Пакеты R для R вызывающей функции в T-SQL и наоборот. Функции RevoScaleR предоставляют аналитики R в масштабе разделяя данные на компоненты, согласование и управление распределенными обработки и объединения результатов. В SQL Server 2016 R Services (в базе данных) ядро RevoScaleR интегрирован с экземпляром компонента database engine, brining данных и аналитики, в том же контексте обработки. <br/><br/>Интеграция T-SQL и R через [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql). Можно вызвать любой код на R с помощью этой хранимой процедуры. Эта инфраструктура безопасности обеспечивает развертывание корпоративного уровня Rn модели и сценарии, которые могут вызываться из приложения с использованием простой хранимой процедуры. Повышает производительность достигается путем потоковой передачи данных из SQL в процессы R и параллелизацию кольца MPI. <br/><br/>Вы можете использовать T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md) функцию для выполнения [собственной оценки](sql-native-scoring.md) на предварительно обученной модели, который был ранее сохранен в требуемом двоичном формате.|

## <a name="linux-support-roadmap"></a>План поддержки Linux

SQL Server 2019 CTP 2.3 — добавлена поддержка Linux R, Python и Java, при установке машинного обучения пакеты с экземпляром компонента database engine. Дополнительные сведения см. в разделе [установить SQL Server служб машинного обучения на платформе Linux](../linux/sql-server-linux-setup-machine-learning.md).

В Linux, SQL Server 2017 не установлена интеграция с R или Python, но можно использовать [собственной оценки](sql-native-scoring.md) в Linux так, как эта функциональность доступна через T-SQL [PREDICT](../t-sql/queries/predict-transact-sql.md), который выполняется в системе Linux. Собственная Оценка позволяет высокопроизводительных оценки на основе предварительно обученные модели, без вызова или даже вносить среду выполнения R.

<a name="azure-sql-database-roadmap"></a>

## <a name="machine-learning-services-in-azure-sql-database"></a>Службы машинного обучения в базе данных Azure SQL

Службы машинного обучения (с помощью R) в базе данных SQL Azure находится в общедоступной предварительной версии. Дополнительные сведения см. в разделе [краткое руководство: Использовать службы машинного обучения (с помощью R) в базе данных SQL Azure (Предварительная версия)](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-r).

## <a name="next-steps"></a>Следующие шаги

+ [Установка служб SQL Server 2017 машинного обучения (в базе данных)](install/sql-machine-learning-services-windows-install.md)
+ [Учебники по машинному обучению и примеры](tutorials/machine-learning-services-tutorials.md)
