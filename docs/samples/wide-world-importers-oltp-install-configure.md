---
title: Установка и настройка образца базы данных WideWorldImporters - SQL | Документация Майкрософт
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6fc303892fdefda350a2bb6513a71226264e50fe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067675"
---
# <a name="installation-and-configuration"></a>Установка и настройка
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Инструкции по установке и конфигурации для базы данных Wide World Importers OLTP.

## <a name="prerequisites"></a>предварительные требования

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (или более поздней версии) или [базы данных SQL Azure](https://azure.microsoft.com/services/sql-database/). Для полной версии примера используйте SQL Server Evaluation, Developer или Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Для получения наилучших результатов используйте от июня 2016 г. или более поздней версии.

## <a name="download"></a>Загрузить

В последнем выпуске примера:

[Wide world-importers выпуска](https://go.microsoft.com/fwlink/?LinkID=800630)

Скачайте образец WideWorldImporters базы данных резервного копирования или bacpac-файл, соответствующий выпуска SQL Server или базы данных SQL Azure.

Исходный код для повторного создания образца базы данных доступен из следующего расположения. Обратите внимание на то, что повторное создание примера приведет к небольшие различия в данных, так как в создания данных случайного фактора:

[Wide world importers —](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-database-scripts)

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
5. В разделе **параметры базы данных** измените имя базы данных на *WideWorldImporters* и выбрать целевой выпуск и цель службы для использования.
6. Нажмите кнопку **Далее** и **Готово** для запуска развертывания. Он будет несколько минут на P1. Если снижением цены требуемого уровня, мы рекомендуем импортировать в новую базу данных P1, а затем измените ценовую категорию на нужном уровне.

## <a name="configuration"></a>Конфигурация

### <a name="full-text-indexing"></a>Полнотекстовое индексирование

Образец базы данных можно воспользоваться полнотекстового индексирования. Тем не менее этот компонент не устанавливается по умолчанию с помощью SQL Server – необходимо выбрать его во время установки SQL Server (он включен по умолчанию в базе данных SQL Azure). Таким образом, после установки шаг является обязательным.

1. В SQL Server Management Studio подключитесь к базе данных WideWorldImporters и открыть новое окно запроса.
2. Выполните следующую команду T-SQL, чтобы включить использование полнотекстового индексирования в базе данных:  `EXECUTE Application.Configuration_ApplyFullTextIndexing`


### <a name="sql-server-audit"></a>подсистема аудита SQL Server

Применимо для следующих объектов: SQL Server

Включение аудита в SQL Server требуется сервер конфигурации. Чтобы Подсистема аудита SQL Server для образца WideWorldImporters, выполните следующую инструкцию в базе данных:

    EXECUTE [Application].[Configuration_ApplyAuditing]

В базе данных SQL Azure, аудита настраивается с помощью [портала Azure](https://portal.azure.com/).

### <a name="row-level-security"></a>Безопасность на уровне строк

Применимо для следующих объектов: База данных SQL Azure

Безопасность на уровне строк не включена по умолчанию в bacpac-файл для загрузки из WideWorldImporters. Чтобы включить безопасность на уровне строк в базе данных, выполните следующую хранимую процедуру:

    EXECUTE [Application].[Configuration_ApplyRowLevelSecurity]

