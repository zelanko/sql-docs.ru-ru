---
title: WideWorldImportersDW - рабочего процесса ETL | Документы Microsoft
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 36638c4cc2bda58ac277822d5c4a4ce5421ab8b4
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34467690"
---
# <a name="wideworldimportersdw-etl-workflow"></a>Рабочий процесс WideWorldImportersDW ETL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Используйте *WWI_Integration* ETL-пакета для переноса данных из базы данных WideWorldImporters WideWorldImportersDW базы данных при изменениях данных. Пакет выполняется периодически (обычно ежедневно).

Пакет обеспечивает высокую производительность с помощью служб интеграции SQL Server для управления операциями массового T-SQL (а не отдельных преобразования в службах Integration Services).

Измерения загружаются сначала, а затем загружаются таблицы фактов. Пакет можно перезапустить любое время после сбоя.

Рабочий процесс выглядит следующим образом:

 ![Рабочий процесс WideWorldImporters ETL](media/wide-world-importers/wideworldimporters-etl-workflow.png)

Рабочий процесс запускается с помощью задачи «выражение», определяет соответствующее время прекращения. Время прекращения — это текущее время минус через несколько минут. (Этот подход является более надежными, чем запрашивает данные непосредственно на текущий момент времени.) С момента усекаются любые миллисекунд.

Основной обработки начинается при заполнении таблицы измерения даты. Обработка гарантирует, что заполнены все даты за текущий год в таблице.

Затем последовательность задач потока данных загружает каждого измерения. Затем они загружаются каждый из фактов.

## <a name="prerequisites"></a>предварительные требования

- SQL Server 2016 (или более поздней версии), с WideWorldImporters и WideWorldImportersDW базы данных (в том же или в разных экземплярах SQL Server)
- Среда SQL Server Management Studio
- Службы SQL Server 2016 Integration Services
  - Убедитесь, что создании каталога служб Integration Services. Создание каталога служб Integration Services, в обозревателе объектов SQL Server Management Studio, щелкните правой кнопкой мыши **службы Integration Services**, а затем выберите **добавьте каталог**. Оставьте значения по умолчанию. Будет предложено включить SQLCLR и укажите пароль.


## <a name="download"></a>Загрузить

В последнем выпуске образца см [wide world-importers освобождения](http://go.microsoft.com/fwlink/?LinkID=800630). Загрузить *ежедневно ETL.ispac* файл пакета служб Integration Services.

Исходный код для повторного создания образца базы данных см. в разделе [wide world-importers](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-integration-etl).

## <a name="install"></a>Установка

1. Развертывание пакета служб Integration Services:
   1. В проводнике Windows откройте *ежедневно ETL.ispac* пакета. Запустится мастер развертывания SQL Server Integration Services.
   2. В разделе **Выбор источника**, имеют значения по умолчанию для развертывания проекта с путем, указывающим на *ежедневно ETL.ispac* пакета.
   3. В разделе **Выбор назначения**, введите имя сервера, на котором размещен каталог служб Integration Services.
   4. Например, выберите путь в каталоге служб Integration Services в новую папку с именем *WideWorldImporters*.
   5. Выберите **развернуть** и завершить работу мастера.

2. Создание задания агента SQL Server для процесса ETL:
   1. В среде Management Studio щелкните правой кнопкой мыши **агента SQL Server**, а затем выберите **New** > **задания**.
   2. Введите имя, например, *WideWorldImporters ETL*.
   3. Добавить **шаг задания** типа **пакет SQL Server Integration Services**.
   4. Выберите сервер, который имеет каталог служб Integration Services, а затем выберите *ежедневно ETL* пакета.
   5. В разделе **конфигурации** > **диспетчеры соединений**, убедитесь в правильности настройки подключения к исходной и целевой. По умолчанию используется для подключения к локальному экземпляру.
   6. Выберите **ОК** для создания задания.

3. Выполнение или планирование задания.
