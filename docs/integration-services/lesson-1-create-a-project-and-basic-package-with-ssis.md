---
title: Урок 1. Создание проекта и простого пакета с помощью служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 27af17bfd3b59d119bbe4d64dd52840c90e88a0d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68112317"
---
# <a name="lesson-1-create-a-project-and-basic-package-with-ssis"></a>Урок 1. Создание проекта и простого пакета с помощью служб SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



На этом занятии вы создадите простой пакет для извлечения, преобразования и загрузки, который будет извлекать данные из отдельного источника неструктурированных файлов, преобразовывать их с помощью двух преобразований типа "уточняющий запрос", а затем записывать преобразованные данные в копию таблицы фактов **FactCurrencyRate**, находящуюся в образце базы данных **AdventureWorksDW2012**. На этом занятии вы узнаете, как создавать пакеты, добавлять и настраивать подключения к источникам данных и назначениям, а также работать с новыми компонентами потока управления и потока данных.  
  
Перед созданием пакета необходимо ознакомиться с форматированием в источнике данных и назначении. После этого можно определить преобразования, необходимые для сопоставления источника данных с назначением.  

## <a name="prerequisites"></a>предварительные требования

Для выполнения упражнений в этом учебнике требуются средства Microsoft SQL Server Data Tools, набор примеров пакетов и образец базы данных.

* Инструкции по установке SQL Server Data Tools см. на странице [Скачать SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md).  
  
* Чтобы скачать все пакеты занятий этого учебника, выполните указанные ниже действия.

    1.  Перейдите к [учебным файлам для служб Integration Services](https://www.microsoft.com/en-us/download/details.aspx?id=56827).

    2.  Нажмите кнопку **Скачать**.

    3.  Выберите файл **Creating a Simple ETL Package.zip** и нажмите кнопку **Далее**.

    4.  Когда файл скачается, распакуйте его содержимое в локальный каталог.  

* Чтобы установить и развернуть образец базы данных **AdventureWorksDW2012**, см. страницу [Установка и настройка образца базы данных AdventureWorks — SQL](../samples/adventureworks-install-configure.md).
  
## <a name="look-at-the-source-data"></a>Обзор исходных данных
Для этого учебника исходные данные представлены в виде набора курсов валют, содержащегося в неструктурированном файле **SampleCurrencyData.txt**. Данные источника в этом файле имеют четыре столбца: средний курс валюты, ключ валюты, ключ даты и курс на конец дня.  
  
Вот пример исходных данных в файле SampleCurrencyData.txt:  
  
<pre>1.00070049USD9/3/05 0:001.001201442  
1.00020004USD9/4/05 0:001  
1.00020004USD9/5/05 0:001.001201442  
1.00020004USD9/6/05 0:001  
1.00020004USD9/7/05 0:001.00070049  
1.00070049USD9/8/05 0:000.99980004  
1.00070049USD9/9/05 0:001.001502253  
1.00070049USD9/10/05 0:000.99990001  
1.00020004USD9/11/05 0:001.001101211  
1.00020004USD9/12/05 0:000.99970009</pre>  
  
При работе с исходными данными неструктурированных файлов важно понимать, как диспетчер подключений к неструктурированным файлам интерпретирует их. Если неструктурированный файл является документом в Юникоде, диспетчер соединений с неструктурированными файлами определяет все столбцы как [DT_WSTR] с шириной, по умолчанию равной 50. Если неструктурированный файл является документом в кодировке ANSI, столбцы определяются как [DT_STR] с шириной по умолчанию, равной 50. Возможно, потребуется изменить эти настройки, чтобы оптимизировать столбцы для конкретных данных. Необходимо узнать тип данных в назначении, а затем выбрать этот тип в диспетчере подключений к неструктурированным файлам.  
  
## <a name="look-at-the-destination-data"></a>Обзор данных назначения
Назначением исходных данных является копия таблицы фактов **FactCurrencyRate** в базе данных **AdventureWorksDW**. Таблица фактов **FactCurrencyRate** имеет четыре столбца и связи с двумя таблицами измерений, как показано в следующей таблице.  
  
|Имя столбца|Тип данных|Таблица уточняющих запросов|Уточняющий столбец|  
|---------------|-------------|----------------|-----------------|  
|AverageRate|FLOAT|None|None|  
|CurrencyKey|int (FK)|DimCurrency|CurrencyKey (PK)|  
|DateKey|int (FK)|DimDate|DateKey (PK)|  
|EndOfDayRate|FLOAT|None|None|  
  
## <a name="map-the-source-data-to-the-destination"></a>Сопоставление исходных данных с назначением  
Анализ форматов данных источника и назначения показывает, что для значений **CurrencyKey** и **DateKey** требуются уточняющие запросы. Преобразования, которые выполняют эти уточняющие запросы, получают эти значения из таблиц измерений **DimCurrency** и **DimDate**.  
  
|Столбец неструктурированных файлов|Имя таблицы|Имя столбца|Тип данных|  
|--------------------|--------------|---------------|-------------|  
|0|FactCurrencyRate|AverageRate|float|  
|1|DimCurrency|CurrencyAlternateKey|nchar (3)|  
|2|DimDate|FullDateAlternateKey|Дата|  
|3|FactCurrencyRate|EndOfDayRate|FLOAT|  
  
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Создание проекта служб Integration Services](../integration-services/lesson-1-1-creating-a-new-integration-services-project.md)  
  
-   [Шаг 2. Добавление и настройка диспетчера подключений к неструктурированным файлам](../integration-services/lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [Шаг 3. Добавление и настройка диспетчера подключений OLE DB](../integration-services/lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [Шаг 4. Добавление задачи потока данных к пакету](../integration-services/lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [Шаг 5. Добавление и настройка источника "Неструктурированный файл"](../integration-services/lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [Шаг 6. Добавление и настройка преобразований "Уточняющий запрос"](../integration-services/lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [Шаг 7. Добавление и настройка назначения OLE DB](../integration-services/lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [Шаг 8. Добавление заметок и форматирование пакета занятия 1](../integration-services/lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [Шаг 9. Тестирование пакета занятия 1](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Создание проекта служб Integration Services](../integration-services/lesson-1-1-creating-a-new-integration-services-project.md)  
  
