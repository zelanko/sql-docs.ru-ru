---
title: Создание анализа служб проекта (учебник интеллектуального анализа данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 784c0401-0358-4117-9c85-4e8220ce71d9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e3c88894ee271e9b96e98e25dc14e62bfc0361ca
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048334"
---
# <a name="creating-an-analysis-services-project-basic-data-mining-tutorial"></a>Создание проекта служб Analysis Services (учебник по интеллектуальному анализу данных — начальный уровень)
  Каждый [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] проекта определяет объекты в одной [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базы данных. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Базы данных может содержать множество различных типов объектов  
  
-   Многомерные модели (кубы)  
  
-   Структуры и модели интеллектуального анализа данных  
  
-   Вспомогательные объекты, такие как источники данных, представления источников данных и пользовательские сборки  
  
 Обратите внимание, что для интеллектуального анализа данных куб **не** требуется. Если необходимо выполнить интеллектуальный анализ данных на уже существующем кубе, следует добавить модели интеллектуального анализа данных в тот проект, который использовался для построения куба. Тем не менее в большинстве случаев можно строить модели на источниках реляционных данных, таких как хранилище данных, и обеспечивать более высокую производительность, не прибегая к использованию куба.  
  
 В этом учебнике будет использоваться в реляционную базу данных, [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], как источник данных. Вы развернете все объекты интеллектуального анализа данных для [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базу данных с именем `BasicDataMining`, используемой только для интеллектуального анализа данных.  
  
 По умолчанию [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] использует **localhost** для новых проектов экземпляр. Если необходимо использовать именованный экземпляр или другой сервер, то сначала создайте и откройте проект, а затем измените имя экземпляра.  
  
 Дополнительные сведения о [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] проектов, см. в разделе [Создание проекта служб Analysis Services](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md).  
  
### <a name="to-create-an-analysis-services-project"></a>Создание проекта служб Analysis Services  
  
1.  Откройте [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  В меню **Файл** последовательно выберите команды **Создать**и **Проект**.  
  
3.  Убедитесь в том, что выбраны **Проекты бизнес-аналитики** на панели **Типы проектов** .  
  
4.  На панели **Шаблоны** выберите **Проект многомерных данных и интеллектуального анализа данных служб Analysis Services**.  
  
5.  В **имя** окне нового проекта имя `BasicDataMining`.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored"></a>Изменение экземпляра, на котором хранятся объекты интеллектуального анализа данных  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]на **проекта** меню, выберите **свойства**.  
  
2.  В левой части панели **Страницы свойств** в области **Свойства настройки**щелкните элемент **Развертывание**.  
  
3.  В правой части панели **Страницы свойств** на панели **Целевой объект**, убедитесь в том, что именем **сервера** является **localhost**. Если используется другой экземпляр, введите имя этого экземпляра. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Создание источника данных &#40;учебник интеллектуального анализа данных&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Построение проектов служб Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)   
 [Создание проекта служб Analysis Services (среда SSDT)](../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  
