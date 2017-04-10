---
title: "Функции служб Integration Services, поддерживаемые различными выпусками SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
caps.latest.revision: 15
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Функции служб Integration Services, поддерживаемые различными выпусками SQL Server
 В этом разделе подробно описаны функции служб SQL Server Integration Services (SSIS), поддерживаемые различными выпусками [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)].  

Компоненты, поддерживаемые выпусками Evaluation и Developer, перечислены в разделе SQL Server Enterprise Edition. 
  
Актуальные заметки о выпуске и сведения о новых возможностях содержатся в следующих разделах:
-   [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
-   [Новые возможности служб Integration Services в SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)
-   [Новые возможности служб Integration Services в SQL Server vNext](../integration-services/what-s-new-in-integration-services-in-sql-server-vnext.md)
    
**Оцените SQL Server 2016!**    

Выпуск SQL Server Evaluation доступен для ознакомления в течение 180 дней.  
    
> [![Скачать на странице центра оценки](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Скачайте SQL Server 2016 на странице центра оценки](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Значок виртуальной машины Azure](../analysis-services/media/azure-virtual-machine-small.png) **[Разверните виртуальную машину с уже установленным SQL Server 2016](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    

##  <a name="a-nameisanew-integration-services-features-in-sql-server-vnext"></a><a name="IS"></a> Новые функции служб Integration Services в SQL Server vNext
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express с инструментами|Express|Разработчик|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Масштабирование|Да||||||Да|
|Поддержка Microsoft Dynamics CRM и Microsoft Dynamics AX в компонентах OData <sup>1</sup>|Да|Да|||||Да|

<sup>1</sup> Эта функция также поддерживается в SQL Server 2016 с пакетом обновления 1 (SP1).

##  <a name="a-nameisa-integration-services"></a><a name="IS"></a> Службы Integration Services  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express с инструментами|Express|Разработчик|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Встроенные соединители источника данных|Да|Да|Да|Да|Да|Да|Да|  
|Соединители источника данных Azure и задачи|Да|Да|Да|Да|Да|Да|Да|  
|мастер импорта и экспорта SQL Server|Да|Да|Да|Да|Да|Да|Да|  
|Соединители и задачи Hadoop и HDFS|Да|Да|Да||||Да|  
|Конструктор и среда выполнения служб SSIS|Да|Да|||||Да|  
|Встроенные задачи и преобразования|Да|Да|||||Да|  
|Средства профилирования основных данных|Да|Да|||||Да|  
|Служба системы отслеживания измененных данных для Oracle компании Attunity|Да||||||Да|  
|Конструктор системы отслеживания измененных данных для Oracle компании Attunity|Да||||||Да| 

##  <a name="a-nameisaaa-integration-services---advanced-adapters"></a><a name="ISAA"></a> Службы Integration Services — дополнительные адаптеры  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express с инструментами|Express|Разработчик|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Высокопроизводительное назначение Oracle|Да||||||Да|  
|Высокопроизводительное назначение Teradata|Да||||||Да|  
|Источник и назначение SAP BW|Да||||||Да|  
|Адаптер загрузки обучающих данных модели интеллектуального анализа данных|Да||||||Да|  
|Адаптер загрузки данных «Обработка измерения»|Да||||||Да|  
|Адаптер загрузки данных обработки секций|Да||||||Да|  
|Компоненты системы отслеживания измененных данных от компании Attunity|Да||||||Да|  
|Соединитель для ODBC от компании Attunity|Да||||||Да|  
  
##  <a name="a-nameisata-integration-services---advanced-transforms"></a><a name="ISAT"></a> Службы Integration Services — дополнительные преобразования  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express с инструментами|Express|Разработчик|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Сохраняемые (высокопроизводительные) уточняющие запросы|Да||||||Да|  
|Преобразование «Запрос интеллектуального анализа данных»|Да||||||Да|  
|Преобразования «Нечеткое группирование» и «Уточняющий запрос»|Да||||||Да|  
|Извлечение терминов и преобразование «Уточняющий запрос»|Да||||||Да|  
  