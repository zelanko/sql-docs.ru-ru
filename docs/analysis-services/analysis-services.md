---
title: "Analysis Services | Microsoft Docs"
ms.date: "03/28/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "Службы Analysis Services, сведения о службах Analysis Services — многомерные данные"
  - "Службы SSAS"
  - "Analysis Services"
  - "Службы SQL Server Analysis Services, сведения о службах Analysis Services — многомерные данные"
  - "службы SQL Server Analysis Services"
  - "многомерные данные [Analysis Services]"
  - "SSAS, сведения о службах Analysis Services — многомерные данные"
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
caps.latest.revision: 60
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 60
---
# Analysis Services
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] — подсистема аналитики данных в Интернете, которая используется в принятии решений и бизнес-аналитике. Эта подсистема предоставляет аналитические данные, которые применяются в деловых отчетах и клиентских приложениях, таких как Power BI, Excel, отчеты служб Reporting Services, а также других инструментах визуализации данных от сторонних производителей.  
  
 Типовой рабочий процесс для [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] включает построение модели на основе многомерных или табличных данных, развертывание модели как базы данных в экземпляре [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , обработку базы данных для загрузки в нее данных или метаданных и назначение разрешений на доступ к данным конечным пользователям. После подготовки доступ к этой многоцелевой семантической модели данных может осуществляться любым клиентским приложением, поддерживающим [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в качестве источника данных.  
  
 Модели заполняются данными из внешних систем обработки данных. Обычно это хранилища данных, размещенные в системе управления реляционными базами данных SQL Server или Oracle (табличные модели поддерживают дополнительные типы источников данных). Модели определяют объекты запроса, такие как кубы, указывают измерения, которые могут использоваться в нескольких кубах, вычисления и ключевые показатели эффективности, которые инкапсулируют бизнес-логику, а также такие режимы работы, как навигация и детализация.  
 
## <a name="analysis-services-on-premises-and-in-the-cloud"></a>Службы Analysis Services локально и в облаке
Службы Analysis Services теперь доступны в облаке как служба Azure. На данный момент в предварительной версии служба Azure Analysis Services поддерживает табличные модели на уровне совместимости 1200. DirectQuery, секции, безопасность на уровне строк, двунаправленные связи и переводы полностью поддерживаются. Дополнительные сведения и пробную версию можно найти на странице [Azure Analysis Services](https://azure.microsoft.com/en-us/services/analysis-services/). 
  
## <a name="server-mode"></a>Режим сервера  
 При установке служб Analysis Services с помощью программы установки [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] для этого экземпляра задается режим сервера.  Каждый режим включает различные функции, относящиеся к определенному решению служб Analysis Services.  
  
-   **Многомерный и режим интеллектуального анализа данных** — реализация конструкций моделирования OLAP (кубов, измерений, мер).  
  
-   **Табличный режим** — реализация реляционных конструкций моделирования (моделей, таблиц, столбцов).  
  
     Табличные модели могут создаваться при уровне совместимости 1200 (по умолчанию) для использования новейших функций или при более старом уровне совместимости 1103. Значительных различий между уровнями совместимости нет. Дополнительные сведения о сравнении уровней совместимости см. в разделе [Уровень совместимости табличных моделей в службах Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).  
  
-   **Режим Power Pivot** — реализация моделей данных [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] и Excel в SharePoint ([!INCLUDE[ssGemini](../includes/ssgemini-md.md)] для SharePoint является подсистемой обработки данных среднего уровня, которая загружает, запрашивает и обновляет модели данных, размещенные в SharePoint).  
  
 Одиночный экземпляр можно настроить только в одном режиме, изменить который впоследствии будет невозможно.  На один сервер можно установить несколько экземпляров, настроенных в различных режимах, однако для каждого из них необходимо запустить программу установки и указать параметры конфигурации.  
  
 Функции [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] различаются в зависимости от выпуска. Дополнительные сведения см. в разделе [Возможности, поддерживаемые различными выпусками SQL Server 2016](../sql-server/возможности-поддерживаемые-различными-выпусками-sql-server-2016.md). 
  
## <a name="authoring-solutions"></a>Создание решений  
 Чтобы создать модель, используйте SQL Server Data Tools (см. раздел [Средства и приложения, использующиеся в службах Analysis Services](../analysis-services/tools-and-applications-used-in-analysis-services.md)), выбрав шаблон проекта табличной или многомерной модели и интеллектуального анализа данных. Шаблон проекта содержит папки для всех объектов, необходимых в модели. Для создания многих основных элементов, таких как источники данных, представления источников данных, измерения, кубы и роли, можно использовать мастеры.  
  
## <a name="documentation-by-area"></a>Документация по разделам  
Документация по службам Analysis Services организована по разделам, которые соответствуют типу создаваемого объекта. Дополнительные сведения о каждом режиме или функциональной области см. в разделах по следующим ссылкам.  
   
 ![Маленький значок папки](../analysis-services/media/filefolder-small.png "Маленький значок папки") [Новые возможности](../analysis-services/what-s-new-in-analysis-services.md)  
  
 ![Маленький значок папки](../analysis-services/media/filefolder-small.png "Маленький значок папки") [Сравнение табличных и многомерных решений](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![Маленький значок папки](../analysis-services/media/filefolder-small.png "Маленький значок папки") [Табличные модели](../analysis-services/tabular-models/tabular-models-ssas.md)  
  
 ![Маленький значок папки](../analysis-services/media/filefolder-small.png "Маленький значок папки") [Многомерные модели](../analysis-services/multidimensional-models/multidimensional-models-ssas.md)  
  
 ![Маленький значок папки](../analysis-services/media/filefolder-small.png "Маленький значок папки") [Интеллектуальный анализ данных](../analysis-services/data-mining/data-mining-ssas.md)  
  
 ![Маленький значок папки](../analysis-services/media/filefolder-small.png "Маленький значок папки") [Power Pivot для SharePoint](../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
 ![Маленький значок папки](../analysis-services/media/filefolder-small.png "Маленький значок папки") [Управление экземплярами служб Analysis Services](../analysis-services/instances/analysis-services-instance-management.md)  
   
 ![Маленький значок папки](../analysis-services/media/filefolder-small.png "Маленький значок папки") [Учебники по службам Analysis Services](../analysis-services/analysis-services-tutorials-ssas.md)  
  
![Маленький значок папки](../analysis-services/media/filefolder-small.png "Маленький значок папки") [Документация для разработчика служб Analysis Services](https://msdn.microsoft.com/library/bb500153(SQL.130).aspx)  
 
![Маленький значок папки](../analysis-services/media/filefolder-small.png "Маленький значок папки") [Технический справочник (службы SSAS)](../analysis-services/powershell/technical-reference-ssas.md)