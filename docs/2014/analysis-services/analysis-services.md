---
title: Аналитические услуги сервера S'L 2014 Документы Майкрософт
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
ms.sourcegitcommit: 8f99d15c5b23d9f3c08a77e2b8bea5772f570493
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2020
ms.locfileid: "80760300"
---
# <a name="sql-server-2014-analysis-services"></a>SQL Server 2014 Analysis Services

  Аналитические службы S'L Server 2014 — это аналитический механизм данных, используемый в решениях поддержки решений и бизнес-аналитики (BI), предоставляющий аналитические данные для бизнес-отчетов и клиентских приложений, таких как Excel, Reporting Services и другие сторонние инструменты BI. 

## <a name="about-sql-server-analysis-services-documentation"></a>О документации по анализу серверов S'L

Документация разделена по версии. В настоящее время вы находитесь в документации аналитического сервиса S'L Server 2014.

- Чтобы узнать больше о сервере S'L [SQL Server previous versions documentation](https://docs.microsoft.com/previous-versions/sql/)2012 и более ранних версиях, см.
- Чтобы узнать больше о сервере S'L 2014, [см.](../2014-toc/index.yml)
- Чтобы узнать больше о сервере S'L [Analysis Services documentation](https://docs.microsoft.com/analysis-services/)Server 2016 и позже, см.
- Чтобы узнать больше об службах анализа Azure, смотрите [документацию аналитических служб Azure.](https://docs.microsoft.com/azure/analysis-services/)

## <a name="analysis-services-workflow"></a>Рабочий процесс аналитических служб

Типичный рабочий процесс включает в себя создание модели oLAP или табликовых данных, развертывание модели в качестве базы данных в экземплярсервера, обработку базы данных для загрузки данных, а затем назначение разрешений для обеспечения доступа к данным. После подготовки доступ к этой многоцелевой модели данных может осуществляться любым клиентским приложением, поддерживающим [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в качестве источника данных.  
  
 Для создания модели используйте инструменты для данных серверов (см. [Инструменты и приложения, используемые в аналитических службах),](tools-and-applications-used-in-analysis-services.md)выбирая шаблон проекта Tabular или Multidimensional и Data Mining. Шаблон проекта содержит папки для всех объектов, необходимых в модели. Для создания всех основных элементов, таких как источники данных, представления источников данных, измерения, кубы и роли, можно использовать мастеры.  
  
 Модели заполняются данными из внешних систем обработки данных. Обычно это хранилища данных, размещенные в системе управления реляционными базами данных SQL Server или Oracle (табличные модели поддерживают дополнительные типы источников данных). Модели определяют объекты запроса, такие как кубы, указывают измерения, которые могут использоваться в нескольких кубах, вычисления и ключевые показатели эффективности, которые инкапсулируют бизнес-логику, а также такие режимы работы, как навигация и детализация.  
  
 Для использования модели она развернута в экземпляре сервера, который запускает базы данных в определенном режиме сервера, делая данные доступными для авторизованных пользователей, которые подключаются через Excel или другие приложения.  
  
 Вы можете установить экземпляр в одном из трех серверных режимов:  
  
-   Как табличный экземпляр, выполняющий табличные модели.  
  
-   Как экземпляр многомерных моделей и интеллектуального анализа данных, выполняющий кубы OLAP и модели интеллектуального анализа данных (режим по умолчанию).  
  
-   Как PowerPivot для SharePoint, выполняющий модели данных PowerPivot и Excel в SharePoint (PowerPivot для SharePoint является подсистемой обработки данных среднего уровня, которая загружает, запрашивает и обновляет модели данных, размещенные в SharePoint).  
  
 Одна подсистема обработки данных — три разных способа ее использования. Обратите внимание, что режимы сервера задаются во время установки и не могут быть изменены впоследствии. Если вам потребуется другой режим, необходимо будет установить новый экземпляр.  
  
 Основная документация по службам Analysis Services организована по разделам, которые соответствуют типу создаваемого объекта. Дополнительные сведения о каждом режиме или функциональной области см. в разделах по следующим ссылкам.  
  
 **Просмотр контента по районам**  
 ![Малый файл Фолдер значок](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [Сравнение табулярных и многомерных решений &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![Малый файл Фолдер значок](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [Анализ служб instance Управления](instances/analysis-services-instance-management.md)  
  
 ![Малый файл Фолдер](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [иконописного моделирования &#40;SSAS Tabular&#41;](tabular-models/tabular-models-ssas.md)  
  
 ![Малый файл Фолдер значок](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [многомерное моделирование &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)  
  
 ![Малый файл Фолдер значок данных](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [&#40;SSAS&#41;](data-mining/data-mining-ssas.md)  
  
 ![Малый файл Фолдер значок](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [PowerPivot для SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
> [!NOTE]  
>  Функции [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] различаются в зависимости от выпуска. Многомерные модели и модели интеллектуального анализа данных поддерживаются в стандартном выпуске, но с меньшим количеством функций по сравнению с выпусками более высокого уровня. Табличные модели и PowerPivot для SharePoint являются функциями высокого уровня, которые отсутствуют в стандартном выпуске. Для получения дополнительной информации [см.](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
## <a name="see-also"></a>См. также:  
 [Учебники по анализу &#40;SSAS&#41;](analysis-services-tutorials-ssas.md)   
 [Установка для сервера S'L 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [&#41;&#41;справочные службы &#40;анализа разработчика](analysis-services-developer-documentation.md)   
 [Ресурсный центр сервера S'L](https://go.microsoft.com/fwlink/?linkID=219676)   
 [SQLCat.com](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
