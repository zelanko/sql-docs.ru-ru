---
title: Создание источника данных (учебник по интеллектуальному анализу данных — базовый) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d7107c32-69ed-49a8-9b6e-32753eebf42c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3f85320a99c901a2fd71c9048750825569559099
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "69494027"
---
# <a name="creating-a-data-source-basic-data-mining-tutorial"></a>Создание источника данных (учебник по интеллектуальному анализу данных — начальный уровень)
  *Источник данных* — это подключение к данным, которое сохраняется и управляется в проекте и развертывается в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] базе данных. Источник данных содержит, кроме обязательных свойств соединения, имя сервера и базы данных, где находится этот источник.  
  
> [!IMPORTANT]  
>  Имя базы данных [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]. Если вы еще не установили эту базу данных, см. страницу [образцов баз данных Microsoft SQL](https://go.microsoft.com/fwlink/?LinkId=88417) .  
  
### <a name="to-create-a-data-source"></a>Создание источника данных  
  
1.  В **Обозреватель решений**щелкните правой кнопкой мыши папку **Источники данных** и выберите пункт **создать источник данных**.  
  
2.  На странице **Мастер источников данных** нажмите кнопку **Далее**.  
  
3.  На странице **Выбор способа определения соединения** нажмите кнопку **создать** , чтобы добавить соединение с [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] базой данных.  
  
4.  В списке **поставщик** в **диспетчере соединений**выберите **собственный OLE DB \ Server Native Client 11,0**.  
  
5.  В поле **имя сервера** введите или выберите имя сервера, на котором установлен [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].  
  
     Например, введите **localhost** , если база данных размещена на локальном сервере.  
  
6.  В поле **Вход** в группу серверов выберите **использовать проверку подлинности Windows**.  
  
    > [!IMPORTANT]  
    >  Во всех случаях, где возможно, следует использовать проверку подлинности Windows, которая обеспечивает более защищенный метод проверки подлинности, чем проверка подлинности SQL Server. Однако проверка подлинности SQL Server обеспечивается для поддержки обратной совместимости. Дополнительные сведения о методах проверки подлинности см. в статье [Подготовка учетных записей в конфигурации ядро СУБД](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md).  
  
7.  В списке **выберите или введите имя базы данных** выберите [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] и нажмите кнопку **ОК**.  
  
8.  Щелкните **Далее**.  
  
9. На странице **сведения об олицетворении** щелкните **использовать учетную запись службы**, а затем нажмите кнопку **Далее**.  
  
     На странице **Завершение работы мастера** Обратите внимание, что по умолчанию источник данных называется Adventure Works DW 2012.  
  
10. Нажмите кнопку **Готово**.  
  
     Новый источник данных, Adventure Works DW 2012, появится в папке **Источники данных** в Обозреватель решений.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Создание представления источника данных &#40;учебник по основам интеллектуального анализа данных&#41;](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Предыдущая задача занятия  
 [Учебник по созданию Analysis Services проекта &#40;Basic Data Mining&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также:  
 [Создание источника данных &#40;многомерных&#41;SSAS](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional)   
 [Определение источника данных](../analysis-services/lesson-1-2-defining-a-data-source.md)   
 [Задание параметров олицетворения (службы SSAS — многомерные)](https://docs.microsoft.com/analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional)  
  
  
