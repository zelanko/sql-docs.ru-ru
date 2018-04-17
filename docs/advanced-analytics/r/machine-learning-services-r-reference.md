---
title: Справочник по API для служб SQL Server Machine Learning | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e8995dbf106db2d9b067e6c26c4277d561d68902
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="api-reference-for-sql-server-machine-learning-services"></a>Справочник по API для служб SQL Server машины обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье ссылки на справочную документацию для машинного обучения интерфейсы API, используемый сервером SQL Server.

**Применяется к:** служб R SQL Server 2016, SQL Server 2017 г машинного обучения служб

В большинстве случаев SQL Server использует те же библиотеки R и Python, входящих в состав Microsoft R Server и Microsoft Server обучения машины. 

> [!NOTE]
> Документация для всех интерфейсов API является производным от исходного кода и не были изменены. Если возникают ошибки, добавьте комментарий в справочной документации API. 

## <a name="r"></a>Чтение

+ [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)

    Масштабируемые алгоритмы, поддерживающие контекстах удаленных вычислений и несколько источников данных.

+ [MicrosoftML](https://docs.microsoft.com/machine-learning-serverr-reference/microsoftml/microsoftml-package)

    Быстрый, масштабируемые обучающих алгоритмов и преобразований для RevoScaleR требует R. машины.

+ [OlapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr)

   Считывает схему источников данных OLAP и выполняет запросы многомерных Выражений.

+ [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)

    Вспомогательные функции для создания правильного формата хранимую процедуру из кода R.

+ [mrsdeploy](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)

   Функции для установления удаленного сеанса в консольном приложении, а также для публикации и управления веб-служба, использующая код R или Python.

## <a name="python"></a>Python

+ [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)

    Эквивалент пакета RevoScaleR для языка R Python. Поддерживает же контексты вычислений источники данных.

+ [Microsoftml для Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)

    Эквивалент Python MicrosoftML пакета для R. поддерживает же контексты вычислений и источники данных и включает в себя быстрых, масштабируемых алгоритмы и преобразования от корпорации Майкрософт. 

## <a name="related-apis"></a>Связанные API

+ [Справочник по функциям RevoPEMAR](https://docs.microsoft.com/machine-learning-server/r-reference/revopemar/pemar)

    Поддерживает разработку для параллельных алгоритмов

+ [RevoUtils](https://docs.microsoft.com/machine-learning-server/r-reference/revoutils/revoutils)

    Служебные функции для использования в средах RevoScaleR

## <a name="other"></a>Другое

«Инструкции» и сводки, определенных с использованием этих API Python в SQL Server или R можно найти здесь:

+ [ScaleR функции для работы с SQL Server](scaler-functions-for-working-with-sql-server-data.md)
+ [Создание хранимой процедуры, с помощью sqlrutils](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
+ [Чтение данных многомерных Выражений в R, с помощью olapR](how-to-create-mdx-queries-using-olapr.md)
