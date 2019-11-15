---
title: Библиотека функций olapR R
description: Общие сведения о библиотеке функций olapR в SQL Server 2016 R Services и Службах машинного обучения SQL Server с R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 507bd04140880a3c15f1e72eed49c29ade56769c
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714998"
---
# <a name="olapr-r-library-in-sql-server"></a>olapR (библиотека R в SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**olapR** — это библиотека Майкрософт с функциями R, используемыми для запросов многомерных выражений к кубу OLAP SQL Server Analysis Services. Функции не поддерживают все операции многомерных выражений, но можно создавать запросы, которые создают срезы, выполняют сегментацию, детализацию, свертку и сведение по измерениям. 

Этот пакет не загружен предварительно в сеанс R. Для загрузки библиотеки выполните приведенную ниже команду.

```R
library(olapR)
```

Эту библиотеку можно использовать для подключений к кубу OLAP Analysis Services во всех поддерживаемых версиях SQL Server. В настоящее время соединения с табличной моделью не поддерживаются.

## <a name="package-version"></a>Версия пакета

Текущая версия — 1.0.0 во всех продуктах и загрузках только для Windows, предоставляющих библиотеку.

## <a name="full-reference-documentation"></a>Полная справочная документация

Библиотека **olapr** распространяется в составе нескольких продуктов Майкрософт, но используется в любом из них одинаково. Благодаря сходству функций [документация по отдельным функциям sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) опубликована только в одном разделе в [справочнике по R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) для Microsoft Machine Learning Server. Если для конкретных продуктов функции будут действовать иначе, выявленные расхождения будут приведены на странице справки по функциям.

## <a name="availability-and-location"></a>Расположение и доступность

Этот пакет предоставляется в следующих продуктах, а также в нескольких образах виртуальных машин в Azure. Расположение пакета изменяется соответствующим образом.

Продукт | Местоположение |
--------|----------|
Службы машинного обучения SQL Server (интеграция с R) | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library | 
SQL Server 2016 R Services | C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library
Microsoft Machine Learning Server (R Server) | C:\Program Files\Microsoft\R_SERVER\library |
Microsoft R Client | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Виртуальная машина обработки и анализа данных (в Azure) | C:\Program Files\Microsoft\R Client\R_SERVER\library |
Виртуальная машина SQL Server (в Azure) <sup>1</sup> | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library |

<sup>1</sup> Интеграция с R необязательна в SQL Server. Библиотека olapR будет установлена при добавлении компонента Машинное обучение или функции R во время настройки виртуальной машины.


## <a name="see-also"></a>См. также раздел

[Создание запросов многомерных выражений с помощью olapR](how-to-create-mdx-queries-using-olapr.md)
