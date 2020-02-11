---
title: Установка и Настройка образца базы данных WideWorldImporters
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: e1683adfa20851d279e8b8e18a3c767db9e5810d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74056274"
---
# <a name="installation-and-configuration"></a>Установка и настройка
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Инструкции по установке и настройке базы данных OLTP для широкого мира.

## <a name="prerequisites"></a>Предварительные требования

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (или более поздней версии) или [базы данных SQL Azure](https://azure.microsoft.com/services/sql-database/). Для полной версии примера используйте SQL Server Evaluation, Developer или Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Для получения наилучших результатов используйте выпуск Июнь 2016 или более поздней версии.

## <a name="download"></a>Скачивание

Последний выпуск примера:

[широкие средства импорта — выпуск](https://go.microsoft.com/fwlink/?LinkID=800630)

Скачайте пример резервной копии базы данных WideWorldImporters или BACPAC, соответствующий выпуску SQL Server или базе данных SQL Azure.

Исходный код для повторного создания образца базы данных доступен по следующему адресу. Обратите внимание, что повторное создание образца приведет к незначительным различиям в данных, так как в создании данных существует случайный фактор.

[широкие средства импорта](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-database-scripts)

## <a name="install"></a>Установка


### <a name="sql-server"></a>SQL Server

Чтобы восстановить резервную копию на SQL Server экземпляр, можно использовать Management Studio.

1. Откройте SQL Server Management Studio и подключитесь к целевому экземпляру SQL Server.
2. Щелкните правой кнопкой мыши узел **базы данных** и выберите команду **восстановить базу данных**.
3. Выберите **устройство** и нажмите кнопку **...**
4. В диалоговом окне **выберите устройства резервного копирования**, нажмите кнопку **Добавить**, перейдите к резервной копии базы данных в файловой системе сервера и выберите резервную копию. Нажмите кнопку **ОК**.
5. При необходимости измените целевое расположение файлов данных и журналов в области **файлы** . Обратите внимание, что рекомендуется размещать файлы данных и журналов на разных дисках.
6. Нажмите кнопку **ОК**. Это приведет к запуску восстановления базы данных. После завершения работы на экземпляре SQL Server будет установлена база данных WideWorldImporters.

### <a name="azure-sql-database"></a>База данных SQL Azure

Чтобы импортировать BACPAC-файл в новую базу данных SQL, можно использовать Management Studio.

1. используемых Если у вас еще нет SQL Server в Azure, перейдите к [портал Azure](https://portal.azure.com/) и создайте новую базу данных SQL. В процессе создания базы данных будет создан сервер. Запишите сервер.
   - Ознакомьтесь с [руководством](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) по созданию базы данных за считаные минуты
2. Откройте SQL Server Management Studio и подключитесь к серверу в Azure.
3. Щелкните правой кнопкой мыши узел **базы данных** и выберите пункт **Импорт приложения уровня данных**.
4. В **параметрах импорта** выберите **Импорт с локального диска** и выберите BACPAC образца базы данных из файловой системы.
5. В разделе **Параметры базы данных** измените имя базы данных на *WideWorldImporters* и выберите целевой выпуск и цель службы для использования.
6. Нажмите кнопку **Далее** и **Готово** , чтобы запустить развертывание. Выполнение через P1 займет несколько минут. Если требуется более низкая Ценовая категория, рекомендуется импортировать в новую базу данных P1, а затем изменить ценовую категорию на нужный уровень.

## <a name="configuration"></a>Конфигурация

### <a name="full-text-indexing"></a>Полнотекстовое индексирование

Образец базы данных может использовать полнотекстовое индексирование. Однако эта функция не устанавливается по умолчанию с SQL Server — необходимо выбрать ее во время установки SQL Server (она включена по умолчанию в базе данных SQL Azure). Поэтому необходимо выполнить действие после установки.

1. В SQL Server Management Studio подключитесь к базе данных WideWorldImporters и откройте новое окно запроса.
2. Выполните следующую команду T-SQL, чтобы разрешить использование полнотекстового индексирования в базе данных:`EXECUTE Application.Configuration_ApplyFullTextIndexing`


### <a name="sql-server-audit"></a>подсистема аудита SQL Server

Применяется к: SQL Server

Включение аудита в SQL Server требует настройки сервера. Чтобы включить аудит SQL Server для образца WideWorldImporters, выполните следующую инструкцию в базе данных:

    EXECUTE [Application].[Configuration_ApplyAuditing]

В базе данных SQL Azure аудит настраивается с помощью [портал Azure](https://portal.azure.com/).

### <a name="row-level-security"></a>Безопасность на уровне строк

Область применения: база данных SQL Azure

Безопасность на уровне строк не включена по умолчанию в скачивании BACPAC WideWorldImporters. Чтобы включить безопасность на уровне строк в базе данных, выполните следующую хранимую процедуру:

    EXECUTE [Application].[Configuration_ApplyRowLevelSecurity]

