---
title: "Рабочий процесс ETL | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- samples
ms.custom: 
ms.date: 06/15/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 679e58fe-b062-4934-a94c-9bb916b0bcb0
caps.latest.revision: 5
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 85898dfc3a12ee195910bf965f0099b35f95b239
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="wideworldimportersdw-etl-workflow"></a>Рабочий процесс WideWorldImportersDW ETL
ETL-пакета WWI_Integration используется для переноса данных из базы данных WideWorldImporters WideWorldImportersDW базы данных при изменении данных. Пакет периодически запускается (чаще всего ежедневно).

## <a name="overview"></a>Обзор

Разработки пакета используется SQL Server Integration Services (SSIS) для управления операциями массового T-SQL (а не как отдельные преобразования в рамках служб SSIS) для обеспечения высокой производительности.

Измерения загружаются во-первых, а затем по таблицам фактов. Пакет можно повторно запустить в любое время после сбоя.

Рабочий процесс выглядит следующим образом:

 ![Рабочий процесс WideWorldImporters ETL](../../sample/world-wide-importers/media/wideworldimporters-etl-workflow.png)

Он начинается с задача «выражение», которая работает соответствующее время прекращения. Время указано текущее время меньше через несколько минут. (Это более надежными, чем запрашивает данные непосредственно на текущий момент времени). Затем он усекает любой миллисекунд с момента.

Основной обработки начинается при заполнении таблицы измерения даты. Это гарантирует, что заполнены все даты за текущий год в таблице.

После этого ряда задач потока данных загружает каждого измерения, а затем каждый из фактов.

## <a name="prerequisites"></a>Предварительные требования

- SQL Server 2016 (или более поздней версии) с базами данных WideWorldImporters и WideWorldImportersDW. Это могут быть на одном или разных экземплярах SQL Server.
- SQL Server Management Studio (SSMS)
- SQL Server 2016 Integration Services (SSIS).
  - Убедитесь, что вы создали каталог SSIS. Если это не так, щелкните правой кнопкой мыши **службы Integration Services** в обозревателе объектов SSMS и выберите **добавьте каталог**. Имеют значения по умолчанию. Он выдаст запрос на включение sqlclr и укажите пароль.


## <a name="download"></a>Загрузить

В последнем выпуске образца:

[Wide world-importers выпуска](http://go.microsoft.com/fwlink/?LinkID=800630)

Загрузите файл пакета служб SSIS **ежедневно ETL.ispac**.

Исходный код для повторного создания образца базы данных доступен из следующего расположения.

[Wide world importers —](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-integration-etl)

## <a name="install"></a>Установить

1. Развертывание пакета служб SSIS.
   - Откройте пакет «Ежедневный ETL.ispac» из проводника Windows. Это приведет к запуску мастера развертывания служб Integration Services.
   - В разделе «Выбор источника» выполните развертывание проекта по умолчанию с путем, указывающим на пакет «Ежедневный ETL.ispac».
   - В разделе «Выбор назначения» введите имя сервера, на котором размещен каталог служб SSIS.
   - Выберите путь в каталоге служб SSIS, например в новую папку «WideWorldImporters».
   - Завершите мастер, нажав на развертывание.

2. Создайте задание агента SQL Server для процесса ETL.
   - В среде SSMS щелкните правой кнопкой мыши «агент SQL Server» и выберите Создать -> задания.
   - Выберите имя, например «WideWorldImporters ETL».
   - Добавьте шаг задания типа «Пакет служб интеграции SQL Server».
   - Выберите сервер в каталоге служб SSIS и выберите пакет «Ежедневный ETL».
   - Конфигурация -> диспетчеры соединений обеспечить правильность настройки подключения к исходной и целевой. По умолчанию используется для подключения к локальному экземпляру.
   - Нажмите кнопку ОК, чтобы создать задание.

3. Выполнение или планирование задания.

