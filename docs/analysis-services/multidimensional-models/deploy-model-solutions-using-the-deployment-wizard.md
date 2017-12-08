---
title: "Развертывание решений модели с помощью мастера развертывания | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Analysis Services Deployment Wizard
- deploying [Analysis Services], Analysis Services Deployment Wizard
- Analysis Services deployments, Analysis Services Deployment Wizard
- Analysis Services Deployment Wizard, about Analysis Services Deployment Wizard
ms.assetid: ff711e8e-971c-43ba-b479-effc034af4a4
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 78caf216358830821b0bc2c5ce212415925d52f8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="deploy-model-solutions-using-the-deployment-wizard"></a>Развертывание решений модели с использованием мастера развертывания
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Развертывания мастер использует JSON выходные файлы, созданные из [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта в качестве входных файлов. Эти входные файлы можно легко изменить для настройки развертывания проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Сформированный скрипт развертывания можно затем либо сразу запустить, либо сохранить и запустить позднее.  
  
 Развертывание можно выполнить при помощи мастера. Также можно автоматизировать развертывание или использовать функцию синхронизации. При больших размерах развернутой базы данных на целевых системах рекомендуется использовать секции. Также создание и заполнение секций можно автоматизировать при помощи объектов AMO.  
  
> [!IMPORTANT]  
>  Выходные файлы, ни скрипт развертывания будет содержать идентификатор пользователя или пароль, если они вводились в строке подключения для источника данных или для олицетворения. Поскольку в данном сценарии они необходимы для обработки, добавьте их вручную. Если в ходе развертывания не выполнится обработка, то эти сведения для соединения и олицетворения при необходимости можно добавить после развертывания. Если в ходе развертывания выполнится обработка, то можно добавить эти сведения с помощью мастера или добавить их в скрипт развертывания после его сохранения.  
  
## <a name="in-this-section"></a>В этом разделе  
 В следующих подразделах рассматривается работа с мастером развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , входными файлами и скриптом развертывания:  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)|Содержит описание различных способов запуска мастера развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Основные сведения о входных файлах, применяемых для создания скрипта развертывания](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)|Содержит описание файлов, используемых мастером развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в качестве входных значений, содержимого каждого из таких файлов, а также содержит ссылки на подразделы, в которых описывается, как изменять значения в каждом из входных файлов.|  
|[Основные сведения о скрипте развертывания служб Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)|Содержит описание скрипта развертывания и его выполнения.|  
  
## <a name="see-also"></a>См. также:  
 [Развертывание решений модели с помощью XMLA](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)   
 [Синхронизация баз данных служб Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)   
 [Основные сведения о входных файлах, применяемых для создания скрипта развертывания](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)   
 [Развертывание решений моделей с использованием программы развертывания](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)  
  
  
