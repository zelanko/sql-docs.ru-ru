---
title: "Уровень совместимости табличных моделей в службах Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.versioncompat.f1"
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
caps.latest.revision: 27
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 27
---
# Уровень совместимости табличных моделей в службах Analysis Services
  *Уровень совместимости* модели или базы данных обозначает набор моделей поведения конкретного выпуска в ядре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Вы можете создать модели на любом доступном уровне совместимости, чтобы эмулировать поведение конкретного выпуска. Например, DirectQuery и метаданные табличных объектов имеют разные реализации в зависимости от установленного уровня совместимости.  
  
 **SQL Server 2016 RTM (1200)**, кратко именуемый уровнем совместимости 1200, — это новый компонент SQL Server 2016, который применяется только к табличным моделям.  Табличные модели на уровне совместимости 1200 будут выполняться только на табличном экземпляре [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] .  
  
 Чтобы создать или обновить табличную модель, используйте SQL Server Data Tools (SSDT) и установите свойство **Уровень совместимости** при создании проекта или после создания в файле **model.bim**.  
  
> [!NOTE]  
>  Для многомерных моделей используется своя нумерация версий в контексте уровней совместимости. Одинаковые числа, как в случае с версией 1103, это — совпадение. Дополнительные сведения см. в разделе [Уровень совместимости многомерной базы данных (службы Analysis Services)](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md).  
  
## Поддерживаемые уровни совместимости для баз данных табличной модели  
 Службы Analysis Services поддерживают следующие уровни совместимости (как для моделей, так и для баз данных).  Возможность использования более высоких уровней совместимости зависит от версии средства, использованного для создания модели.  
  
||||  
|-|-|-|  
|Уровень совместимости|Версия сервера|Версия средства моделирования|  
|1200|Работает только на экземплярах SQL Server 2016|[Только SQL Server Data Tools для Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkID=690931) <sup>1</sup><br /><br /> [What's New in Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md) предоставляет сведения о функциональных возможностях, доступных на этом уровне.|  
|1103|SQL Server 2016<br /><br /> SQL Server 2014<br /><br /> SQL Server 2012 SP1|[SQL Server Data Tools для Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkID=690931) <sup>2</sup><br /><br /> [SQL Server Data Tools для Business Intelligence (Visual Studio 2013)](https://www.microsoft.com/en-us/download/details.aspx?id=42313)<br /><br /> [SQL Server Data Tools для Business Intelligence (Visual Studio 2012)](http://www.microsoft.com/en-us/download/details.aspx?id=36843)|  
|1100|SQL Server 2016<br /><br /> SQL Server 2014<br /><br /> SQL Server 2012 SP1<br /><br /> SQL Server 2012|[SQL Server Data Tools для Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkID=690931) <sup>1</sup><br /><br /> [SQL Server Data Tools для Business Intelligence (Visual Studio 2013)](https://www.microsoft.com/en-us/download/details.aspx?id=42313)<br /><br /> [SQL Server Data Tools для Business Intelligence (Visual Studio 2012)](http://www.microsoft.com/en-us/download/details.aspx?id=36843)<br /><br /> Business Intelligence Development Studio (запускается в оболочке Visual Studio 2010 и устанавливается с помощью программы установки SQL Server)|  
  
 <sup>1</sup> SQL Server Data Tools для Visual Studio 2015 можно использовать для развертывания табличной модели 1100 или 1103 в более ранних выпусках служб Analysis Services.  
  
 <sup>2</sup> уровни совместимости 1100, 1103 и 1200 одинаково подходят для проектов табличной модели в SQL Server Data Tools для Visual Studio 2015, но на экземпляре SQL Server 2016 служб Analysis Services можно развернуть и запустить только модель 1200.  
  
## Задание уровня совместимости при создании или обновлении проекта табличной модели в SSDT  
 При создании нового проекта табличной модели в SQL Server Data Tools (SSDT) в диалоговом окне **Параметры нового табличного проекта** можно указать уровень совместимости.  
  
 ![ssas_tabularproject_compat1200](../../analysis-services/tabular-models/media/ssas-tabularproject-compat1200.jpg "ssas_tabularproject_compat1200")  
  
 Также вы можете задать уровень совместимости по умолчанию, выбрав параметр **Больше не показывать это сообщение** . Во всех последующих проектах будет использоваться заданный уровень совместимости. Уровень совместимости, используемый в SSDT по умолчанию, вы можете изменить в меню **Инструменты** > **Параметры**.  
  
 Для обновления проекта табличной модели установите значение **SQL Server 2016 RTM (1200)** для свойства **Уровень совместимости** в окне **Свойства** нужной модели.  Подробнее см. в разделе [Upgrade Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md) .  
  
> [!NOTE]  
>  Создание табличной модели можно выполнить на основе импортированной книги Power Pivot. По умолчанию Power BI Desktop автоматически создает табличные модели на уровне совместимости 1200. Однако книги Power Pivot более ранних версий могут иметь уровень совместимости 1100. При использовании старой книги не забудьте обновить ее, то есть изменить свойство **Уровень совместимости** .  
  
## Проверка уровня совместимости для базы данных в среде SSMS  
 В среде SSMS щелкните правой кнопкой мыши имя базы данных и в контекстном меню выберите **Свойства** > **Уровень совместимости**.  
  
## Проверка поддерживаемого уровня совместимости для сервера в среде SSMS  
 В среде SSMS щелкните правой кнопкой мыши имя сервера и в контекстном меню выберите **Свойства** > **Поддерживаемый уровень совместимости**.  
  
 Это свойство указывает наивысший уровень совместимости базы данных, с которым она может работать на этом сервере.  Поддерживаемый уровень совместимости доступен только для чтения. Его нельзя изменить.  
  
## См. также  
 [Уровень совместимости многомерной базы данных (службы Analysis Services)](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Новые возможности в службах Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Импорт из PowerPivot (табличные службы SSAS)](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)   
 [Создание проекта табличной модели (службы Analysis Services)](../../analysis-services/tabular-models/create-a-new-tabular-model-project-analysis-services.md)  
  
  