---
title: Мастер развертывания служб интеграции | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 60bc9f05f7a00075efbda2972cf78d9d169c55d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36094599"
---
# <a name="integration-services-deployment-wizard"></a>Мастер развертывания служб Integration Services
  Мастер развертывания служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] разворачивает проекты в каталоге SSISDB на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью модели развертывания проектов.  
  
 Чтобы запустить [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] мастер развертывания из проекта, открытого в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]выберите **развернуть** из **проекта** меню. Чтобы запустить мастер [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], разверните **каталоги служб Integration Services** > **SSISDB** узел в обозревателе объектов щелкните правой кнопкой мыши **проекты** папки, а затем щелкните **развернуть проект**.  
  
 Мастер состоит из следующих четырех шагов. Нажмите кнопку **Далее** для перехода к следующему шагу или **Назад** для возврата к предыдущему шагу.  
  
1.  **Выберите источник** — выберите [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] проект, который вы хотите развернуть.  
  
2.  **Выбор места назначения** — выберите назначение проекта.  
  
3.  **Просмотрите** — отображает выбранные элементы.  
  
4.  **Развертывание/результаты** — развертывает проект и отображает результаты.  
  
## <a name="select-source"></a>Выбор источника  
 Чтобы развернуть созданный файл развертывания проекта, выберите **файл развертывания проекта** и введите путь к файлу ispac или нажмите кнопку **Обзор** найти его в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] папки проекта. Для развертывания проекта, который находится в каталоге служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , выберите **Каталог служб Integration Services**, а затем введите имя сервера и путь к проекту в каталоге.  
  
 Если мастер запускается в среде [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], по умолчанию в качестве источника выбирается открытый проект, а этот шаг пропускается. Чтобы вернуться к этому шагу и выбору другого источника, нажмите кнопку **Назад** или нажмите кнопку **Выбор источника** в левой области.  
  
## <a name="select-destination"></a>Выбор назначения  
 Для выбора папки назначения проекта в каталоге [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] введите экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или нажмите кнопку **Обзор** , чтобы осуществить выбор из списка серверов. Введите путь к проекту в SSISDB или нажмите кнопку **Обзор** , чтобы произвести выбор.  
  
 Если мастер запускается в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], по умолчанию мастер выбирает подключенный экземпляр сервера и вводит путь к выбранном проекту. Эти значения вы можете изменить для развертывания проекта в другое местоположение.  
  
## <a name="review"></a>Просмотр  
 Мастер позволяет просмотреть выбранные параметры перед развертыванием проекта. Вы можете изменить выбранные параметры, нажав кнопку **Назад**или кнопку любого из шагов на левой панели.  
  
## <a name="deployresults"></a>Развертывание/результаты  
 При нажатии кнопки **развернуть** из **проверки** развертывания проекта и **результатов** страницы отображается состояние каждого действия. Если действие не выполнено, нажмите кнопку **Ошибка** в столбце **Результат** для отображения описания ошибки. Нажмите кнопку **сохранить отчет...**  для сохранения результатов в XML-файл.  
  
 Нажмите кнопку **Закрыть**, чтобы выйти из мастера.  
  
## <a name="see-also"></a>См. также  
 [Развертывание проектов на сервере служб Integration Services](../../2014/integration-services/deploy-projects-to-integration-services-server.md)   
 [Развертывание проектов и пакетов](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  