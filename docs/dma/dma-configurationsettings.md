---
title: Настройка параметров для помощника по миграции данных (SQL Server) | Документация Майкрософт
description: Узнайте, как настроить параметры для Data Migration Assistant, обновляя значения в файле конфигурации
ms.custom: ''
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.openlocfilehash: cb50b5380a305382bfb5494273cd335c8b60f51e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058873"
---
# <a name="configure-settings-for-data-migration-assistant"></a>Настройка параметров для помощника по миграции данных

Можно оптимизировать определенные поведение Data Migration Assistant, установив значения конфигурации в файле dma.exe.config. В этой статье описывается значения ключа конфигурации.

Файл dma.exe.config Data Migration Assistant классического приложения и программу командной строки можно найти в следующих папках на компьютере.

- Классическое приложение

  % ProgramFiles %\\Microsoft Data Migration Assistant\\dma.exe.config

- Программа командной строки

  % ProgramFiles %\\Microsoft Data Migration Assistant\\dmacmd.exe.config 

Не забудьте сохранить копию исходного файла конфигурации перед внесением изменений. После внесения изменений перезапустите помощник по миграции данных новые значения конфигурации вступили в силу.

## <a name="number-of-databases-to-assess-in-parallel"></a>Количество баз данных для оценки в параллельном режиме

Помощник по миграции данных получает доступ к нескольким базам данных в параллельном режиме. Во время оценки Data Migration Assistant извлечение приложения уровня данных (dacpac), чтобы разобраться со схемой базы данных. Эта операция может истечь время ожидания, если несколько баз данных на одном сервере оцениваются в параллельном режиме. 

Начиная с версии 2.0 Data Migration Assistant, вы можете управлять это путем задания параметра конфигурации parallelDatabases. Значение по умолчанию — 8.

```
<advisorGroup>

<workflowSettings>

<assessment parallelDatabases="8" />

</workflowSettings>

</advisorGroup>
```




## <a name="number-of-databases-to-migrate-in-parallel"></a>Количество баз данных для миграции в параллельном режиме

Помощник по миграции данных переносит несколько баз данных в параллельном режиме, прежде чем миграция имен входа. Во время миграции Data Migration Assistant будет создать резервную копию базы данных-источника, при необходимости скопируйте резервную копию и затем восстановить ее на целевом сервере. Могут возникать сбои времени ожидания, при выборе нескольких баз данных для миграции. 

Начиная с версии 2.0-помощник по миграции данных, в случае возникновения этой проблемы можно уменьшить значение конфигурации parallelDatabases. Можно увеличить значение, чтобы сократить общее время миграции.

```
<advisorGroup>

<workflowSettings>

<migration parallelDatabases="8″ />

</workflowSettings>

</advisorGroup>
```


## <a name="dacfx-settings"></a>Параметры DacFX

Во время оценки Data Migration Assistant извлечение приложения уровня данных (dacpac), чтобы разобраться со схемой базы данных. Эта операция может завершиться сбоем с тайм-ауты для очень крупных баз данных, или если сервер находится под нагрузкой. Начиная с версии 1.0 переноса данных, можно изменить следующие значения конфигурации, чтобы избежать ошибок. 

> [!NOTE]
> Всего &lt;dacfx&gt; закомментирована запись по умолчанию. Удалить комментарии, а затем измените значение, при необходимости.

- commandTimeout

   Этот параметр задает свойство IDbCommand.CommandTimeout в *секунд*. (По умолчанию = 60)

- databaseLockTimeout

   Этот параметр аналогичен [ЗАДАТЬ БЛОКИРОВКУ\_времени ожидания TIMEOUT\_период](../t-sql/statements/set-lock-timeout-transact-sql.md) в *миллисекунд*. (По умолчанию = 5000)

- maxDataReaderDegreeOfParallelism

  Этот параметр задает число подключений пула подключений SQL для использования. (По умолчанию = 8)

```
<advisorGroup>

<advisorSettings>

<dacFx  commandTimeout="60" databaseLockTimeout="5000"
maxDataReaderDegreeOfParallelism="8"/>

</advisorSettings>

</advisorGroup>
```

## <a name="stretch-database-recommendation-threshold"></a>Stretch Database: Пороговое значение рекомендации

С помощью [SQL Server Stretch Database](https://docs.microsoft.com/sql/sql-server/stretch-database/stretch-database), динамически, можно растянуть "горячего" резервирования и "холодные" данные транзакций из Microsoft SQL Server 2016 в Azure. Stretch Database целевых объектов транзакционных баз данных с большим количеством "холодных" данных. Рекомендация Stretch Database, в разделе рекомендация по функции хранилища, сначала определяет таблицы, которому она предположительно будет преимущества этой функции, а затем он определяет изменения, которые должны быть выполнены, чтобы разрешить использование таблицы для этой функции.

Начиная с версии 2.0 Data Migration Assistant, вы можете контролировать это пороговое значение для таблицы для Stretch Database компонента с помощью recommendedNumberOfRows значение конфигурации. Значение по умолчанию — 100 000 строк. Если вы хотите проанализировать возможности stretch для даже небольших таблиц, уменьшите значение соответствующим образом.

```
<advisorGroup>

<advisorSettings>

<stretchDBAdvisor  recommendedNumberOfRows="100000" />

</advisorSettings>

</advisorGroup>
```


## <a name="sql-connection-timeout"></a>Время ожидания соединения SQL

Вы можете управлять [время ожидания подключения SQL](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectiontimeout(v=vs.110).aspx) для исходных и целевых экземпляров во время выполнения оценки или миграции, установив значение времени ожидания подключения в указанное число секунд. Значение по умолчанию — 15 секунд.

```
<appSettings>

<add key="ConnectionTimeout" value="15" />

</appSettings>
```


## <a name="see-also"></a>См. также

[Скачать помощник по миграции данных](https://www.microsoft.com/download/details.aspx?id=53595)
