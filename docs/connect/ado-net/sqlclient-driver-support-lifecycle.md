---
title: Жизненный цикл поддержки драйвера SqlClient
description: Страница с информацией о жизненном цикле поддержки продукта.
ms.date: 09/08/2020
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 5b9b461454db98de77ed6003477b7a02114067eb
ms.sourcegitcommit: 71a334c5120a1bc3809d7657294fe44f6c909282
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/09/2020
ms.locfileid: "89614593"
---
# <a name="sqlclient-driver-support-lifecycle"></a>Жизненный цикл поддержки драйвера SqlClient

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Библиотека Microsoft.Data.SqlClient соответствует последней версии политики поддержки .NET Core для всех выпусков.

[Просмотреть политику поддержки .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)

## <a name="microsoftdatasqlclient-release-cadence"></a>Частота выпусков Microsoft.Data.SqlClient

Новые стабильные (общедоступные) выпуски публикуются каждые шесть месяцев с обычной частотой, начиная с версии 1.2, а между ними выходят по 2–3 предварительных выпуска. Выпуски долгосрочной поддержки (LTS) будут отбираться заинтересованными лицами и специалистами по поддержке на основе нескольких характеристик и отзывов клиентов.

### <a name="release-life-cycles"></a>Жизненный цикл выпусков

| Версия | Дата официального выпуска | Последняя версия исправления | Дата выпуска исправления | Уровень поддержки  | Окончание поддержки |
| -- | -- | -- | -- | -- | -- |
| 2.0 | 16 июня 2020 г. | 2.0.1 | 25 августа 2020 г. | Текущий | |
| 1.1 | 20 ноября 2019 г. | 1.1.3 | 15 мая 2020 г. | LTS | 21 ноября 2022 г. |
| 1.0 | 28 августа 2019 г. | 1.0.19269.1 | 26 сентября 2019 г. | Текущий | 20 февраля 2020 г. |

### <a name="long-term-support-lts-releases"></a>Выпуски долгосрочной поддержки (LTS)

Выпуски долгосрочной поддержки поддерживаются в течение трех лет после первоначального выпуска.

### <a name="current-releases"></a>Текущие выпуски

Текущие выпуски поддерживаются в течение трех месяцев после следующего текущего выпуска или выпуска долгосрочной поддержки.

## <a name="sql-version-compatibility-with-microsoftdatasqlclient"></a>Совместимость версий SQL с Microsoft.Data.SqlClient

|Версия базы данных&nbsp;&#8594;<br />&#8595; Версия драйвера|База данных SQL Azure|Azure Synapse Analytics|Управляемый экземпляр SQL Azure|SQL Server 2019|SQL Server 2017|SQL Server 2016|SQL Server 2014|SQL Server 2012|
|---|---|---|---|---|---|---|---|---|
|2.0|Да|Да|Да|Да|Да|Да|Да|Да|
|1,1|Да|Да|Да|Да|Да|Да|Да|Да|
|1.0|Да|Да|Да|Да|Да|Да|Да|Да|
