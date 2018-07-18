---
title: Создание источника данных (учебник интеллектуального анализа данных) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d7107c32-69ed-49a8-9b6e-32753eebf42c
caps.latest.revision: 51
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ca60870200473b80f114e17db2222d18f5219fba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312724"
---
# <a name="creating-a-data-source-basic-data-mining-tutorial"></a>Создание источника данных (учебник по интеллектуальному анализу данных — начальный уровень)
  Объект *источника данных* является подключение к данным, которая сохраняется и управляется из проекта и развернуть ваш [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базы данных. Источник данных содержит, кроме обязательных свойств соединения, имя сервера и базы данных, где находится этот источник.  
  
> [!IMPORTANT]  
>  Имя базы данных [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]. Если вы еще не установили эту базу данных, см. в разделе [образцы баз данных SQL Microsoft](http://go.microsoft.com/fwlink/?LinkId=88417) страницы.  
  
### <a name="to-create-a-data-source"></a>Создание источника данных  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **источников данных** папку и выберите **новый источник данных**.  
  
2.  На **Добро пожаловать в мастер источников данных** щелкните **Далее**.  
  
3.  На **Выбор метода определения соединения** щелкните **New** для добавления подключения к [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] базы данных.  
  
4.  В **поставщика** в списке **диспетчер соединений**выберите **Native OLE DB\Собственный Server клиент SQL 11.0**.  
  
5.  В **имя_сервера** введите или выберите имя сервера, на котором установлен [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].  
  
     Например, введите **localhost** Если база данных размещается на локальном сервере.  
  
6.  В **Войдите на сервер** группы выберите **использовать проверку подлинности Windows**.  
  
    > [!IMPORTANT]  
    >  Во всех случаях, где возможно, следует использовать проверку подлинности Windows, которая обеспечивает более защищенный метод проверки подлинности, чем проверка подлинности SQL Server. Однако проверка подлинности SQL Server обеспечивается для поддержки обратной совместимости. Дополнительные сведения о методах проверки подлинности см. в разделе [Настройка компонента Database Engine - Провизионирование учетных записей](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md).  
  
7.  В **выберите или введите имя базы данных** выберите [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] и нажмите кнопку **ОК**.  
  
8.  Нажмите кнопку **Далее**.  
  
9. На **сведения об олицетворении** щелкните **учетной записи службы,**, а затем нажмите кнопку **Далее**.  
  
     На **завершение работы мастера** странице, обратите внимание, что, по умолчанию источник данных называется Adventure Works DW 2012.  
  
10. Нажмите кнопку **Готово**.  
  
     Новый источник данных Adventure Works DW 2012 появится в **источников данных** папку в обозревателе решений.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Создание данных представление источника &#40;учебник интеллектуального анализа данных&#41;](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Предыдущая задача занятия  
 [Создание анализа служб проекта &#40;учебник интеллектуального анализа данных&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Создание источника данных (многомерные службы SSAS)](../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md)   
 [Определение источника данных](../analysis-services/lesson-1-2-defining-a-data-source.md)   
 [Задание параметров олицетворения &#40;службы SSAS — многомерные&#41;](../analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional.md)  
  
  
