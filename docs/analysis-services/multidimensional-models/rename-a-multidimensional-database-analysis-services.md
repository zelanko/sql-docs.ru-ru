---
title: Переименование многомерной базы данных (службы Analysis Services) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e894db8be928f3d4bb5c53b93ead85feae94128
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027111"
---
# <a name="rename-a-multidimensional-database-analysis-services"></a>Переименование многомерной базы данных (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
 [Задание свойств многомерной базы данных & #40; Службы Analysis Services & #41;](../../analysis-services/multidimensional-models/set-multidimensional-database-properties-analysis-services.md)   
 [Настройка свойств проекта служб Analysis Services & #40; SSDT & #41;](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)   
 [Развертывание проектов служб Analysis Services & #40; SSDT & #41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
  
