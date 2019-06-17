---
title: Преобразование - машинного обучения SQL Server типов данных Python-to-SQL
description: Просмотрите тип converstions явных и неявных данных между кодом Python и SQL Server в решения машинного обучения, обработки и анализа данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 6a7cb7e8f93489bb52c1457fbf25bf7206026914
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62642756"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Сопоставления типов данных между кодом Python и SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Для решений Python, выполните функцию интеграции Python в службах машинного обучения SQL Server просмотрите список неподдерживаемых типов данных и преобразования типов данных, которые могут осуществляться неявно, когда данные передаются между Python и SQL Server.

## <a name="python-version"></a>Версия Python

SQL Server 2017 Anaconda 4.2 распространения и Python 3.6.

Подмножество функций RevoScaleR (rxLinMod rxLogit, rxPredict, rxDTrees, rxBTrees, может быть несколько других) обеспечивается с помощью API Python, с помощью нового пакета Python **revoscalepy**. Этот пакет можно использовать для работы с данными, с помощью кадров данных Pandas, файлы XDF или SQL-запросы данных.

Дополнительные сведения см. в разделе [revoscalepy модуля в SQL Server](ref-py-revoscalepy.md) и [Справочник по функциям revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

Python поддерживает ограниченный набор типов данных по сравнению с SQL Server. В результате каждый раз при использовании данных из SQL Server в скриптах Python, данные могут неявно преобразовываться в совместимый тип данных. Тем не менее часто точное преобразование не может выполняться автоматически и будет возвращена ошибка.

## <a name="python-and-sql-data-types"></a>Python и типы данных SQL

В этой таблице перечислены неявных преобразований, которые предоставляются. Другие типы данных не поддерживаются.

|SQLtype|Тип Python|
|-------|-----------|
|**bigint**|`numeric`|
|**binary**|`raw`|
|**bit**|`bool`|
|**char**|`str`|
|**float**|`float64`|
|**int**|`int32`|
|**nchar**|`str`|
|**nvarchar**|`str`|
|**nvarchar(max)**|`str`|
|**real**|`float32`|
|**smallint**|`int16`|
|**tinyint**|`uint8`|
|**varbinary**|`bytes`|
|**varbinary(max)**|`bytes`|
|**varchar(n)**|`str`|
|**varchar(max)**|`str`|

## <a name="see-also"></a>См. также

