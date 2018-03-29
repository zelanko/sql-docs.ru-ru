---
title: Основные сведения о Analysis Services скрипт развертывания | Документы Microsoft
ms.custom: ''
ms.date: 03/27/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], scripts
- Analysis Services deployments, scripts
- scripts [Analysis Services], deployment
ms.assetid: a63ebee9-9848-48f1-82ad-64ecf2e47019
caps.latest.revision: ''
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e9615dcfffe4a36a00ff61e15c41e9ff39bb7bfb
ms.sourcegitcommit: d6881107b51e1afe09c2d8b88b98d075589377de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="understanding-the-analysis-services-deployment-script"></a>Основные сведения о скрипте развертывания служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Скрипт развертывания XML для аналитики, сформированный мастером развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , состоит из двух частей.  
  
-   Первая часть скрипта содержит команды, необходимые для создания, изменения или удаления соответствующих объектов служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в целевой базе данных. По умолчанию входные файлы, сформированные проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , основываются на добавочном развертывании. В результате скрипт развертывания XML для аналитики влияет только на те объекты, которые были изменены или удалены.  
  
-   Вторая часть скрипта развертывания содержит команды, необходимые для обработки только тех объектов, которые были созданы или изменены на целевом сервере (параметр «Обработка по умолчанию») или для полной обработки целевой базы данных. Кроме того, можно выбрать, чтобы скрипт развертывания не содержал команд обработки.  
  
 Весь скрипт развертывания может выполняться в одной транзакции или в нескольких транзакциях. Если скрипт выполняется в нескольких транзакциях, то первая часть скрипта выполняется в виде одной транзакции, а каждый объект обрабатывается в собственной транзакции.  
  
> [!IMPORTANT]  
>  Мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывает объекты только в одну базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Он не осуществляет развертывание никаких объектов или данных уровня сервера.  
  
## <a name="see-also"></a>См. также  
 [Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [Основные сведения о входных файлах, применяемых для создания скрипта развертывания](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)  
  
  
