---
title: Развертывание решений модели с помощью мастера развертывания | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cde312f2bfad67c6cfe61a9b8379973c1f59a56c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38004666"
---
# <a name="deploy-model-solutions-using-the-deployment-wizard"></a>Развертывание решений модели с использованием мастера развертывания
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Развертывания мастер использует файлы выходных данных JSON, созданные из [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта в качестве входных файлов. Эти входные файлы можно легко изменить для настройки развертывания проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Сформированный скрипт развертывания можно затем либо сразу запустить, либо сохранить и запустить позднее.  

> [!NOTE]
> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Программа мастера развертывания устанавливается вместе с [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) (SSMS). Убедитесь, что вы используете последнюю версию. Если выполняется из командной строки, по умолчанию последней версии мастера развертывания устанавливается в C:\Program Files (x86) \Microsoft SQL Server\140\Tools\Binn\ManagementStudio. 
  
 Развертывание можно выполнить при помощи мастера. Также можно автоматизировать развертывание или использовать функцию синхронизации. При больших размерах развернутой базы данных на целевых системах рекомендуется использовать секции. Создание и заполнение секций можно автоматизировать с помощью табличной модели объектов (TOM) языка Scriting табличной модели (TMSL) и объекты управления Analysis (AMO).  
  
> [!IMPORTANT]  
>  Ни выходные файлы, ни скрипт развертывания будет содержать идентификатор пользователя или пароль, если они указываются в строке подключения для источника данных или для олицетворения. Поскольку в данном сценарии они необходимы для обработки, добавьте их вручную. Если в ходе развертывания не выполнится обработка, то эти сведения для соединения и олицетворения при необходимости можно добавить после развертывания. Если в ходе развертывания выполнится обработка, то можно добавить эти сведения с помощью мастера или добавить их в скрипт развертывания после его сохранения.  
  
## <a name="in-this-section"></a>в этом разделе  
 В следующих подразделах рассматривается работа с мастером развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , входными файлами и скриптом развертывания:  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)|Содержит описание различных способов запуска мастера развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Основные сведения о входных файлах, применяемых для создания скрипта развертывания](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)|Содержит описание файлов, используемых мастером развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в качестве входных значений, содержимого каждого из таких файлов, а также содержит ссылки на подразделы, в которых описывается, как изменять значения в каждом из входных файлов.|  
|[Основные сведения о скрипте развертывания служб Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)|Содержит описание скрипта развертывания и его выполнения.|  
  
## <a name="see-also"></a>См. также  
 [Развертывание решений модели с помощью XMLA](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)   
 [Синхронизация баз данных служб Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)   
 [Основные сведения о входных файлах, применяемых для создания скрипта развертывания](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)   
 [Развертывание решений моделей с использованием программы развертывания](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)  
  
  
