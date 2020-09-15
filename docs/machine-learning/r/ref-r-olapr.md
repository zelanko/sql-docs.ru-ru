---
title: Пакет R olapR
description: olapR — это пакет R от Майкрософт, используемый для запросов многомерных выражений к кубу OLAP SQL Server Analysis Services. Функции не поддерживают все операции многомерных выражений, но можно создавать запросы, которые создают срезы, выполняют сегментацию, детализацию, свертку и сведение по измерениям. Этот пакет входит в состав Служб машинного обучения SQL Server и служб SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/14/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ba5f9677022eb07a8810f3ea9c5dcffeaa716e7c
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2020
ms.locfileid: "88179938"
---
# <a name="olapr-r-package-in-sql-server-machine-learning-services"></a>olapR (пакет R в Службах машинного обучения SQL Server)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

**olapR** — это пакет R от Майкрософт, используемый для запросов многомерных выражений к кубу OLAP SQL Server Analysis Services. Функции не поддерживают все операции многомерных выражений, но можно создавать запросы, которые создают срезы, выполняют сегментацию, детализацию, свертку и сведение по измерениям. Этот пакет входит в состав [Служб машинного обучения SQL Server](../sql-server-machine-learning-services.md) и [служб SQL Server 2016 R Services](sql-server-r-services.md).

Этот пакет можно использовать для подключений к кубу OLAP Analysis Services во всех поддерживаемых версиях SQL Server. В настоящее время соединения с табличной моделью не поддерживаются.

## <a name="load-package"></a>Загрузка пакета

Пакет **olapR** не загружен предварительно в сеанс R. Для загрузки пакета выполните приведенную ниже команду.

```R
library(olapR)
```

## <a name="package-version"></a>Версия пакета

Текущая версия — 1.0.0 во всех продуктах и загрузках только для Windows, предоставляющих пакет.

## <a name="full-reference-documentation"></a>Полная справочная документация

Пакет **olapr** распространяется в нескольких продуктах Майкрософт, но его использование не зависит от того, получили ли вы его в SQL Server или в другом продукте. Благодаря сходству функций [документация по отдельным функциям sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) опубликована только в одном разделе в [справочнике по R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) для Microsoft Machine Learning Server. Если для конкретных продуктов функции будут действовать иначе, выявленные расхождения будут приведены на странице справки по функциям.

## <a name="availability-and-location"></a>Расположение и доступность

Этот пакет предоставляется в следующих продуктах, а также в нескольких образах виртуальных машин в Azure. Расположение пакета изменяется соответствующим образом.

Продукт | Расположение |
--------|----------|
Службы машинного обучения SQL Server (интеграция с R) | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library | 
SQL Server 2016 R Services | C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library
Microsoft Machine Learning Server (R Server) | C:\Program Files\Microsoft\R_SERVER\library |
Microsoft R Client | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Виртуальная машина обработки и анализа данных (в Azure) | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Виртуальная машина SQL Server (в Azure) <sup>1</sup> | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library |

<sup>1</sup> Интеграция с R необязательна в SQL Server. Пакет olapR будет установлен при добавлении компонента "Машинное обучение" или функции R во время настройки виртуальной машины.


## <a name="see-also"></a>См. также раздел

[Создание запросов многомерных выражений с помощью olapR](how-to-create-mdx-queries-using-olapr.md)
