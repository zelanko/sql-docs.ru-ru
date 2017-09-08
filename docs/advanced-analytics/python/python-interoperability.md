---
title: "Взаимодействие Python | Документы Microsoft"
ms.custom: 
ms.date: 04/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 32762183ff5273998848978238788cc830319b91
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="python-interoperability"></a>Взаимодействие с Python

В этом разделе описаны компоненты Python, которые будут установлены, если включена функция **службы обучения машины (в базе данных)** и выберите в качестве языка Python.

> [!NOTE]
> Поддержка Python — это функция предварительной версии и еще находится в стадии разработки.

## <a name="python-components"></a>Компоненты Python

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]не изменяйте исполняемые файлы Python. Среда выполнения Python устанавливается независимо от средства SQL, а также выполняется за пределами [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] процесса.

Распределение, которое связано с определенным [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] экземпляра можно найти в папке, связанный с экземпляром.

Например если вы установили службы обучения машины с параметром Python на экземпляре по умолчанию, найдите его в разделе:

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER`

Установка служб SQL Server 2017 г машины обучения добавляет распределение Anaconda Python. В частности используются установщики Anaconda 3, основании Anaconda 4.3 ветви. Ожидаемый уровень Python для SQL Server 2017 г. — Python 3.5.

## <a name="new-in-this-release"></a>В этом выпуске

Список пакетов, поддерживаемых дистрибутив Anaconda, см. на сайте компания Continuum analytics: [Anaconda список пакетов](https://docs.continuum.io/anaconda/pkg-docs)

Машины обучения в 2017 г. SQL Server также включен новый **revoscalepy** библиотеки для Python.

Эта библиотека предоставляет следующие функциональные возможности, эквивалентное значению **RevoScaleR** пакет для Microsoft R. Другими словами, поддерживает создание контекстах удаленных вычислений, а также различными моделей масштабируемой машинного обучения, такие как **rxLinMod**. Дополнительные сведения о RevoScaleR см. в разделе [распределенных и параллельных вычислений с ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing).

Поскольку поддержки для Python — это функция предварительной версии и находится в разработке, **revoscalepy** библиотека в настоящее время содержит только подмножество функциональных возможностей RevoScaleR. 

Может включать последующих добавлений [Когнитивных набор средств Microsoft](https://www.microsoft.com/research/product/cognitive-toolkit/). Прежнее название — CNTK, эта библиотека поддерживает различные модели нейронной сети, включая convolutional сетей (CNN), повторяющемся сетей (RNN) и Long короткий памяти термин сетей (LSTM).

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

[Библиотеки Python и типы данных](python-libraries-and-data-types.md)
