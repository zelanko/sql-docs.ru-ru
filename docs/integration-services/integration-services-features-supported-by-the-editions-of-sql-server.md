---
title: "Функции, поддерживаемые различными выпусками SQL Server служб Integration Services | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 8cc1fcfdeae8742a93916dfb08c9db1215f88721
ms.openlocfilehash: e9d1b8851f113fa44264230a79d0e496007ed96b
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="integration-services-features-supported-by-the-editions-of-sql-server"></a>Возможности интеграции служб, поддерживаемые различными выпусками SQL Server
 В этом разделе подробно описаны функции служб SQL Server Integration Services (SSIS), поддерживаемые различными выпусками [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)].  

Возможности, поддерживаемые выпусками Evaluation и Developer см. в функции, перечисленные для выпуска Enterprise Edition в следующих таблицах.
  
Последние заметки о выпуске и возможности новой информации см. следующие статьи:
-   [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
-   [Новые возможности служб Integration Services в SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)
-   [Новые возможности служб Integration Services в SQL Server 2017](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md)
    
**Оцените SQL Server 2016!**    

Выпуск SQL Server Evaluation доступен для ознакомления в течение 180 дней.  
    
> [![Скачать на странице центра оценки](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Скачайте SQL Server 2016 на странице центра оценки](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
## <a name="ISNew"></a>Новые возможности служб Integration Services в SQL Server 2017 г.
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Горизонтальное масштабирование Master|Да|||||
|Горизонтальное масштабирование работника|Да|Да <sup>1</sup>|TBD|TBD|TBD|
|Поддержка Microsoft Dynamics AX и Microsoft Dynamics CRM в компонентах OData <sup>2</sup>|Да|Да||||

<sup>1</sup> при выполнении пакетов, которые требуется только для корпоративных возможностей в масштабное развертывание работников масштабирования, необходимо также выполнить на экземплярах SQL Server Enterprise.

<sup>2</sup> эта функция также поддерживается в SQL Server 2016 с пакетом обновления 1.

## <a name="IEWiz"></a>Мастер экспорта и импорта SQL Server

|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|мастер импорта и экспорта SQL Server|Да|Да|Да|Да|Да|  

## <a name="IS"></a> Службы Integration Services  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Встроенные соединители источника данных|Да|Да|||| 
|Встроенные задачи и преобразования|Да|Да||||  
|Источник и назначение от компании Attunity|Да|Да|||| 
|Соединители источника данных Azure и задачи|Да|Да||||  
|Hadoop и HDFS соединители и задачи|Да|Да||||  
|Средства профилирования основных данных|Да|Да|||| 

## <a name="ISAA"></a>Службы Integration Services — Дополнительные источники и назначения  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Высокопроизводительный Oracle источника и назначения от компании Attunity|Да|||||  
|Источник Teradata высокой производительности и назначение от компании Attunity|Да|||||  
|Источник и назначение SAP BW|Да|||||  
|Назначение «Обучение модели интеллектуального анализа данных»|Да|||||  
|Назначение «Обработка измерений»|Да|||||  
|Назначение обработки секции|Да|||||  
  
## <a name="ISAT"></a>Службы Integration Services — дополнительные задачи и преобразования  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Изменить компоненты отслеживания измененных данных attunity <sup>1</sup>|Да|||||  
|Преобразование «Запрос интеллектуального анализа данных»|Да|||||  
|«Нечеткое группирование» и «Нечеткий уточняющий запрос»|Да|||||  
|Извлечение терминов и «Уточняющий запрос термина»|Да|||||  

<sup>1</sup> компоненты измененных данных attunity требуют Enterprise edition. Change Data Capture Service и записать конструктор данных, тем не менее, не требуют Enterprise edition. Можно использовать конструктор и служба на компьютере, где не установлено служб SSIS.

