---
title: Параметры конфигурации (данных помощник миграции SQL Server) | Документы Microsoft
ms.custom: ''
ms.date: 08/31/2017
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 4b42f816755b312f95609bd25ac6122b8fbf321c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32867209"
---
# <a name="configuration-settings-for-data-migration-assistant"></a>Параметры конфигурации для помощника по миграции данных

Можно выполнить тонкую настройку определенных данных помощник по миграции с помощью значений конфигурации в файле dma.exe.config поведение. В этой статье описаны значения ключа конфигурации.

Файл dma.exe.config для приложения рабочего стола помощник по миграции данных и программу командной строки можно найти в следующих папках на компьютере.

- Классическое приложение

  % ProgramFiles %\\помощник по миграции данных Microsoft\\dma.exe.config

- Служебная программа командной строки

  % ProgramFiles %\\помощник по миграции данных Microsoft\\dmacmd.exe.config 

Обязательно сохраните копию исходного файла конфигурации перед внесением каких-либо изменений. После внесения изменений, перезапустите данных помощник по миграции для новые значения конфигурации вступили в силу.

## <a name="number-of-databases-to-assess-in-parallel"></a>Число баз данных для оценки в параллельном режиме

Помощник по миграции данных оценивает несколько баз данных в параллельном режиме. В процессе оценки помощник по миграции данных извлекает приложение уровня данных (dacpac) для понимания схемы базы данных. Эта операция может прерваться, если несколько баз данных на том же сервере оцениваются в параллельном режиме. 

Начиная с версии 2.0 помощник по миграции данных, можно обеспечить управление это, указав parallelDatabases значение конфигурации. Значение по умолчанию — 8.

```
<advisorGroup>

<workflowSettings>

<assessment parallelDatabases="8" />

</workflowSettings>

</advisorGroup>
```




## <a name="number-of-databases-to-migrate-in-parallel"></a>Число баз данных для миграции в параллельном режиме

Помощник по миграции данных переносятся несколько баз данных в параллельном режиме, перед перенос имен входа. Во время миграции помощник по миграции данных будет создать резервную копию базы данных-источника, при необходимости создайте резервную копию и восстановите его на целевом сервере. Возможны ошибки времени ожидания при выборе нескольких баз данных для миграции. 

Начиная с v2.0 помощник по миграции данных, в случае возникновения этой проблемы можно уменьшить значение parallelDatabases конфигурации. Можно увеличить значение, чтобы сократить общее время миграции.

```
<advisorGroup>

<workflowSettings>

<migration parallelDatabases=”8″ />

</workflowSettings>

</advisorGroup>
```


## <a name="dacfx-settings"></a>Параметры DacFX

В процессе оценки помощник по миграции данных извлекает приложение уровня данных (dacpac) для понимания схемы базы данных. Эта операция может завершиться тайм-аутов для очень больших баз данных, или если сервер работает под нагрузкой. Начиная с версии 1.0 переноса данных, можно изменить следующие значения конфигурации, чтобы избежать ошибок. 

> [!NOTE]
> Всего &lt;dacfx&gt; операция закомментирована по умолчанию. Удалить все комментарии и при необходимости измените значение.

- CommandTimeout

   Этот параметр задает свойство IDbCommand.CommandTimeout в *секунд*. (По умолчанию = 60)

- databaseLockTimeout

   Это эквивалентно [УСТАНОВИТЬ БЛОКИРОВКИ\_время ожидания TIMEOUT\_период ](../t-sql/statements/set-lock-timeout-transact-sql.md) в *миллисекунд*. (По умолчанию = 5000)

- maxDataReaderDegreeOfParallelism

   Число подключений пула подключений SQL для использования. (По умолчанию = 8)

```
<advisorGroup>

<advisorSettings>

<dacFx  commandTimeout="60" databaseLockTimeout="5000"
maxDataReaderDegreeOfParallelism="8"/>

</advisorSettings>

</advisorGroup>
```


## <a name="stretch-database-recommendation-threshold"></a>Переноса базы данных: Пороговое значение рекомендация

С [базы данных Stretch SQL Server](https://docs.microsoft.com/sql/sql-server/stretch-database/stretch-database), можно растянуть динамически горячие и холодные данные о транзакциях из Microsoft SQL Server 2016 в Azure. Stretch целевых объектов транзакций баз данных с большим объемом холодных данных. Рекомендации базы данных Stretch, в разделе рекомендаций компонент хранилища, сначала определяет таблицы, он считает выиграет от этой функции, а затем он находит изменения, которые должны быть выполнены для включения таблицы для этой функции.

Начиная с версии 2.0 помощник по миграции данных, можно управлять это пороговое значение для таблицы попасть под функция растяжения базы данных, с помощью значения конфигурации recommendedNumberOfRows. Значение по умолчанию — 100 000 строк. Если вы хотите проанализировать возможности переноса для даже для небольших таблиц, соответствующим образом затем уменьшите значение.

```
<advisorGroup>

<advisorSettings>

<stretchDBAdvisor  recommendedNumberOfRows="100000" />

</advisorSettings>

</advisorGroup>
```


## <a name="sql-connection-timeout"></a>Время ожидания соединения SQL

Можно управлять [время ожидания подключения SQL](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectiontimeout(v=vs.110).aspx) для исходной и целевой экземпляры во время выполнения оценки или миграции, установив значение времени ожидания подключения в указанное количество секунд. Значение по умолчанию — 15 секунд.

```
<appSettings>

<add key="ConnectionTimeout" value="15" />

</appSettings>
```


## <a name="see-also"></a>См. также:

[Загрузка помощник по миграции данных](https://www.microsoft.com/download/details.aspx?id=53595)
