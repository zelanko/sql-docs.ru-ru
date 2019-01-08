---
title: Развертывание Analysis Services Project | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 71948f2f20d764e74716f067f76f1b63268fdac2
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52537474"
---
# <a name="lesson-2-5---deploying-an-analysis-services-project"></a>Занятие 2 – 5-развертывание проекта служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

Чтобы просмотреть куб и данные измерения для объектов куба «Учебник по службам [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] » проекта «Учебник по службам [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] », необходимо развернуть проект на указанном экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , а затем выполнить обработку куба и его измерений. *Развертывание* [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] проекта создаются определенные объекты в экземпляре [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. При*обработке* объектов в экземпляре [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] данные из базовых источников данных копируются в объекты кубов. Дополнительные сведения см. в разделах [Развертывание проектов служб Analysis Services (среда SSDT)](../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md) и [Настройка свойств проекта служб Analysis Services (среда SSDT)](../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)создаются определенные объекты.  
  
На этой стадии процесса разработки развертывание куба обычно производится в экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] на сервере разработки. После завершения разработки проекта бизнес-аналитики обычно производится развертывание данных на рабочем сервере с помощью мастера развертывания служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Дополнительные сведения см. в разделах [Развертывание решений многомерных моделей](../analysis-services/multidimensional-models/multidimensional-model-solution-deployment.md) и [Развертывание решений модели с использованием мастера развертывания](../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md).  
  
Для выполнения следующей задачи необходимо проверить свойства развертывания проекта Tutorial служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , а затем развернуть его для локального экземпляра служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
### <a name="to-deploy-the-analysis-services-project"></a>Развертывание проекта служб Analysis Services  
  
1.  В обозревателе решений щелкните правой кнопкой мыши проект **Учебник по службам Analysis Services** и выберите пункт **Свойства**.  
  
    Откроется диалоговое окно **Страницы свойств учебника по службам Analysis Services** , содержащее свойства конфигурации Active(Development). Можно определить несколько конфигураций, каждая из которых будет иметь собственные значения свойств. Например, разработчик может по-разному настроить один и тот же проект для его развертывания на разных компьютерах с разными свойствами среды разработки, такими как имена баз данных или свойства обработки. Обратите внимание на значение свойства **Путь вывода** . Это свойство указывает расположение, в котором сохраняются XMLA-скрипты развертывания проекта при его сборке. Это скрипты, используемые для развертывания содержащихся в проекте объектов для экземпляра служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
2.  В узле **Свойства конфигурации** на левой панели щелкните элемент **Развертывание**.  
  
    Просмотрите свойства развертывания проекта. По умолчанию шаблон проекта служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] настроен таким образом, что выполняется последовательное развертывание всех проектов служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] для указанного по умолчанию экземпляра служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] на локальном компьютере, создается база данных [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] с именем проекта, а также выполняется обработка объектов с параметрами по умолчанию после завершения развертывания. Дополнительные сведения см. в разделах [Настройка свойств проекта служб Analysis Services (среда SSDT)](../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)создаются определенные объекты.  
  
    > [!NOTE]  
    > Если вы хотите развернуть проект в именованном экземпляре [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] на локальном компьютере или к экземпляру на удаленном сервере, изменить **Server** имя свойства, к соответствующему экземпляру, такие как \<  *ServerName**>\\<** InstanceName ** >*.  
  
3.  Нажмите кнопку **ОК**.  
  
4.  В обозревателе решений щелкните правой кнопкой мыши проект **Учебник Analysis Services** и выберите пункт **Развертывание**. Возможно, потребуется подождать.  
  
    > [!NOTE]  
    > Если при развертывании возникают ошибки, проверьте разрешения на базу данных с помощью среды SQL Server Management Studio. У учетной записи, указанной для соединения с источником данных, должно быть имя входа в экземпляр SQL Server. Дважды щелкните имя пользователя для просмотра свойств сопоставления пользователей. Эта учетная запись должна иметь разрешения db_datareader для базы данных **AdventureWorksDW2012** .  
  
    [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] собирается и развертывается проект учебника по службам [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в указанном экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] с использованием скрипта развертывания. Ход выполнения развертывания отображается в двух окнах: **вывода** окна и **выполнение развертывания — учебник по службам Analysis Services** окна.  
  
    Откройте окно вывода, если необходимо, выбрав пункт **Вывод** в меню **Вид** . В окне **Вывод** отображается общий ход выполнения развертывания. **Выполнение развертывания — учебник по службам Analysis Services** окна отображаются подробные сведения о каждом шаге, выполняемом в процессе развертывания. Дополнительные сведения см. в разделах [Построение проектов служб Analysis Services (среда SSDT)](../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md) и [Развертывание проектов служб Analysis Services (среда SSDT)](../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md).  
  
5.  Просмотрите содержимое **вывода** окна и **выполнение развертывания — учебник по службам Analysis Services** окно, чтобы убедиться, что куб построен, развернут и обработан без ошибок.  
  
6.  Чтобы скрыть окно **Выполнение развертывания — учебник по службам Analysis Services** , щелкните значок **Автоматически скрывать** (значок похож на канцелярскую кнопку) на панели инструментов этого окна.  
  
7.  Чтобы скрыть окно **Вывод** , щелкните значок **Автоматически скрывать** на панели инструментов этого окна.  
  
Развертывание куба учебника по службам [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] для локального экземпляра [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]и его обработка успешно завершены.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Просмотр куба](../analysis-services/lesson-2-6-browsing-the-cube.md)  
  
## <a name="see-also"></a>См. также  
[Развертывание проектов служб Analysis Services (среда SSDT)](../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
[Настройка свойств проекта служб Analysis Services (среда SSDT)](../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)  
  
  
  
