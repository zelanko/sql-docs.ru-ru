---
title: Установка & Настройка образца базы данных хранилища WideWorldImporters
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.custom: seo-lt-2019
ms.openlocfilehash: d8768fec2f96c725a9ba4bbf91996e95de4c800a
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056304"
---
# <a name="wideworldimportersdw-installation-and-configuration"></a>Установка и настройка WideWorldImportersDW
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Инструкции по установке и настройке для базы данных WideWorldImportersDW.

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (или более поздней версии) или [базы данных SQL Azure](https://azure.microsoft.com/services/sql-database/). Чтобы использовать полную версию образца, используйте SQL Server Evaluation, Developer или Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Для получения наилучших результатов используйте выпуск Июнь 2016 или более поздней версии.

## <a name="download"></a>Загрузить

Последний выпуск примера:

[широкие средства импорта — выпуск](https://go.microsoft.com/fwlink/?LinkID=800630)

Скачайте пример резервной копии базы данных WideWorldImportersDW или BACPAC, соответствующий выпуску SQL Server или базе данных SQL Azure.

Исходный код для повторного создания образца базы данных доступен по следующему адресу. Обратите внимание, что заполнение данных основано на ETL из базы данных OLTP (WideWorldImporters):

[wide-world-importers-source](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-dw-database-scripts)

## <a name="install"></a>Установить


### <a name="sql-server"></a>SQL Server

Чтобы восстановить резервную копию на SQL Server экземпляр, можно использовать Management Studio.

1. Откройте SQL Server Management Studio и подключитесь к целевому экземпляру SQL Server.
2. Щелкните правой кнопкой мыши узел **базы данных** и выберите команду **восстановить базу данных**.
3. Выберите **устройство** и нажмите кнопку **...**
4. В диалоговом окне **выберите устройства резервного копирования**, нажмите кнопку **Добавить**, перейдите к резервной копии базы данных в файловой системе сервера и выберите резервную копию. Нажмите кнопку **ОК**.
5. При необходимости измените целевое расположение файлов данных и журналов в области **файлы** . Обратите внимание, что рекомендуется размещать файлы данных и журналов на разных дисках.
6. Нажмите кнопку **ОК**. Это приведет к запуску восстановления базы данных. После завершения работы на экземпляре SQL Server будет установлена база данных WideWorldImporters.

### <a name="azure-sql-database"></a>Azure SQL Database

Чтобы импортировать BACPAC-файл в новую базу данных SQL, можно использовать Management Studio.

1. используемых Если у вас еще нет SQL Server в Azure, перейдите к [портал Azure](https://portal.azure.com/) и создайте новую базу данных SQL. В процессе создания базы данных будет создан сервер. Запишите сервер.
   - Ознакомьтесь с [руководством](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) по созданию базы данных за считаные минуты
2. Откройте SQL Server Management Studio и подключитесь к серверу в Azure.
3. Щелкните правой кнопкой мыши узел **базы данных** и выберите пункт **Импорт приложения уровня данных**.
4. В **параметрах импорта** выберите **Импорт с локального диска** и выберите BACPAC образца базы данных из файловой системы.
5. В разделе **Параметры базы данных** измените имя базы данных на *WideWorldImportersDW* и выберите целевой выпуск и цель службы для использования.
6. Нажмите кнопку **Далее** и **Готово** , чтобы запустить развертывание. Выполнение займет несколько минут. При указании цели обслуживания ниже S2 может потребоваться больше времени.

## <a name="configuration"></a>Конфигурация

[Относится к SQL Server 2016 (и более поздней версии) для разработчиков, оценки и выпуска Enterprise Edition]

Образец базы данных может использовать Polybase для выполнения запросов к файлам в Hadoop или хранилище BLOB-объектов Azure. Однако этот компонент не устанавливается по умолчанию SQL Server — его необходимо выбрать во время установки SQL Server. Поэтому необходимо выполнить действие после установки.

1. В SQL Server Management Studio подключитесь к базе данных WideWorldImportersDW и откройте новое окно запроса.
2. Выполните следующую команду T-SQL, чтобы включить использование Polybase в базе данных:

   Выполните [приложение]. [Configuration_ApplyPolyBase]
