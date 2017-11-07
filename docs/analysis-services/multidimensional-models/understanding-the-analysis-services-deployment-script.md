---
title: "Основные сведения о Analysis Services скрипт развертывания | Документы Microsoft"
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
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], scripts
- Analysis Services deployments, scripts
- scripts [Analysis Services], deployment
ms.assetid: a63ebee9-9848-48f1-82ad-64ecf2e47019
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1ccc1b2b2861a20de2f02bf118a5abcf14e8ea6b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="understanding-the-analysis-services-deployment-script"></a>Основные сведения о скрипте развертывания служб Analysis Services
  Скрипт развертывания XML для аналитики, сформированный мастером развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , состоит из двух частей.  
  
-   Первая часть скрипта содержит команды, необходимые для создания, изменения или удаления соответствующих объектов служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в целевой базе данных. По умолчанию входные файлы, сформированные проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , основываются на добавочном развертывании. В результате скрипт развертывания XML для аналитики влияет только на те объекты, которые были изменены или удалены.  
  
-   Вторая часть скрипта развертывания содержит команды, необходимые для обработки только тех объектов, которые были созданы или изменены на целевом сервере (параметр «Обработка по умолчанию») или для полной обработки целевой базы данных. Кроме того, можно выбрать, чтобы скрипт развертывания не содержал команд обработки.  
  
 Весь скрипт развертывания может выполняться в одной транзакции или в нескольких транзакциях. Если скрипт выполняется в нескольких транзакциях, то первая часть скрипта выполняется в виде одной транзакции, а каждый объект обрабатывается в собственной транзакции.  
  
> [!IMPORTANT]  
>  Мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывает объекты только в одну базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Он не осуществляет развертывание никаких объектов или данных уровня сервера.  
  
## <a name="see-also"></a>См. также  
 [Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [Основные сведения о входных файлах, применяемых для создания скрипта развертывания](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)  
  
  

