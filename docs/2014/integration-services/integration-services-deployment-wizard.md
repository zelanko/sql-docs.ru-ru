---
title: Мастер развертывания Integration Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 721953c31a44a2ea02f480c9830e6347adfd4eb3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66058011"
---
# <a name="integration-services-deployment-wizard"></a>Мастер развертывания служб Integration Services
  Мастер развертывания служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] разворачивает проекты в каталоге SSISDB на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью модели развертывания проектов.  
  
 Чтобы запустить мастер [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] развертывания из открытого проекта в, в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]меню **проект** выберите пункт **развернуть** . Чтобы [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]запустить мастер в, разверните узел **Integration Services каталоги** > **SSISDB** в обозревателе объектов, щелкните правой кнопкой мыши папку **проекты** и выберите пункт **развернуть проект**.  
  
 Мастер состоит из следующих четырех шагов. Нажмите кнопку **Далее** , чтобы перейти к следующему шагу или **назад** , чтобы вернуться к предыдущему шагу.  
  
1.  **Выберите источник** — выберите [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] проект, который требуется развернуть.  
  
2.  **Выберите назначение** — выберите назначение проекта.  
  
3.  **Просмотр** . отображает параметры.  
  
4.  **Развертывание/результаты** — развертывает проект и отображает результаты.  
  
## <a name="select-source"></a>Выбор источника  
 Чтобы развернуть созданный файл развертывания проекта, выберите **файл развертывания проекта** и введите путь к ISPAC-файлу или нажмите кнопку **Обзор** , чтобы найти его в папке [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проекта. Для развертывания проекта, который находится в каталоге служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , выберите **Каталог служб Integration Services**, а затем введите имя сервера и путь к проекту в каталоге.  
  
 Если мастер запускается в среде [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], по умолчанию в качестве источника выбирается открытый проект, а этот шаг пропускается. Чтобы вернуться к этому шагу и выбрать другой источник, нажмите кнопку **назад** или выберите **источник** на левой панели.  
  
## <a name="select-destination"></a>Выбор назначения  
 Для выбора папки назначения проекта в каталоге [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] введите экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или нажмите кнопку **Обзор** , чтобы осуществить выбор из списка серверов. Введите путь к проекту в SSISDB или нажмите кнопку **Обзор** , чтобы произвести выбор.  
  
 Если мастер запускается в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], по умолчанию мастер выбирает подключенный экземпляр сервера и вводит путь к выбранном проекту. Эти значения вы можете изменить для развертывания проекта в другое местоположение.  
  
## <a name="review"></a>Просмотр  
 Мастер позволяет просмотреть выбранные параметры перед развертыванием проекта. Вы можете изменить выбранные параметры, нажав кнопку **Назад**или кнопку любого из шагов на левой панели.  
  
## <a name="deployresults"></a>Развертывание/результаты  
 При нажатии кнопки **развернуть** на странице **Просмотр** проект развертывается, а на странице **результаты** отображается успех или неудача каждого действия. Если действие не выполнено, нажмите кнопку **Ошибка** в столбце **Результат** для отображения описания ошибки. Нажмите кнопку **сохранить отчет...** , чтобы сохранить результаты в XML-файл.  
  
 Чтобы выйти из мастера, нажмите кнопку **Закрыть**.  
  
## <a name="see-also"></a>См. также  
 [Развертывание проектов на сервере Integration Services](../../2014/integration-services/deploy-projects-to-integration-services-server.md)   
 [Развертывание проектов и пакетов](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
