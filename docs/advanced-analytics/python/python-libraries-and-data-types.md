---
title: Библиотеки Python | Документы Microsoft
ms.custom: ''
ms.date: 03/30/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 14691885d6dcdb91558ddc9566f4320c8119a9dd
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="python-libraries-and-data-types"></a>Библиотеки Python и типы данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описываются библиотеки Python, которые входят в состав следующих продуктов:

+ Изучение служб (в базе данных) машины SQL Server
+ Microsoft машинного обучения Server (изолированный)

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



