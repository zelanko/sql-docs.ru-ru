---
title: Проект скриптов в SQL Server Management Studio для служб Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [Analysis Services]
- scripts [Analysis Services], projects
- projects [Analysis Services], Analysis Server Scripts project
- projects [Analysis Services], creating
- Analysis Server Scripts project
- items [Analysis Services]
ms.assetid: c4f5a06b-e2e4-4660-a3a8-6fd356742c02
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8d1553189b3d25da5394ea2f5f32a411134206b3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207650"
---
# <a name="analysis-services-scripts-project-in-sql-server-management-studio"></a>Проект скриптов служб Analysis Services в среде SQL Server Management Studio
  В службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]вы можете создать проект скриптов для служб Analysis Server в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , чтобы сгруппировать связанные скрипты для совместной разработки, управления и контроля версий. Если в настоящий момент в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]не загружен проект, то при создании нового проекта сценария сервера анализа данных будет автоматически создано новое решение. В противном случае новый проект сценария сервера анализа данных может быть создан в новом решении или добавлен к нему.  
  
 Для создания проекта сценариев сервера анализа данных в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]используйте следующие основные шаги:  
  
1.  В меню «Файл» укажите пункт **Создать**, а затем выберите пункт **Проект**.  
  
     Выберите шаблон проекта **Скрипты служб Analysis Server** , а затем укажите имя и расположение для нового проекта.  
  
2.  Щелкните правой кнопкой мыши элемент **Соединения** , чтобы создать новое соединение в папке "Соединения" в проекте "Скрипты служб Analysis Server" в обозревателе решений.  
  
     Эта папка содержит строки подключения для экземпляров служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , в отношении которых могут выполняться скрипты, содержащиеся в проекте скриптов служб Analysis Server. В проекте скриптов сервера анализа данных могут использоваться несколько соединений, и можно выбирать соединение, в отношении которого запускать скрипт, содержащийся в проекте, во время выполнения.  
  
3.  Щелкните правой кнопкой мыши элемент **Запросы** , чтобы создать скрипты многомерных выражений, расширений интеллектуального анализа данных и XML для аналитики (XMLA) в папке "Скрипты" проекта скриптов служб Analysis Server в обозревателе решений. Дополнительные сведения см. в статье [Script Administrative Tasks in Analysis Services](../script-administrative-tasks-in-analysis-services.md).  
  
4.  Щелкните правой кнопкой мыши проект, укажите пункт **Добавить**и выберите пункт **Существующий элемент** , чтобы добавить прочие файлы, например текстовые файлы, содержащие примечания к проекту, в папке **Разное** проекта "Скрипты служб Analysis Server" в обозревателе решений. Эти файлы не учитываются средой [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="file-types"></a>Типы файлов  
 Решение в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] может содержать несколько типов файлов, в зависимости от того, какие проекты включены в решение и какие элементы включены в каждый из проектов этого решения. Дополнительные сведения о типах файлов для решений в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]см. в разделе [Файлы для управления решениями и проектами](../../ssms/solution/files-that-manage-solutions-and-projects.md). Обычно файлы для каждого проекта в решении среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] хранятся в папке решения, в отдельной папке для каждого проекта.  
  
 Папка проекта для проекта сценариев сервера анализа данных может содержать типы файлов, список которых приведен в следующей таблице.  
  
|Тип файла|Описание|  
|---------------|-----------------|  
|Файл определения проекта сценариев сервера анализа данных (SSMSASPROJ)|Содержит метаданные о папках, отображаемых в обозревателе решений, а также данные, указывающие, в каких папках должны отображаться файлы, включенные в проект.<br /><br /> Файл определения проекта также содержит метаданные для соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , содержащихся в проекте, а также метаданные, связывающие соединения с файлами скриптов, включенными в проект.|  
|Файл скрипта расширений интеллектуального анализа данных (DMX)|Содержит скрипт расширений интеллектуального анализа данных, включенный в проект.|  
|Файл скрипта многомерных выражений (MDX)|Содержит скрипт многомерных выражений, включенный в проект.|  
|Файл скрипта XML для аналитики (XMLA)|Содержит XMLA-скрипт, включенный в проект.|  
  
## <a name="analysis-services-templates"></a>Шаблоны служб Analysis Services  
 При добавлении новых сценариев многомерных выражений, расширений интеллектуального анализа данных или XML для аналитики в проект сценариев сервера анализа данных имеется возможность использования обозревателя шаблонов для определения размещения шаблонов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , представляющих собой сочетание стандартных сценариев или инструкций, демонстрирующих выполнение конкретного действия. Обозреватель шаблонов доступен в меню **Вид** и включает шаблоны для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]и [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Дополнительные сведения см. в статье [Use Analysis Services Templates in SQL Server Management Studio](use-analysis-services-templates-in-sql-server-management-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Создание многомерных моделей с помощью SQL Server Data Tools &#40;SSDT&#41;](../multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)   
 [Многомерные выражения &#40;многомерных Выражений&#41; ссылки](/sql/mdx/multidimensional-expressions-mdx-reference)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; ссылки](/sql/dmx/data-mining-extensions-dmx-reference)   
 [Язык сценариев Analysis Services &#40;ASSL&#41; ссылки](../scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [Язык сценариев Analysis Services &#40;ASSL&#41; ссылки](../scripting/analysis-services-scripting-language-assl-for-xmla.md)  
  
  
