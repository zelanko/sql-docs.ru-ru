---
title: WideWorldImportersDW - рабочий процесс ETL | Документация Майкрософт
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d17cc2ccc46733c857f884f78a1b0c9b3f980586
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51674113"
---
# <a name="wideworldimportersdw-etl-workflow"></a>Рабочий процесс WideWorldImportersDW ETL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Используйте *WWI_Integration* ETL-пакета для переноса данных из базы данных WideWorldImporters к базе данных WideWorldImportersDW при изменении данных. Пакет выполняется периодически (обычно ежедневно).

Пакет гарантирует высокую производительность с помощью SQL Server Integration Services для оркестрации операций массового T-SQL (вместо отдельных преобразования в службах Integration Services).

Сначала загружаются измерений, а затем загружаются таблицы фактов. Вы можете повторно запустить пакет любое время после сбоя.

Рабочий процесс выглядит следующим образом:

 ![Рабочий процесс WideWorldImporters ETL](media/wide-world-importers/wideworldimporters-etl-workflow.png)

Рабочий процесс запускается с помощью задачи «выражение», который определяет соответствующее время прекращения. Пороговое значение времени — это текущее время минус несколько минут. (Этот подход является более надежным, чем получение данных непосредственно на текущий момент времени.) Любой миллисекунд усекаются от времени.

Основная обработка начинается с заполнения таблицы измерения даты. Обработка гарантирует, что заполнены все даты за текущий год в таблице.

Затем последовательность задач потока данных загружает каждого измерения. После этого они загружаются каждый факт.

## <a name="prerequisites"></a>предварительные требования

- SQL Server 2016 (или более поздней версии), с помощью WideWorldImporters и WideWorldImportersDW базы данных (в том же или в разных экземплярах SQL Server)
- SQL Server Management Studio
- Службы SQL Server 2016 Integration Services
  - Обязательно создайте в каталоге служб Integration Services. Чтобы создать каталог служб Integration Services в обозревателе объектов SQL Server Management Studio, щелкните правой кнопкой мыши **служб Integration Services**, а затем выберите **добавить каталог**. Оставьте значения по умолчанию. Вам предложено включить SQLCLR и укажите пароль.


## <a name="download"></a>Загрузить

Последний выпуск примера, см. в разделе [wide world-importers выпуска](https://go.microsoft.com/fwlink/?LinkID=800630). Скачайте *ежедневного ETL.ispac* файл пакета служб Integration Services.

Исходный код для повторного создания образца базы данных, см. в разделе [wide world importers —](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-integration-etl).

## <a name="install"></a>Установка

1. Развертывание пакета служб Integration Services:
   1. В проводнике Windows откройте *ежедневного ETL.ispac* пакета. Запустится мастер развертывания SQL Server Integration Services.
   2. В разделе **Выбор источника**, выполните значения по умолчанию для развертывания проекта, с помощью пути к *ежедневного ETL.ispac* пакета.
   3. В разделе **Выбор места расположения**, введите имя сервера, на котором размещен каталог служб Integration Services.
   4. Выберите путь в каталоге служб Integration Services, например, в новую папку с именем *WideWorldImporters*.
   5. Выберите **развернуть** для завершения работы мастера.

2. Создание задания агента SQL Server для процесса ETL:
   1. В среде Management Studio щелкните правой кнопкой мыши **агента SQL Server**, а затем выберите **New** > **задания**.
   2. Введите имя, например, *WideWorldImporters ETL*.
   3. Добавить **шага задания** типа **пакет SQL Server Integration Services**.
   4. Выберите сервер, который имеет каталог служб Integration Services, а затем выберите *ежедневного ETL* пакета.
   5. В разделе **конфигурации** > **диспетчеры соединений**, убедитесь в правильности настройки подключения к исходной и целевой среды. По умолчанию используется для подключения к локальному экземпляру.
   6. Выберите **ОК** для создания задания.

3. Выполнение или планирование задания.
