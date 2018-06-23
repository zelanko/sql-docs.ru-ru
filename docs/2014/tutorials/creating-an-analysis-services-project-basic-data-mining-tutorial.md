---
title: Создание служб Analysis Services проекта (учебник по интеллектуальному анализу данных) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 784c0401-0358-4117-9c85-4e8220ce71d9
caps.latest.revision: 50
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d650feead984a358d169851fba246215a58b6d34
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312532"
---
# <a name="creating-an-analysis-services-project-basic-data-mining-tutorial"></a>Создание проекта служб Analysis Services (учебник по интеллектуальному анализу данных — начальный уровень)
  Каждый [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] проекта определяет объекты в одной [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базы данных. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Базы данных может содержать множество различных типов объектов  
  
-   Многомерные модели (кубы)  
  
-   Структуры и модели интеллектуального анализа данных  
  
-   Вспомогательные объекты, такие как источники данных, представления источников данных и пользовательские сборки  
  
 Обратите внимание, что для интеллектуального анализа данных куб **не** требуется. Если необходимо выполнить интеллектуальный анализ данных на уже существующем кубе, следует добавить модели интеллектуального анализа данных в тот проект, который использовался для построения куба. Тем не менее в большинстве случаев можно строить модели на источниках реляционных данных, таких как хранилище данных, и обеспечивать более высокую производительность, не прибегая к использованию куба.  
  
 В этом учебнике будет использоваться в реляционную базу данных, [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], как источник данных. Развернет все объекты интеллектуального анализа данных для [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базы данных с именем `BasicDataMining`, используемой только для интеллектуального анализа данных.  
  
 По умолчанию [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] использует **localhost** для новых проектов экземпляр. Если необходимо использовать именованный экземпляр или другой сервер, то сначала создайте и откройте проект, а затем измените имя экземпляра.  
  
 Дополнительные сведения о [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] проектов, в разделе [Создание проекта служб Analysis Services](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md).  
  
### <a name="to-create-an-analysis-services-project"></a>Создание проекта служб Analysis Services  
  
1.  Откройте [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  В меню **Файл** последовательно выберите команды **Создать**и **Проект**.  
  
3.  Убедитесь в том, что выбраны **Проекты бизнес-аналитики** на панели **Типы проектов** .  
  
4.  На панели **Шаблоны** выберите **Проект многомерных данных и интеллектуального анализа данных служб Analysis Services**.  
  
5.  В **имя** поле, введите имя нового проекта `BasicDataMining`.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored"></a>Изменение экземпляра, на котором хранятся объекты интеллектуального анализа данных  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]на **проекта** последовательно выберите пункты **свойства**.  
  
2.  В левой части панели **Страницы свойств** в области **Свойства настройки**щелкните элемент **Развертывание**.  
  
3.  В правой части панели **Страницы свойств** на панели **Целевой объект**, убедитесь в том, что именем **сервера** является **localhost**. Если используется другой экземпляр, введите имя этого экземпляра. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Создание источника данных &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Построение проектов служб Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)   
 [Создание проекта служб Analysis Services (среда SSDT)](../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  