---
title: Установка и настройка | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- samples
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dd1f09b-dcff-4627-899a-eca5162d9e5b
caps.latest.revision: 4
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: On Demand
ms.openlocfilehash: add5788063cdc5026d343061b8111cbec42e5a4d
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2018
---
# <a name="installation-and-configuration"></a>Установка и настройка
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Расширенный World Importers OLTP базы данных инструкции по установке и конфигурации.

## <a name="prerequisites"></a>предварительные требования

- [SQL Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) (или более поздней версии) или [базы данных SQL Azure](https://azure.microsoft.com/services/sql-database/). Для полной версии образца используйте SQL Server Evaluation, Developer или Enterprise Edition.
- [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md). Для получения наилучших результатов используйте выпуска июня 2016 г. или более поздней версии.

## <a name="download"></a>Загрузить

В последнем выпуске образца:

[wide-world-importers-release](http://go.microsoft.com/fwlink/?LinkID=800630)

Загрузите образец WideWorldImporters базы данных резервной копии или bacpac-файл, соответствующий выпуска SQL Server или база данных SQL Azure.

Исходный код для повторного создания образца базы данных доступен из следующего расположения. Обратите внимание, что повторное создание образца приведет небольшие различия в данных, так как нет случайного фактора поколения данных.

[wide-world-importers](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-database-scripts)

## <a name="install"></a>Установка


### <a name="sql-server"></a>SQL Server

Восстановление резервной копии к экземпляру SQL Server, можно использовать среду Management Studio.

1. Откройте SQL Server Management Studio и подключитесь к целевому экземпляру SQL Server.
2. Щелкните правой кнопкой мыши **баз данных** , а затем установите **восстановление базы данных**.
3. Выберите **устройства** и нажмите кнопку **...**
4. В диалоговом окне **Выбор устройства резервного копирования**, нажмите кнопку **добавить**, перейдите к резервной копии базы данных в файловой системе сервера и выберите резервную копию. Нажмите кнопку **ОК**.
5. При необходимости изменить целевое расположение для данных и файлы журналов, в **файлы** области. Обратите внимание, что это лучший способ размещения данных и файлы журнала на разных дисках.
6. Нажмите кнопку **ОК**. Это инициирует восстановление базы данных. После завершения работы, вы получите базы данных WideWorldImporters, установленных на экземпляре SQL Server.

### <a name="azure-sql-database"></a>Azure SQL Database

Чтобы импортировать bacpac в новую базу данных SQL, можно использовать среду Management Studio.

1. (необязательно) Если вы еще не SQL Server в Azure, перейдите в папку [портал Azure](https://portal.azure.com/) и создать новую базу данных SQL. В процессе для создания базы данных, создании сервера. Запишите сервера.
   - В разделе [этого учебника](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) Создание базы данных в минутах
2. Откройте SQL Server Management Studio и подключитесь к серверу в Azure.
3. Щелкните правой кнопкой мыши **баз данных** , а затем установите **Импорт приложения уровня данных**.
4. В **Импорт параметров** выберите **импорт с локального диска** и выбора bacpac-файл образца базы данных из файловой системы.
5. В разделе **параметры базы данных** изменить имя базы данных для *WideWorldImporters* и выберите цель выпуска и службы целевой для использования.
6. Нажмите кнопку **Далее** и **Готово** для запуска развертывания. Он будет несколько минут на P1. Если нижней цены требуемого уровня, рекомендуется импортировать в новую базу данных P1, а затем измените ценовую категорию требуемый уровень.

## <a name="configuration"></a>Конфигурация

### <a name="full-text-indexing"></a>Полнотекстовое индексирование

Образец базы данных могут пользоваться полнотекстового индексирования. Тем не менее этот компонент не устанавливается по умолчанию вместе с SQL Server: необходимо выбрать его во время установки SQL Server (включено по умолчанию в базе данных SQL Azure). Таким образом, после установки шаг является обязательным.

1. В SQL Server Management Studio подключитесь к базе данных WideWorldImporters и открыть новое окно запроса.
2. Выполните следующую команду T-SQL, чтобы включить использование полнотекстового индексирования в базе данных:  `EXECUTE Application.Configuration_ApplyFullTextIndexing`


### <a name="sql-server-audit"></a>подсистема аудита SQL Server

Применяется к: SQL Server

Включение аудита в SQL Server требуется настройка сервера. Для включения аудита SQL Server для образца WideWorldImporters, выполните следующую инструкцию в базе данных:

    EXECUTE [Application].[Configuration_ApplyAuditing]

В базе данных SQL Azure, аудита настраивается с помощью [портал Azure](https://portal.azure.com/).

### <a name="row-level-security"></a>Безопасность на уровне строк

Применяется к: база данных Azure SQL

Безопасность на уровне строк не включена по умолчанию для скачивания bacpac WideWorldImporters. Чтобы включить безопасность на уровне строк в базе данных, выполните следующую хранимую процедуру:

    EXECUTE [Application].[Configuration_ApplyAuditing]

