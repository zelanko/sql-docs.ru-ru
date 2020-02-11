---
title: WideWorldImportersDW — рабочий процесс ETL | Документация Майкрософт
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f33d36cccbbea6f37139410f9d3d6e03f740ee96
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68067621"
---
# <a name="wideworldimportersdw-etl-workflow"></a>Рабочий процесс ETL WideWorldImportersDW
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Используйте *WWI_Integration* пакет ETL для переноса данных из базы данных WideWorldImporters в базу данных WideWorldImportersDW при изменении данных. Пакет выполняется периодически (обычно ежедневно).

Пакет обеспечивает высокую производительность, используя SQL Server Integration Services для управления массовыми операциями T-SQL (вместо отдельных преобразований в Integration Services).

Сначала загружаются измерения, а затем загружаются таблицы фактов. Вы можете повторно запустить пакет в любое время после сбоя.

Рабочий процесс выглядит следующим образом:

 ![Рабочий процесс ETL WideWorldImporters](media/wide-world-importers/wideworldimporters-etl-workflow.png)

Рабочий процесс начинается с задачи Expression, которая определяет соответствующее время отсечения. Время отсечки равно текущему времени минус несколько минут. (Этот подход является более надежным, чем запрос данных непосредственно на текущее время.) Все миллисекунды усекаются с момента времени.

Основная обработка начинается с заполнения таблицы измерения Date. Обработка гарантирует заполнение всех дат текущего года в таблице.

Затем ряд задач потока данных загружает каждое измерение. Затем они загружают каждый факт.

## <a name="prerequisites"></a>Предварительные требования

- SQL Server 2016 (или более поздней версии) с базами данных WideWorldImporters и WideWorldImportersDW (в том же или в разных экземплярах SQL Server)
- SQL Server Management Studio
- Службы SQL Server 2016 Integration Services
  - Убедитесь, что создан каталог Integration Services. Чтобы создать каталог Integration Services, в SQL Server Management Studio обозревателе объектов щелкните правой кнопкой мыши **Integration Services**, а затем выберите **Добавить каталог**. Оставьте параметры по умолчанию. Вам будет предложено включить SQLCLR и указать пароль.


## <a name="download"></a>Скачивание

Последний выпуск примера см. в разделе широкие средства [импорта данных — выпуск](https://go.microsoft.com/fwlink/?LinkID=800630). Скачайте файл пакета *ETL. ISPAC ежедневно* Integration Services.

Сведения о повторном создании образца базы данных в исходном коде см. в разделе [широкие мировые средства импорта](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-integration-etl).

## <a name="install"></a>Установка

1. Развертывание пакета Integration Services:
   1. В проводнике Windows откройте ежедневный пакет *ETL. ISPAC* . Запустится мастер развертывания SQL Server Integration Services.
   2. В разделе **Выбор источника**выполните значения по умолчанию для развертывания проекта, указав путь к *ежедневному пакету ETL. ISPAC* .
   3. В разделе **Выбор назначения**введите имя сервера, на котором размещен каталог Integration Services.
   4. Выберите путь в каталоге Integration Services, например, в новой папке с именем *WideWorldImporters*.
   5. Нажмите кнопку **развернуть** , чтобы завершить работу мастера.

2. Создайте агент SQL Server задание для процесса ETL:
   1. В Management Studio щелкните правой кнопкой мыши **Агент SQL Server**и выберите **создать** > **Задание**.
   2. Введите имя, например *WIDEWORLDIMPORTERS ETL*.
   3. Добавьте **шаг задания** типа **SQL Server Integration Services пакета**.
   4. Выберите сервер, на котором находится каталог Integration Services, а затем выберите *ежедневный пакет ETL* .
   5. В разделе**Диспетчеры соединений** **конфигурации** > убедитесь, что подключения к источнику и целевому объекту настроены правильно. По умолчанию устанавливается соединение с локальным экземпляром.
   6. Нажмите кнопку **ОК** , чтобы создать задание.

3. Выполните или Запланируйте задание.
