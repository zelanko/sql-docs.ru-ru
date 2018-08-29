---
title: Образец базы данных WideWorldImporters OLAP - Установка и настройка - SQL | Документация Майкрософт
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 08/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: b4c272ce3f4a3e534b688301542071c5e06cef89
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43080973"
---
# <a name="wideworldimportersdw-installation-and-configuration"></a>WideWorldImportersDW Установка и настройка
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Инструкции по установке и конфигурации для базы данных WideWorldImportersDW.

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (или более поздней версии) или [базы данных SQL Azure](https://azure.microsoft.com/services/sql-database/). Чтобы использовать полную версию примера, используйте SQL Server Evaluation, Developer или Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Для получения наилучших результатов используйте от июня 2016 г. или более поздней версии.

## <a name="download"></a>Загрузить

В последнем выпуске примера:

[Wide world-importers выпуска](http://go.microsoft.com/fwlink/?LinkID=800630)

Скачайте образец WideWorldImportersDW базы данных резервного копирования или bacpac-файл, соответствующий выпуска SQL Server или базы данных SQL Azure.

Исходный код для повторного создания образца базы данных доступен из следующего расположения. Обратите внимание на то, что заполнение данных основана на ETL из базы данных OLTP (WideWorldImporters):

[wide-world-importers-source](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-dw-database-scripts)

## <a name="install"></a>Установка


### <a name="sql-server"></a>SQL Server

Восстановление резервной копии к экземпляру SQL Server, можно использовать среду Management Studio.

1. Откройте SQL Server Management Studio и подключитесь к целевому экземпляру SQL Server.
2. Щелкните правой кнопкой мыши **баз данных** узел и выберите **Restore Database**.
3. Выберите **устройства** и нажмите кнопку **...**
4. В диалоговом окне **Выбор устройства резервного копирования**, нажмите кнопку **добавить**, перейдите к резервной копии базы данных в файловой системе сервера и выберите резервную копию. Нажмите кнопку **ОК**.
5. При необходимости изменить целевое расположение для данных и файлов журналов в **файлы** области. Обратите внимание на то, что это лучший способ размещения данных и файлы журнала на разных дисках.
6. Нажмите кнопку **ОК**. Это инициирует восстановление базы данных. После ее завершения вы получите базы данных WideWorldImporters, установленных на экземпляре SQL Server.

### <a name="azure-sql-database"></a>База данных SQL Azure

Чтобы импортировать bacpac в новую базу данных SQL, можно использовать среду Management Studio.

1. (необязательно) Если у вас еще нет SQL Server в Azure, перейдите к [портала Azure](https://portal.azure.com/) и создать новую базу данных SQL. В создание базы данных, создании сервера. Следует обратить внимание сервера.
   - См. в разделе [учебником](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) Создание базы данных в минутах
2. Откройте SQL Server Management Studio и подключитесь к серверу в Azure.
3. Щелкните правой кнопкой мыши **баз данных** узел и выберите **Импорт приложения уровня данных**.
4. В **Импорт параметров** выберите **импорт с локального диска** и выберите bacpac-файл образца базы данных из файловой системы.
5. В разделе **параметры базы данных** измените имя базы данных на *WideWorldImportersDW* и выбрать целевой выпуск и цель службы для использования.
6. Нажмите кнопку **Далее** и **Готово** для запуска развертывания. Может занять несколько минут. При указании цели обслуживания ниже, чем S2 может занять больше времени.

## <a name="configuration"></a>Конфигурация

[Применяется к SQL Server 2016 (и более поздние версии) Developer, Evaluation и Enterprise Edition]

Образец базы данных можно воспользоваться PolyBase файлы запросов в хранилище BLOB-объектов Azure или Hadoop. Тем не менее этот компонент не устанавливается по умолчанию с помощью SQL Server – необходимо выбрать его во время установки SQL Server. Таким образом, после установки шаг является обязательным.

1. В SQL Server Management Studio подключитесь к базе данных WideWorldImportersDW и открыть новое окно запроса.
2. Выполните следующую команду T-SQL, чтобы разрешить использование PolyBase в базе данных:

   ВЫПОЛНИТЕ [приложение]. [Configuration_ApplyPolyBase]
