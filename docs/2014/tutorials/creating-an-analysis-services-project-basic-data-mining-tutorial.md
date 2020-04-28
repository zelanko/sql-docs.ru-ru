---
title: Создание проекта Analysis Services (учебник по интеллектуальному анализу данных — базовый) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 784c0401-0358-4117-9c85-4e8220ce71d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a7fcece285a17e158fcdfe77ef00004afe637541
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "69494033"
---
# <a name="creating-an-analysis-services-project-basic-data-mining-tutorial"></a>Создание проекта служб Analysis Services (учебник по интеллектуальному анализу данных — начальный уровень)
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Каждый [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] проект определяет объекты в одной [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базе данных. База данных [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] может содержать множество различных типов объектов  
  
-   Многомерные модели (кубы)  
  
-   Структуры и модели интеллектуального анализа данных  
  
-   Вспомогательные объекты, такие как источники данных, представления источников данных и пользовательские сборки  
  
 Обратите внимание, что для интеллектуального анализа данных куб **не** требуется. Если необходимо выполнить интеллектуальный анализ данных на уже существующем кубе, следует добавить модели интеллектуального анализа данных в тот проект, который использовался для построения куба. Тем не менее в большинстве случаев можно строить модели на источниках реляционных данных, таких как хранилище данных, и обеспечивать более высокую производительность, не прибегая к использованию куба.  
  
 В этом учебнике в качестве источника данных используется реляционное хранилище данных [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]. Все объекты интеллектуального анализа данных будут развернуты в базе данных [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] с именем `BasicDataMining`, используемой только для интеллектуального анализа данных.  
  
 По умолчанию службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] используют для новых проектов экземпляр **localhost** . Если необходимо использовать именованный экземпляр или другой сервер, то сначала создайте и откройте проект, а затем измените имя экземпляра.  
  
 Дополнительные сведения о службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] см. в разделе [Creating an Analysis Services Project](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md).  
  
### <a name="to-create-an-analysis-services-project"></a>Создание проекта служб Analysis Services  
  
1.  Откройте [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  В меню **Файл** последовательно выберите команды **Создать**и **Проект**.  
  
3.  Убедитесь в том, что выбраны **Проекты бизнес-аналитики** на панели **Типы проектов** .  
  
4.  На панели **Шаблоны** выберите **Проект многомерных данных и интеллектуального анализа данных служб Analysis Services**.  
  
5.  В поле **имя** введите имя нового проекта `BasicDataMining`.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored"></a>Изменение экземпляра, на котором хранятся объекты интеллектуального анализа данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], в меню **Проект** выберите **Свойства**.  
  
2.  В левой части панели **Страницы свойств** в области **Свойства настройки**щелкните элемент **Развертывание**.  
  
3.  В правой части панели **Страницы свойств** на панели **Целевой объект**, убедитесь в том, что именем **сервера** является **localhost**. Если используется другой экземпляр, введите имя этого экземпляра. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Учебник по созданию источника данных &#40;Basic Data Mining&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также:  
 [Сборка Analysis Services проектов &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt)   
 [Создание проекта служб Analysis Services (среда SSDT)](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt)  
  
  
