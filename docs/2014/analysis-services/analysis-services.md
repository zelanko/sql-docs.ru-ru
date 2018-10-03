---
title: Службы Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, about Analysis Services - Multidimensional Data
- SSAS
- Analysis Services
- SQL Server Analysis Services, about Analysis Services - Multidimensional Data
- SQL Server Analysis Services
- multidimensional data [Analysis Services]
- SSAS, about Analysis Services - Multidimensional Data
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c2bcf7cb620a97578b921ca09d565ff2ef2fe77a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080977"
---
# <a name="analysis-services"></a>Службы Analysis Services
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] — подсистема аналитики данных в Интернете, которая используется в решениях для бизнес-аналитики (BI) и поддержки принятия решений. Эта подсистема предоставляет аналитические данные, которые применяются в бизнес-отчетах и клиентских приложениях, таких как Excel, отчеты служб Reporting Services, а также других сторонних средствах бизнес-аналитики. Типовой рабочий процесс для [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] включает построение модели на основе OLAP или табличных данных, развертывание модели в виде базы данных на экземпляре [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], обработку базы данных для загрузки в нее данных и присваивание разрешений на доступ к данным. После подготовки доступ к этой многоцелевой модели данных может осуществляться любым клиентским приложением, поддерживающим [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в качестве источника данных.  
  
 Чтобы создать модель, используйте SQL Server Data Tools (см. в разделе [средств и приложений, используемых в службах Analysis Services](tools-and-applications-used-in-analysis-services.md)), выбрав табличный или многомерный и интеллектуальный анализ данных шаблон проекта. Шаблон проекта содержит папки для всех объектов, необходимых в модели. Для создания всех основных элементов, таких как источники данных, представления источников данных, измерения, кубы и роли, можно использовать мастеры.  
  
 Модели заполняются данными из внешних систем обработки данных. Обычно это хранилища данных, размещенные в системе управления реляционными базами данных SQL Server или Oracle (табличные модели поддерживают дополнительные типы источников данных). Модели определяют объекты запроса, такие как кубы, указывают измерения, которые могут использоваться в нескольких кубах, вычисления и ключевые показатели эффективности, которые инкапсулируют бизнес-логику, а также такие режимы работы, как навигация и детализация.  
  
 Для использования модели она развертывается на экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], где базы данных работают в определенном режиме сервера, что делает данные доступными авторизованным пользователям, которые подключаются к ним посредством Excel или других приложений.  
  
 Можно установить экземпляр [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в одном из трех режимов сервера.  
  
-   Как табличный экземпляр, выполняющий табличные модели.  
  
-   Как экземпляр многомерных моделей и интеллектуального анализа данных, выполняющий кубы OLAP и модели интеллектуального анализа данных (режим по умолчанию).  
  
-   Как PowerPivot для SharePoint, выполняющий модели данных PowerPivot и Excel в SharePoint (PowerPivot для SharePoint является подсистемой обработки данных среднего уровня, которая загружает, запрашивает и обновляет модели данных, размещенные в SharePoint).  
  
 Одна подсистема обработки данных — три разных способа ее использования. Обратите внимание, что режимы сервера задаются во время установки и не могут быть изменены впоследствии. Если вам потребуется другой режим, необходимо будет установить новый экземпляр.  
  
 Основная документация по службам Analysis Services организована по разделам, которые соответствуют типу создаваемого объекта. Дополнительные сведения о каждом режиме или функциональной области см. в разделах по следующим ссылкам.  
  
 **Просмотр содержимого по области**  
 ![Маленький значок папки](../../2014/integration-services/media/filefolder-small.gif "маленький значок папки") [сравнение табличных и многомерных решений &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![Маленький значок папки](../../2014/integration-services/media/filefolder-small.gif "маленький значок папки") [управление экземплярами служб Analysis Services](instances/analysis-services-instance-management.md)  
  
 ![Маленький значок папки](../../2014/integration-services/media/filefolder-small.gif "маленький значок папки") [табличного моделирования &#40;табличные службы SSAS&#41;](tabular-models/tabular-models-ssas.md)  
  
 ![Маленький значок папки](../../2014/integration-services/media/filefolder-small.gif "маленький значок папки") [многомерное моделирование &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)  
  
 ![Маленький значок папки](../../2014/integration-services/media/filefolder-small.gif "маленький значок папки") [интеллектуального анализа данных &#40;SSAS&#41;](data-mining/data-mining-ssas.md)  
  
 ![Маленький значок папки](../../2014/integration-services/media/filefolder-small.gif "маленький значок папки") [PowerPivot для SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
> [!NOTE]  
>  Функции [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] различаются в зависимости от выпуска. Многомерные модели и модели интеллектуального анализа данных поддерживаются в стандартном выпуске, но с меньшим количеством функций по сравнению с выпусками более высокого уровня. Табличные модели и PowerPivot для SharePoint являются функциями высокого уровня, которые отсутствуют в стандартном выпуске. Дополнительные сведения см. в разделе [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>См. также  
 [Руководства по службам Analysis &#40;SSAS&#41;](analysis-services-tutorials-ssas.md)   
 [Установка SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Руководство разработчика &#40;служб Analysis Services&#41;](analysis-services-developer-documentation.md)   
 [Центр ресурсов SQL Server](http://go.microsoft.com/fwlink/?linkID=219676)   
 [Сайте SQLCat.com](http://go.microsoft.com/fwlink/?linkID=220963)  
  
  
