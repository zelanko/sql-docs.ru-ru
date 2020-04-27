---
title: SQL Server 2014 Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: 986356e6ebf7697bf0b425553f6803659a0fc5cb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "80760300"
---
# <a name="sql-server-2014-analysis-services"></a>SQL Server 2014 Analysis Services

  SQL Server 2014 Analysis Services — это модуль аналитических данных, используемый в решениях для поддержки принятия решений и бизнес-аналитики (BI), предоставляющий аналитические данные для бизнес-отчетов и клиентских приложений, таких как Excel, отчеты Reporting Services и другие сторонние средства бизнес-аналитики. 

## <a name="about-sql-server-analysis-services-documentation"></a>Документация по SQL Server Analysis Services

Документация разделена по версии. В настоящее время вы используете SQL Server 2014 Analysis Services документацию.

- Дополнительные сведения о SQL Server 2012 и более ранних версиях см. в [документации по SQL Server предыдущих версий](https://docs.microsoft.com/previous-versions/sql/).
- Дополнительные сведения о SQL Server 2014 см. в [электронной документации по SQL Server 2014](../2014-toc/index.yml)
- Дополнительные сведения о SQL Server 2016 и более поздних версиях см. в [документации по Analysis Services](https://docs.microsoft.com/analysis-services/).
- Дополнительные сведения о Azure Analysis Services см. в [документации по Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/).

## <a name="analysis-services-workflow"></a>Рабочий процесс Analysis Services

Типичный рабочий процесс включает создание модели OLAP или табличных данных, развертывание модели в качестве базы данных на экземпляре сервера, обработку базы данных для ее загрузки с данными, а затем назначение разрешений для разрешения доступа к данным. После подготовки доступ к этой многоцелевой модели данных может осуществляться любым клиентским приложением, поддерживающим [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в качестве источника данных.  
  
 Чтобы создать модель, используйте SQL Server Data Tools (см. раздел [средства и приложения, используемые в Analysis Services](tools-and-applications-used-in-analysis-services.md)), выбрав шаблон проекта табличный или многомерный и интеллектуальный анализ данных. Шаблон проекта содержит папки для всех объектов, необходимых в модели. Для создания всех основных элементов, таких как источники данных, представления источников данных, измерения, кубы и роли, можно использовать мастеры.  
  
 Модели заполняются данными из внешних систем обработки данных. Обычно это хранилища данных, размещенные в системе управления реляционными базами данных SQL Server или Oracle (табличные модели поддерживают дополнительные типы источников данных). Модели определяют объекты запроса, такие как кубы, указывают измерения, которые могут использоваться в нескольких кубах, вычисления и ключевые показатели эффективности, которые инкапсулируют бизнес-логику, а также такие режимы работы, как навигация и детализация.  
  
 Чтобы использовать модель, она развертывается на экземпляре сервера, где выполняются базы данных в определенном режиме сервера, делая их доступными для полномочных пользователей, подключающихся через Excel или другие приложения.  
  
 Экземпляр можно установить в одном из трех режимов сервера:  
  
-   Как табличный экземпляр, выполняющий табличные модели.  
  
-   Как экземпляр многомерных моделей и интеллектуального анализа данных, выполняющий кубы OLAP и модели интеллектуального анализа данных (режим по умолчанию).  
  
-   Как PowerPivot для SharePoint, выполняющий модели данных PowerPivot и Excel в SharePoint (PowerPivot для SharePoint является подсистемой обработки данных среднего уровня, которая загружает, запрашивает и обновляет модели данных, размещенные в SharePoint).  
  
 Одна подсистема обработки данных — три разных способа ее использования. Обратите внимание, что режимы сервера задаются во время установки и не могут быть изменены впоследствии. Если вам потребуется другой режим, необходимо будет установить новый экземпляр.  
  
 Основная документация по службам Analysis Services организована по разделам, которые соответствуют типу создаваемого объекта. Дополнительные сведения о каждом режиме или функциональной области см. в разделах по следующим ссылкам.  
  
 **Просмотр содержимого по областям**  
 ![Маленький значок папки с файлами](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [Сравнение табличных и многомерных решений &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![Маленький значок папки с файлами](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [Analysis Services управление экземплярами](instances/analysis-services-instance-management.md)  
  
 ![Маленький значок папки с файлами](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [табличное моделирование &#40;ТАБЛИЧные&#41;SSAS](tabular-models/tabular-models-ssas.md)  
  
 ![Маленький значок папки с файлами](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [многомерное моделирование &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)  
  
 ![Маленький значок папки](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [интеллектуальный анализ данных &#40;SSAS&#41;](data-mining/data-mining-ssas.md)  
  
 ![Маленький значок папки](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [PowerPivot для SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
> [!NOTE]  
>  Функции [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] различаются в зависимости от выпуска. Многомерные модели и модели интеллектуального анализа данных поддерживаются в стандартном выпуске, но с меньшим количеством функций по сравнению с выпусками более высокого уровня. Табличные модели и PowerPivot для SharePoint являются функциями высокого уровня, которые отсутствуют в стандартном выпуске. Дополнительные сведения см. [в разделе функции, поддерживаемые различными Выпусками SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>См. также  
 [Учебники по Analysis Services &#40;SSAS&#41;](analysis-services-tutorials-ssas.md)   
 [Установка для SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [&#40;Analysis Services с руководством разработчика&#41;](analysis-services-developer-documentation.md)   
 [Центр ресурсов SQL Server](https://go.microsoft.com/fwlink/?linkID=219676)   
 [SQLCat.com](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
