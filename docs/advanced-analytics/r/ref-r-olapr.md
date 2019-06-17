---
title: Библиотека функций olapR R - служб машинного обучения SQL Server
description: Общие сведения о библиотеке olapR функций в SQL Server 2016 R Services и служб SQL Server 2017 машинного обучения с помощью языка R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e5419900b8ba573ec0658a5022be68105b0b8607
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62641855"
---
# <a name="olapr-r-library-in-sql-server"></a>olapR (библиотека R в SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**olapR** — это библиотека Microsoft функций R, используемых для запросов многомерных Выражений для куба OLAP служб Analysis Services SQL Server. Функции не поддерживают все операции многомерных Выражений, но можно создавать запросы, этому срезу кости, Углубленная детализация, rollup и сведения по измерениям. 

Этот пакет не предварительно в сеанс R. Выполните следующую команду, чтобы загрузить библиотеку.

```R
library(olapR)
```

Эту библиотеку можно использовать для подключения к кубу OLAP служб Analysis Services на всех поддерживаемых версиях SQL Server. В настоящее время не поддерживаются подключения к табличной модели.

## <a name="package-version"></a>Версия пакета

Текущая версия — 1.0.0 во всех продуктах только для Windows и загружает, предоставляя библиотеки.

## <a name="full-reference-documentation"></a>Полная справочная документация

**Olapr** library распространяется в нескольких продуктов корпорации Microsoft, но использование совпадает ли вы получаете библиотеки в SQL Server или другой продукт. Так как функции являются одинаковыми, [документации для отдельных sqlrutils функций](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) публикуется только в одном месте в разделе [ссылку R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) для сервера машинного обучения Майкрософт. Следует любого конкретного продукта существует поведения, несоответствия будут указаны в странице справки по функции.

## <a name="availability-and-location"></a>Доступность и расположение

Этот пакет предоставляется в следующих продуктах, а также на несколько образов виртуальных машин в Azure. Расположение пакета изменяется соответствующим образом.

Продукт | Местоположение |
--------|----------|
Служб SQL Server 2017 машинного обучения (с интеграцией R) | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library | 
SQL Server 2016 R Services | C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library
Microsoft Machine Learning Server (R Server) | C:\Program Files\Microsoft\R_SERVER\library |
Microsoft R Client | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Виртуальная машина анализа данных (в Azure) | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Виртуальной машине SQL Server (в Azure) <sup>1</sup> | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library |

<sup>1</sup> интеграция R является необязательным в SQL Server. Библиотека olapR устанавливается при добавлении машинного обучения или компонент R во время настройки виртуальной Машины.


## <a name="see-also"></a>См. также

[Создание запросов многомерных Выражений, с помощью olapR](how-to-create-mdx-queries-using-olapr.md)
