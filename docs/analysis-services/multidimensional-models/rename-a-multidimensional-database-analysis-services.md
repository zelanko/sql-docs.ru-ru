---
title: "Переименование многомерной базы данных (службы Analysis Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- renaming databases
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3d822aff82a3f38bd4dd8fdec69a87792e8d56a5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="rename-a-multidimensional-database-analysis-services"></a>Переименование многомерной базы данных (службы Analysis Services)
  Способ изменения имени базы данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] зависит от способа подключения к базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Чтобы изменить имя существующей базы данных, необходимо подключиться к ней в режиме в сети. Чтобы изменить имя базы данных, в которой будут создаваться экземпляры объектов проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , необходимо подключиться к ней в режиме проекта.  
  
### <a name="to-change-the-database-name-in-online-mode"></a>Изменение имени базы данных в режиме в сети  
  
1.  Используя среду [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], подключитесь напрямую к базе данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  В обозревателе решений щелкните правой кнопкой мыши базу данных, после чего выберите пункт **Изменить базу данных**.  
  
3.  В текстовом поле **Имя базы данных** измените имя базы данных.  
  
4.  На панели инструментов щелкните **Сохранить** или **Сохранить все** , щелкните **Сохранить выбранные элементы** или **Сохранить все** в меню **Файл** , или закройте **Конструктор баз данных** и при появлении запроса нажмите кнопку **Сохранить** .  
  
     Имя базы данных обновится в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , а объекты базы данных обновятся в обозревателе решений.  
  
### <a name="to-change-the-database-name-in-project-mode"></a>Изменение имени базы данных в проектном режиме  
  
1.  Откройте проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  В обозревателе решений щелкните правой кнопкой мыши проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Страницы свойств** в разделе **Свойства конфигурации** выберите пункт **Развертывание** .  
  
4.  Измените свойство **База данных** на новое имя базы данных.  
  
     В следующий раз при развертывании проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] он будет развернут с новым именем базы данных. Если база данных уже существует, она будет перезаписана.  
  
### <a name="to-change-the-database-name-using-sql-server-management-studio"></a>Изменение имени базы данных с помощью среды SQL Server Management Studio.  
  
-   Щелкните правой кнопкой базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и измените свойство "Имя".  
  
## <a name="see-also"></a>См. также  
 [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Задание свойств многомерной базы данных &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/set-multidimensional-database-properties-analysis-services.md)   
 [Настройка свойств проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)   
 [Развертывание проектов служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
  

