---
title: "Развертывание решений модели с использованием XML для Аналитики | Документы Microsoft"
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
- XML scripts [Analysis Services]
- scripts [Analysis Services], deployment
- deploying [Analysis Services], XML scripts
- Analysis Services deployments, XML scripts
ms.assetid: a8cb1837-fcac-4730-bea4-a72cf94d9f7c
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cb6e34a647d2c241e1a968077c989d17ad5c4e19
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="deploy-model-solutions-using-xmla"></a>Развертывание решений модели с помощью XMLA
  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]параметр **Используя CREATE** команды **Создать скрипт для базы данных** создает XML-скрипт всей базы данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или одного из составляющих ее объектов. Получившийся в результате скрипт затем можно запускать на другом компьютере для повторного создания схемы (метаданных) базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Скрипт формирует всю базу данных, а механизм добавочного обновления уже развернутых объектов при использовании скрипта отсутствует. После выполнения скрипта и развертывания базы данных вновь созданную базу необходимо обработать до ее просмотра пользователями.  
  
 Дополнительные сведения о команде **Создать скрипт для базы данных** см. в разделе [Документирование и работа со скриптами в базе данных служб Analysis Services](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md).  
  
## <a name="modifying-object-properties-in-the-xml-script"></a>Изменение свойств объектов в XML-скрипте  
 При использовании команды **Создать скрипт для базы данных** нельзя изменять определенные свойства (например, имя базы данных, строки соединений с источниками данных и параметры безопасности) объектов базы данных. Эти свойства необходимо либо изменить вручную в скрипте после его формирования, либо изменить в развернутой базе данных после выполнения скрипта.  
  
> [!IMPORTANT]  
>  XML-скрипт не будет содержать пароль, если он указан в строке соединения для источника данных или для олицетворения. Поскольку в данном скрипте пароль требуется для обработки, его нужно добавить вручную в скрипт перед запуском либо добавить в XML после выполнения скрипта.  
  
## <a name="see-also"></a>См. также  
 [Развертывание решений модели с использованием мастера развертывания](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)   
 [Синхронизация баз данных служб Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)  
  
  
