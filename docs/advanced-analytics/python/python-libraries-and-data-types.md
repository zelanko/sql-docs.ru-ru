---
title: Python библиотек и типы данных в SQL Server машинного обучения | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f8dfa7f343a3a179b05b624a083238e08011c4a5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31201696"
---
# <a name="python-libraries-and-data-types"></a>Python библиотек и типы данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается библиотеки Python, которые входят в состав службы обучения машины SQL Server (в базе данных) и установок (автономный).

В этой статье также перечислены неподдерживаемые типы данных и списки тип данных преобразования, которые может выполнять неявно при передаче данных между Python и SQL Server.

## <a name="python-version"></a>Версия Python

2017 г CTP-версия SQL Server 2.0 включает часть дистрибутив Anaconda и Python 3.6.

Часть возможностей RevoScaleR (rxLinMod rxLogit, rxPredict, rxDTrees, rxBTrees, может быть несколько других) с помощью API-интерфейсы Python, с помощью нового пакета Python **revoscalepy**. Этот пакет можно использовать для работы с данными, с помощью кадров данных Pandas, XDF-файлов или запросов анализа данных SQL.

Дополнительные сведения см. в разделе [возможности revoscalepy?](what-is-revoscalepy.md).

## <a name="python-and-sql-data-types"></a>Python и типы данных SQL

Python поддерживает ограниченное число типов данных по сравнению с SQL Server.

В результате при использовании данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в скриптах Python, данные могут неявно преобразовываться в совместимый тип данных. Тем не менее часто точное преобразование не может выполняться автоматически, и возвращается сообщение об ошибке.

В этой таблице перечислены неявные преобразования, которые предоставляются. Другие типы данных не поддерживаются.

|SQLtype|Тип Python|
|-|-|
|**bigint**|`numeric`|
|**binary**|`raw`|
|**бит**|`bool`|
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



