---
title: Занятие 1. Создание проекта и основного пакета с помощью служб SSIS | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a4431e593a74c7f6a656f78cd70abfd19c813bdd
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51642081"
---
# <a name="lesson-1-create-a-project-and-basic-package-with-ssis"></a>Занятие 1. Создание проекта и основного пакета с помощью служб SSIS

В этом занятии вы создадите простой пакет для извлечения, преобразования и загрузки, который будет извлекать данные из отдельного источника неструктурированных файлов, преобразовывать полученные данные с помощью двух компонентов преобразования поиска, а затем записывать эти данные в копию таблицы фактов **FactCurrencyRate**, находящуюся в базе данных **AdventureWorksDW2012**. На этом занятии предстоит узнать, как создавать новые пакеты, добавлять и настраивать соединения с источниками данных и назначениями, а также работать с новыми компонентами потока управления и потока данных.  
  
> [!IMPORTANT]  
> Для выполнения упражнений этого учебника потребуется образец базы данных **AdventureWorksDW2012** . Дополнительные сведения об установке и развертывании **AdventureWorksDW2012**, в разделе [Образцы продуктов служб Reporting Services на сайте CodePlex](https://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="understanding-the-package-requirements"></a>Основные сведения о требованиях пакета  
Для выполнения упражнений этого учебника требуется Microsoft SQL Server Data Tools.  
  
Дополнительные сведения об установке SQL Server Data Tools см. в разделе [Скачать SQL Server Data Tools](https://msdn.microsoft.com/data/hh297027).  
  
Перед созданием пакета необходимо знать о форматировании в источнике данных и в назначении. Если эти форматы данных известны, можно определить преобразования, необходимые для сопоставления формата данных источника формату назначения.  
  
### <a name="looking-at-the-source"></a>Анализ источника  
Для этого учебника данные источника представлены в виде набора курсов валют, содержащегося в неструктурированном файле SampleCurrencyData.txt. Данные источника в этом файле имеют четыре столбца: средний курс валюты, ключ валюты, ключ даты и курс на конец дня.  
  
Здесь приведен пример данных источника, содержащихся в файле SampleCurrencyData.txt:  
  
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
  
При работе с данными источника неструктурированных файлов важно понимать, как диспетчер соединений с неструктурированными файлами интерпретирует данные неструктурированных файлов. Если неструктурированный файл является документом в Юникоде, диспетчер соединений с неструктурированными файлами определяет все столбцы как [DT_WSTR] с шириной, по умолчанию равной 50. Если неструктурированный файл является документом в кодировке ANSI, все столбцы определяются как [DT_STR] с шириной, равной 50. Возможно, потребуется изменить эти настройки, чтобы оптимизировать столбцы для конкретных данных. Чтобы сделать это, необходимо узнать тип данных в назначении, куда будут заноситься эти данные, а затем выбрать правильный тип данных в диспетчере соединений с неструктурированными файлами.  
  
### <a name="looking-at-the-destination"></a>Анализ назначения  
Конечным назначением исходных данных является копия таблицы фактов **FactCurrencyRate** в базе данных **AdventureWorksDW**. Таблица фактов **FactCurrencyRate** имеет четыре столбца и связи с двумя таблицами измерений, как показано в следующей таблице.  
  
|Имя столбца|Тип данных|Таблица уточняющих запросов|Уточняющий столбец|  
|---------------|-------------|----------------|-----------------|  
|AverageRate|FLOAT|None|None|  
|CurrencyKey|int (FK)|DimCurrency|CurrencyKey (PK)|  
|DateKey|int (FK)|DimDate|DateKey (PK)|  
|EndOfDayRate|FLOAT|None|None|  
  
### <a name="mapping-source-data-to-be-compatible-with-the-destination"></a>Сопоставление совместимых данных источника с назначением  
Анализ форматов данных источника и назначения показывает, что для значений **CurrencyKey** и **DateKey** требуются уточняющие запросы. Преобразования, которые выполнят эти уточняющие запросы, получат значения **CurrencyKey** и **DateKey** , с помощью альтернативных ключей из таблиц измерений **DimCurrency** и **DimDate** .  
  
|Столбец неструктурированных файлов|Имя таблицы|Имя столбца|Тип данных|  
|--------------------|--------------|---------------|-------------|  
|0|FactCurrencyRate|AverageRate|float|  
|1|DimCurrency|CurrencyAlternateKey|nchar (3)|  
|2|DimDate|FullDateAlternateKey|Дата|  
|3|FactCurrencyRate|EndOfDayRate|FLOAT|  
  
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Создание нового проекта служб Integration Services](../integration-services/lesson-1-1-creating-a-new-integration-services-project.md)  
  
-   [Шаг 2. Добавление и настройка диспетчера подключения неструктурированных файлов](../integration-services/lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [Шаг 3. Добавление и настройка диспетчера подключений OLE DB](../integration-services/lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [Шаг 4. Добавление задачи потока данных в пакет](../integration-services/lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [Шаг 5. Добавление и настройка источника неструктурированных файлов](../integration-services/lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [Шаг 6. Добавление и настройка преобразований "Уточняющий запрос"](../integration-services/lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [Шаг 7. Добавление и настройка назначения OLE DB](../integration-services/lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [Шаг 8. Упрощение чтения пакета, созданного на занятии 1](../integration-services/lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [Шаг 9. Проверка учебного пакета, созданного на занятии 1](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Создание нового проекта служб Integration Services](../integration-services/lesson-1-1-creating-a-new-integration-services-project.md)  
  
