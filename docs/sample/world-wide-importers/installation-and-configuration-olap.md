---
title: "Установка и настройка | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- samples
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d07ffb9a-ac4f-4295-9aeb-ecfb97600134
caps.latest.revision: 3
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: f40894ea8ee3d7b998a8a45170e9833f2e6c763f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="wideworldimportersdw-installation-and-configuration"></a>WideWorldImportersDW Установка и настройка
Инструкции по установке и конфигурации для WideWorldImportersDW базы данных.

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (или более поздней версии) или [базы данных SQL Azure](https://azure.microsoft.com/services/sql-database/). Чтобы использовать полную версию примера, используйте SQL Server Evaluation, Developer или Enterprise Edition.
- [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md). Для получения наилучших результатов используйте выпуска июня 2016 г. или более поздней версии.

## <a name="download"></a>Загрузить

В последнем выпуске образца:

[Wide world-importers выпуска](http://go.microsoft.com/fwlink/?LinkID=800630)

Загрузите образец WideWorldImportersDW базы данных резервной копии или bacpac-файл, соответствующий выпуска SQL Server или база данных SQL Azure.

Исходный код для повторного создания образца базы данных доступен из следующего расположения. Обратите внимание, что заполнение данных основана на ETL из базы данных OLTP (WideWorldImporters).

[Wide world-importers источника](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-dw-database-scripts)

## <a name="install"></a>Установить


### <a name="sql-server"></a>SQL Server

Восстановление резервной копии к экземпляру SQL Server, можно использовать среду Management Studio.

1. Откройте SQL Server Management Studio и подключитесь к целевому экземпляру SQL Server.
2. Щелкните правой кнопкой мыши **баз данных** , а затем установите **восстановление базы данных**.
3. Выберите **устройства** и нажмите кнопку **...**
4. В диалоговом окне **Выбор устройства резервного копирования**, нажмите кнопку **добавить**, перейдите к резервной копии базы данных в файловой системе сервера и выберите резервную копию. Нажмите кнопку **ОК**.
5. При необходимости изменить целевое расположение для данных и файлы журналов, в **файлы** области. Обратите внимание, что это лучший способ размещения данных и файлы журнала на разных дисках.
6. Нажмите кнопку **ОК**. Это инициирует восстановление базы данных. После завершения работы, вы получите базы данных WideWorldImporters, установленных на экземпляре SQL Server.

### <a name="azure-sql-database"></a>База данных SQL Azure

Чтобы импортировать bacpac в новую базу данных SQL, можно использовать среду Management Studio.

1. (необязательно) Если вы еще не SQL Server в Azure, перейдите в папку [портал Azure](https://portal.azure.com/) и создать новую базу данных SQL. В процессе для создания базы данных, создании сервера. Запишите сервера.
   - В разделе [этого учебника](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) Создание базы данных в минутах
2. Откройте SQL Server Management Studio и подключитесь к серверу в Azure.
3. Щелкните правой кнопкой мыши **баз данных** , а затем установите **Импорт приложения уровня данных**.
4. В **Импорт параметров** выберите **импорт с локального диска** и выбора bacpac-файл образца базы данных из файловой системы.
5. В разделе **параметры базы данных** изменить имя базы данных для *WideWorldImportersDW* и выберите цель выпуска и службы целевой для использования.
6. Нажмите кнопку **Далее** и **Готово** для запуска развертывания. Займет несколько минут. При указании цели обслуживания ниже, чем S2 может занять больше времени.

## <a name="configuration"></a>Конфигурация

[Применяется к SQL Server 2016 (и более поздние версии) Developer, Evaluation и Enterprise Edition]

Образец базы данных могут пользоваться PolyBase файлы запросов в хранилище больших двоичных объектов Azure или Hadoop. Тем не менее этот компонент не устанавливается по умолчанию вместе с SQL Server: необходимо выбрать его во время установки SQL Server. Таким образом, после установки шаг является обязательным.

1. В SQL Server Management Studio подключитесь к базе данных WideWorldImportersDW и открыть новое окно запроса.
2. Выполните следующие команды T-SQL, чтобы использовать PolyBase в базе данных:

   ВЫПОЛНИТЕ [приложение]. [Configuration_ApplyPolyBase]

