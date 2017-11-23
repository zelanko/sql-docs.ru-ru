---
title: "Python взаимодействие с SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 11/03/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: ee7187d490c8da80c66fb27156b2726e71782238
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="python-interoperability-with-sql-server"></a>Python взаимодействие с SQL Server

В этом разделе описаны компоненты Python, которые будут установлены, если включена функция **службы обучения машины (в базе данных)** и выберите в качестве языка Python.

## <a name="python-components"></a>Компоненты Python

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]не изменяйте исполняемые файлы Python. Среда выполнения Python устанавливается независимо от средства SQL, а также выполняется за пределами [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] процесса.

Распределение, которое связано с определенным [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] экземпляра можно найти в папке, связанный с экземпляром.

Например если вы установили службы обучения машины с параметром Python на экземпляре по умолчанию, найдите его в разделе:

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

Установка служб SQL Server 2017 г машины обучения добавляет распределение Anaconda Python. В частности используются установщики Anaconda 3, основании Anaconda 4.3 ветви. Ожидаемый уровень Python для SQL Server 2017 г. — Python 3.5.

## <a name="new-python-packages-in-this-release"></a>Новые пакеты Python в этом выпуске

Список пакетов, поддерживаемых дистрибутив Anaconda, см. на сайте компания Continuum analytics: [Anaconda список пакетов](https://docs.continuum.io/anaconda/pkg-docs)

Машины обучения в 2017 г. SQL Server также включен новый **revoscalepy** библиотеки для Python.

Эта библиотека предоставляет следующие функциональные возможности, эквивалентное значению **RevoScaleR** пакет для Microsoft R. Другими словами, поддерживает создание контекстах удаленных вычислений, а также различными моделей масштабируемой машинного обучения, такие как **rxLinMod**. Дополнительные сведения о RevoScaleR см. в разделе [распределенных и параллельных вычислений с ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing).

[Microsoftml для Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) пакет устанавливается как часть машинного обучения SQL Server при добавлении Python в установку. Этот пакет содержит много алгоритмов машинного обучения, оптимизированные для скорость и точность, а также строки преобразования для работы с текстом и изображениями. Дополнительные сведения см. в разделе [с помощью пакета MicrosoftML с SQL Server](https://docs.microsoft.com/sql/advanced-analytics/using-the-microsoftml-package).

Microsoftml и revoscalepy тесно связаны; Источники данных в microsoftml определяются как revoscalepy объектов. Вычисление ограничения контекста в операцию передачи revoscalepy microsoftml. А именно все функциональные возможности доступны для локальных операций, но при переключении контекста удаленных вычислений необходим RxInSqlServer.

## <a name="using-python-in-sql-server"></a>С помощью Python в SQL Server

Вы импортируете **revoscalepy** модуля в коде Python и затем вызывать функции из модуля, как и все остальные функции Python.

Входные данные для Python должен быть табличной. Все результаты Python должен возвращаться в виде **pandas** кадра данных.

Можно выполнять код Python в T-SQL, путем внедрения скрипта в хранимой процедуре.

Можно также запускать код из локальной интегрированную среду разработки Python и имеют скрипта, выполняемого на компьютере SQL Server, путем определения контекста удаленных вычислений.

Можно работать с локальными данными, получение данных из SQL Server или других источников данных ODBC или использовать формат файла XDF для обмена данными с другими источниками, или с помощью решений R.

**Дополнительные сведения**

+ Поддерживаемые функции: [возможности revoscalepy](what-is-revoscalepy.md) 
+ Поддерживаемые типы данных Python: [библиотеки Python и типы данных](python-libraries-and-data-types.md)
+ Поддерживаемые источники данных: ODBC баз данных SQL Server и XDF-файлов
+ Поддерживается контекстов вычислений: local или SQL Server

### <a name="licensing"></a>Лицензирование

В процессе установки службы обучения машины с Python должен дать согласие с условиями открытой лицензии GNU.

## <a name="see-also"></a>См. также:

[Библиотеки и типы данных Python](python-libraries-and-data-types.md)
