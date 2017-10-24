---
title: "Справочник по API для служб SQL Server Machine Learning | Документы Microsoft"
ms.custom: 
ms.date: 07/31/2017
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1c776c43d66d01a2f721b5d3d8bc540741bf8b13
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---

# <a name="api-reference-for-sql-server-machine-learning-services"></a>Справочник по API для служб SQL Server машины обучения

В этой статье ссылки на справочную документацию для машинного обучения интерфейсы API, используемый сервером SQL Server. 

**Применяется к:** служб R SQL Server 2016, SQL Server 2017 г машинного обучения служб

В большинстве случаев SQL Server использует те же библиотеки R и Python, входящих в состав Microsoft R Server и Microsoft Server обучения машины. 

> [!NOTE]
> Документация для всех интерфейсов API является производным от исходного кода и не после измененного.

## <a name="r"></a>Чтение

+ [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)

    Масштабируемые алгоритмы, поддерживающие контекстах удаленных вычислений и несколько источников данных.

+ [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)

    Быстрый, масштабируемые обучающих алгоритмов и преобразований для RevoScaleR требует R. машины.

+ [olapR](https://docs.microsoft.com/r-server/r-reference/olapr/olapr)

   Считывает схему источников данных OLAP и выполняет запросы многомерных Выражений.

+ [sqlrutils](https://docs.microsoft.com/r-server/r-reference/sqlrutils/sqlrutils)

    Вспомогательные функции для создания правильного формата хранимую процедуру из кода R.

+ [mrsdeploy](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package)

   Функции для установления удаленного сеанса в консольном приложении, а также для публикации и управления веб-служба, использующая код R или Python.

## <a name="python"></a>Python

+ [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)

    Эквивалент пакета RevoScaleR для языка R Python. Поддерживает же контексты вычислений источники данных.

+ [Microsoftml для Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)

    Эквивалент Python MicrosoftML пакета для R. поддерживает же контексты вычислений и источники данных и включает в себя быстрых, масштабируемых алгоритмы и преобразования от корпорации Майкрософт.

## <a name="related-apis"></a>Связанные API

+ [Справочник по функциям RevoPEMAR](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

    Поддерживает разработку для параллельных алгоритмов

+ [RevoUtils](https://docs.microsoft.com/r-server/r-reference/revoutils/revoutils)

    Служебные функции для использования в средах RevoScaleR

## <a name="other"></a>Другое

«Инструкции» и сводки, определенных с использованием этих API Python в SQL Server или R можно найти здесь:

+ [ScaleR функции для работы с SQL Server](scaler-functions-for-working-with-sql-server-data.md)
+ [Создание хранимой процедуры, с помощью sqlrutils](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
+ [Чтение данных многомерных Выражений в R, с помощью olapR](how-to-create-mdx-queries-using-olapr.md)

