---
title: "Службы SQL Server R Настройка производительности | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf6f3b7d-f9f9-4e45-b0d1-07850b53e0c5
caps.latest.revision: 20
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 19
---
# Службы SQL Server R Настройка производительности
[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] предоставляет платформу для разработки интеллектуальных приложений, предназначенных для получения новых аналитических данных. В обработке данных можно использовать возможности языка R для обучения и создавать модели, используя данные, хранящиеся внутри [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Как только модель готова для производства, специалистом в обработке данных можно работать с администраторами баз данных и инженеров SQL для развертывания решения в рабочей среде. Сведения в этом разделе инструкции высокой уровня настройки производительности обоих при создании и обучения модели и при развертывании модели в рабочей среде.

Сведения в этом документе предполагается, что вы знакомы с [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] Основные понятия и терминология. Общие сведения о службах R см. в разделе [R служб SQL Server](../../advanced-analytics/r-services/sql-server-r-services.md).

> [!NOTE]
> Хотя большая часть информации в данном разделе общих рекомендаций по настройке [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], некоторые информация относится только к RevoScaleR аналитические функции.

## В этом разделе

* [Конфигурация SQL Server](../../advanced-analytics/r-services/sql-server-configuration-r-services.md): этот документ содержит рекомендации по настройке оборудования, [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] устанавливается на. Это может пригодиться для __администраторов баз данных__.

* [R и оптимизации данных](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md): в этом документе приведены инструкции по использовании сценариев R со службами R. Это может пригодиться для __анализу данных__.

* [Исследование производительности](../../advanced-analytics/r-services/performance-case-study-r-services.md): этот документ содержит тестовые данные и скриптов R, которые могут использоваться для проверки влияния рекомендации, содержащиеся в предыдущих документов.

## Ссылки

Ниже приведены ссылки на сведения, используемые при разработке настоящего документа.

* [Определение необходимого размера файла подкачки для 64-разрядных версий Windows](https://support.microsoft.com/kb/2860880)

* [Сжатие данных](../../relational-databases/data-compression/data-compression.md)

* [Включение сжатия таблицы или индекса](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

* [Отключение сжатия таблицы или индекса](../../relational-databases/data-compression/disable-compression-on-a-table-or-index.md)

* [Средство тестирования DISKSPD хранения нагрузки генератора и производительности](https://github.com/microsoft/diskspd)

* [Ссылка на FSUtil служебных программ](https://technet.microsoft.com/library/cc753059.aspx)

* [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)

* [Службы R Services](../../advanced-analytics/r-services/r-services.md)

* [Параметры настройки производительности rxDForest и rxDTree](https://support.microsoft.com/kb/3104235)

* [Наблюдение и настройка производительности](../../relational-databases/performance/monitor-and-tune-for-performance.md)

* [Руководство пользователя RevoScaleR](https://packages.revolutionanalytics.com/doc/7.0.0/win/RevoScaleR_Users_Guide.pdf)

* [Регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)

## См. также:

 
 [Настройка SQL Server для служб R](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
 
 [Исследование производительности](../../advanced-analytics/r-services/performance-case-study-r-services.md)
 
 [R и оптимизация данных](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md)