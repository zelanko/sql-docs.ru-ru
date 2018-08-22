---
title: Python библиотеки и типы данных в SQL Server машинного обучения | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7b977d079589dbb4c54d5c31fec644d9f984dd61
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "40434854"
---
# <a name="python-libraries-and-data-types"></a>Библиотеки и типы данных Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается библиотек Python, которые входят в состав службы машинного обучения из состава SQL Server (в базе данных) и установки (автономная).

В этой статье также перечислены неподдерживаемые типы данных и списки данных тип преобразования, может выполняться неявно, когда данные передаются между Python и SQL Server.

## <a name="python-version"></a>Версия Python

SQL Server 2017 Anaconda 4.2 распространения и Python 3.6.

Подмножество функций RevoScaleR (rxLinMod rxLogit, rxPredict, rxDTrees, rxBTrees, может быть несколько других) обеспечивается с помощью API Python, с помощью нового пакета Python **revoscalepy**. Этот пакет можно использовать для работы с данными, с помощью кадров данных Pandas, файлы XDF или SQL-запросы данных.

Дополнительные сведения см. в разделе [Какова revoscalepy?](what-is-revoscalepy.md).

## <a name="python-and-sql-data-types"></a>Python и типы данных SQL

Python поддерживает ограниченный набор типов данных по сравнению с SQL Server.

Таким образом, при использовании данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в сценарии Python, данные могут быть неявно преобразован в совместимый тип данных. Тем не менее часто точное преобразование не может выполняться автоматически и будет возвращена ошибка.

В этой таблице перечислены неявных преобразований, которые предоставляются. Другие типы данных не поддерживаются.

|SQLtype|Тип Python|
|-|-|
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



