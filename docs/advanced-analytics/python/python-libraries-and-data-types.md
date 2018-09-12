---
title: Python библиотеки и типы данных в SQL Server машинного обучения | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 384c8c94bdef65e41af999848c9bac63fc0c8d40
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43888370"
---
# <a name="python-libraries-and-data-types"></a>Библиотеки и типы данных Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается библиотек Python, которые входят в состав службы машинного обучения из состава SQL Server (в базе данных) и установки (автономная).

В этой статье также перечислены неподдерживаемые типы данных и списки данных тип преобразования, может выполняться неявно, когда данные передаются между Python и SQL Server.

## <a name="python-version"></a>Версия Python

SQL Server 2017 Anaconda 4.2 распространения и Python 3.6.

Подмножество функций RevoScaleR (rxLinMod rxLogit, rxPredict, rxDTrees, rxBTrees, может быть несколько других) обеспечивается с помощью API Python, с помощью нового пакета Python **revoscalepy**. Этот пакет можно использовать для работы с данными, с помощью кадров данных Pandas, файлы XDF или SQL-запросы данных.

Дополнительные сведения см. в разделе [Какова revoscalepy?](what-is-revoscalepy.md).

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



