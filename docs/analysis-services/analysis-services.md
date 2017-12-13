---
title: "Службы Analysis Services | Документы Microsoft"
ms.date: 05/11/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.custom: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Analysis Services, about Analysis Services - Multidimensional Data
- SSAS
- Analysis Services
- SQL Server Analysis Services, about Analysis Services - Multidimensional Data
- SQL Server Analysis Services
- multidimensional data [Analysis Services]
- SSAS, about Analysis Services - Multidimensional Data
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
caps.latest.revision: "60"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: d31d430fdaf5276b52a3f90efacf4a9a56576a35
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="what-is-analysis-services"></a>Новые возможности служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]Службы Analysis Services — это ядро аналитических данных, используемых в поддержки принятия решений и бизнес-аналитика, предоставляя аналитические данные для бизнес-отчеты и клиентские приложения, такие как Power BI, Excel, отчеты служб Reporting Services и других инструментах визуализации данных.  
  
 Типичный рабочий процесс включает создание модели, многомерные или табличные данные, развертывание модели в качестве базы данных на экземпляре сервера для локальных служб SQL Server Analysis Services или служб Azure Analysis Services, Настройка повторяющегося обработки данных и назначение разрешения на доступ к данным конечным пользователем. Когда она будет готова к работе, вашей семантическую модель данных может осуществляться любым клиентским приложениям, поддерживающих служб Analysis Services в качестве источника данных.  
 
## <a name="analysis-services-on-premises-and-in-the-cloud"></a>Службы Analysis Services локально и в облаке
Службы Analysis Services теперь доступны в облаке как служба Azure. Azure службы Analysis Services поддерживают табличные модели на уровне совместимости 1200 и выше. DirectQuery, секции, безопасность на уровне строк, двунаправленные связи и переводы полностью поддерживаются. Дополнительные сведения и пробную версию можно найти на странице [Azure Analysis Services](https://azure.microsoft.com/en-us/services/analysis-services/). 
  
## <a name="server-mode"></a>Режим сервера  
 При установке служб Analysis Services с помощью программы установки SQL Server, во время настройки можно указать режим сервера для этого экземпляра.  Каждый режим включает различные функции, относящиеся к определенному решению служб Analysis Services.   
  
-   **Табличный режим** - реляционных данных в памяти реализуют моделирования конструкции (модели, таблицы, столбцы, меры, иерархии).  

-   **Многомерный и режим интеллектуального анализа данных** — реализация конструкций моделирования OLAP (кубов, измерений, мер). 

-   **Power Pivot Mode** -модели данных Power Pivot реализуйте и Excel в SharePoint (Power Pivot для SharePoint представляет собой механизм данных среднего уровня, который загружает, запрашивает и обновляет модели данных, размещенные в SharePoint).  
  
 Одиночный экземпляр можно настроить только в одном режиме, изменить который впоследствии будет невозможно.  На один сервер можно установить несколько экземпляров, настроенных в различных режимах, однако для каждого из них необходимо запустить программу установки и указать параметры конфигурации. Подробные сведения и сравнения различных возможностей, предоставляемых в каждом из режимов, в разделе [сравнение табличных и многомерных решений](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md).
  
## <a name="authoring-and-managing-solutions"></a>Создание решений и управление ими  
 Чтобы создать модель и развернуть ее на сервере, используйте SQL Server Data Tools, выбрав шаблон проекта либо табличный или многомерный и интеллектуальный анализ данных. Шаблон проекта содержит папки для всех объектов, необходимых в модели. Мастера и конструкторы для создания многих основные элементы, такие как подключение к источникам данных, связи, меры и ролей. После развертывания базы данных модели на сервере SQL Server Management Studio (SSMS) используется для обработки данных настройки, наблюдения и управления сервером и базами данных. Дополнительные сведения см. в разделе [средств и приложений, используемых в службах Analysis Services](../analysis-services/tools-and-applications-used-in-analysis-services.md). 
  
## <a name="documentation-by-area"></a>Документация по разделам  
В общем, документация по Azure Analysis Services входит в состав документации Azure. И документация по SQL Server Analysis Services входит в состав документации SQL. Тем не менее по крайней мере для табличных моделей, как создавать и развертывать проекты является так же, независимо от того, какие платформы, вы используете.  
   
*  [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/)
*  [Новые возможности SQL Server Analysis Services](../analysis-services/what-s-new-in-analysis-services.md)   
*  [Сравнение табличных и многомерных решений](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
*  [Табличные модели](../analysis-services/tabular-models/tabular-models-ssas.md)  
*  [Многомерные модели](../analysis-services/multidimensional-models/multidimensional-models-ssas.md)  
*  [Интеллектуальный анализ данных](../analysis-services/data-mining/data-mining-ssas.md)  
*  [Power Pivot для SharePoint](../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
*  [Управление экземплярами](../analysis-services/instances/analysis-services-instance-management.md)    
*  [Руководства](../analysis-services/analysis-services-tutorials-ssas.md)   
*  [Документация для разработчиков](https://msdn.microsoft.com/library/bb500153(SQL.130).aspx)  
*  [Технический справочник (службы SSAS)](../analysis-services/powershell/technical-reference-ssas.md)
