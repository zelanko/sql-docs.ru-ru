---
title: Новые возможности служб SQL Server машины обучения | Документы Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d4beafc3c5dcb19c1b46b53d727f36733884daad
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="what-is-sql-server-machine-learning-services"></a>Новые возможности служб SQL Server машины обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Службы SQL Server Machine Learning — это внедренные, прогнозной аналитики и данных обработки и анализа ядро, могут выполнять код R и Python в базе данных SQL Server, как хранимые процедуры, как скрипт T-SQL, содержащий инструкции R или Python или R или Python, содержащая код T-SQL. 

Ключа ценностного предложения службы обучения машины является степенью его собственных пакетов для доставки углубленной аналитики с масштабируемостью и возможность перевести вычисления и обработки, в которой хранятся данные, что исключает необходимость извлечения данных между сеть.

Существует два варианта использования возможности обучения в SQL Server: 

+ [**Обучение машины службы (в базе данных) для SQL Server** ](r/sql-server-r-services.md) действует в пределах экземпляра компонента database engine, где Вычислительное ядро полностью интегрирован с компонентом database engine. В большинстве установок являются этот параметр.
+ [**Обучение компьютера сервера SQL Server (автономный)** ](r/r-server-standalone.md) установка не SQL. Несмотря на то, что программа установки SQL Server используется для установки сервера, полностью отсоединяется от SQL Server. Функционально он эквивалентен отличные от SQL [машины обучения Windows Microsoft Server для](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

## <a name="r-and-python-packages"></a>Пакеты R и Python

Для каждого языка поддерживается через собственные пакеты Microsoft, используемый для создания и обучения моделей различных типов, оценки данных и параллельную обработку базовых системных ресурсов с помощью.

Так как собственные пакеты создаются в распределениях открытым исходным кодом R и Python, скрипт или код, который выполняется в SQL Server можно вызывать базовый функции и использовать пакетов сторонних совместима с версией языка, представленные в SQL Server (Python 3.5 и последние версии R, в настоящее время 3.3.3.).

| Чтение  | Python | Описание |
|-----------|----------------|-------------|
| [RevoScaleR](r/revoscaler-overview.md) | [revoscalepy](python/what-is-revoscalepy.md)   | Функции в этих библиотеках являются наиболее широко используемых. Преобразования данных и манипуляции, формирование сводных статистических данных, визуализации и моделирования и анализа в различных форматах, находятся в этих библиотеках. Кроме того функции в этих библиотеках автоматически распределять рабочую нагрузку между доступных ядер для параллельной обработки, возможность работать с фрагментами данных, которые являются скоординированы и не управляется Вычислительное ядро. |
| [MicrosoftML](using-the-microsoftml-package.md) | [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Отрасли алгоритмов машинного обучения для featurization изображения, проблем классификации и многое другое. |
| [OlapR](r/how-to-create-mdx-queries-using-olapr.md) | none | Построении или выполнении запроса многомерных Выражений в R-сценария.
| [SqlRUtils](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md) | none | Функции для помещения R-скриптов в T-SQL хранимой процедуры, регистрация хранимой процедуры в базе данных и запуск хранимой процедуры из среды разработки R.
| [mrsdeploy](operationalization-with-mrsdeploy.md) | none | В основном используется в установке отличные от SQL Server обучения машины, такие как [(автономный) версии](r/r-server-standalone.md). Этот пакет можно используйте для развертывания и размещения веб-служб, построение топологии масштабирования выделенных веб-службы с и вычислительных узлов, переключаться между локальным и удаленным сеансы, выполнять диагностику и многое другое. Для установки (в базе данных), использовать этот пакет в количества клиентов: например, для доступа к веб-службы на удаленном сервере исключительно для выполнения только службы обучения машины рабочих нагрузок. |

Переносимость пользовательский код R и Python осуществляется через распространения пакета и переводчикам, встроенные в нескольких продуктов. Те же пакеты, которые поставляются в SQL Server также доступны в нескольких других продуктов и служб Майкрософт, включая отличные от SQL версия, называемая [Microsoft Server обучения машины](https://docs.microsoft.com/machine-learning-server/). Включить свободного клиентов, включающих нашей интерпретаторов R и Pyton [клиент Microsoft R](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) и [библиотеки Python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter).

Пакеты и интерпретаторов также доступны на нескольких [виртуальных машин Azure](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-azure-vm-on-linux), машинного обучения Azure и Azure служб, таких как [HDInsight](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-on-azure-hdinsight). 


## <a name="use-cases"></a>Способы применения

**Аналитика в базе данных**

Разработчики и аналитикам часто содержат код, выполняющийся на локальном экземпляре SQL Server. Если SQL Server и Интегрированная среда разработки таких как [Visual Studio с помощью R](https://docs.microsoft.com/visualstudio/rtvs/) или [Visual Studio с Python](https://docs.microsoft.com/visualstudio/python/installing-python-support-in-visual-studio) на том же компьютере, можно построить, обучения и тестирования моделей локально на любом языке. Пакет управления упрощает локальный доступ: как администратор, вы можете загрузить дополнительных пакетов сторонних разработчиков, с помощью встроенных разрешений для этой роли.

Для анализа в базе данных наиболее распространенным подходом является использование [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) для выполнения сценария R или Python. Учебники, перечисленные в [дальнейшие действия](#next-steps) будет приступить к работе.

**Клиент сервер конфигурации**

Любой клиентской рабочей станции с интегрированной среды разработки, установите [клиент Microsoft R](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) или [библиотеки Python](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)и затем написать код, который помещает выполнения (называют *контекста удаленных вычислений*) к данным и операций на удаленном сервере SQL. 

Аналогичным образом при использовании выпуск Developer edition, можно создавать решения на клиентской рабочей станции, используя те же библиотеки и интерпретаторов и затем развернуть рабочий код на обучение машины службы (в базе данных) для SQL Server. 

## <a name="version-history"></a>История изменений

Службы SQL Server 2017 г машины обучения — поколения служб SQL Server 2016 R, улучшены, чтобы включить Python. Ниже приведен полный список всех версий с момента их появления до текущего выпуска. 

| Название продукта | Версия подсистемы | Дата выпуска |
|--------------|---------|--------------|
| SQL Server 2017 г машины обучения Services (в базе данных) | R Server 9.2.1 <br/> Сервер Python 9.2 | Октябрь 2017 г. |
| Обучение машины сервера 2017 г. SQL Server (автономный) | R Server 9.2.1 <br/> Сервер Python 9.2 | Октябрь 2017 г. |
| Службы R SQL Server 2016 (в базе данных) | R Server 9.1  | Июля 2017 г.  |
| SQL Server 2016 R Server (изолированный)  |  R Server 9.1 | Июля 2017 г. |



## <a name="documentation-for-each-version"></a>Документация для каждой версии

Последние версии документации по SQL Server зависит от версии. Для служб SQL Server Machine Learning Python доступен только в 2017 г. и более поздней версии, а R поддерживается во всех версиях. Если не указано иное, можно предположить, что документация R применяется 2016 года и 2017 версий.


## <a name="related-machine-learning-products"></a>Связанные машинного обучения продуктов

 +  [Подготовка виртуальной машины Azure](r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)
  
  Azure marketplace включает в себя несколько образов виртуальных машин, включающие машины обучения Server или R Server. Создание виртуальной машины в Microsoft Azure является самым быстрым способом получения для разработки и развертывания моделей прогнозирования. Получены с возможностями масштабирования и общего доступа к уже настроена, которых облегчает внедрение аналитики приложений и интегрировать серверной системы.

+ [Виртуальная машина обработки и анализа данных](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/)

  Последнюю версию данных обработки и анализа виртуальной машины включает машины обучения, а сервер SQL, и массив наиболее популярных средств для машинного обучения, все предварительно и протестирован. Можно создавать записные книжки Jupyter разработки решений в Юлии и использовать библиотеки поддержкой GPU углубленного обучения как MXNet, CNTK и TensorFlow.

<a name="next-steps"></a>

## <a name="next-steps"></a>Следующие шаги

**Шаг 1.** установить и настроить программное обеспечение. 

+ [Установка служб SQL Server 2017 г машинного обучения (в базе данных)](install/sql-machine-learning-services-windows-install.md)

**Шаг 2.** приступить к работе с кодом, используя одну из этих учебников:

+ [Учебник: Запустите Python в T-SQL](tutorials/run-python-using-t-sql.md)
+ [Учебник: Запускать в T-SQL](tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)

**Шаг 3.** Добавьте избранные пакеты R и Python и использовать их вместе с пакетами, предоставляемых корпорацией Майкрософт

+ [R-пакет управления для SQL Server](r/r-package-management-for-sql-server-r-services.md)