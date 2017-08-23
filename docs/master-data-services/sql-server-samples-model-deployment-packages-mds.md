---
title: "Примеры SQL Server: Модель развертывания пакетов (MDS) | Документы Microsoft"
ms.custom: 
ms.date: 07/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "службы master data services"
- "образец"
ms.assetid: 9b31b7b6-319b-4840-b67d-eb383e7762b1
caps.latest.revision: 21
author: sabotta
ms.author: carlasab
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d7a031ba18c6782cdd73ae31ef395bc2ecdcf102
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="sql-server-examples-model-deployment-packages-mds"></a>Примеры SQL Server: Пакеты развертывания модели (MDS)
  Примеры пакетов модели с данными входят в комплект установки [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. По умолчанию для этих файлы пакета находятся \<диска > \Program Files\Microsoft SQL Server\130\Master Data Services\Samples\Packages.  
  
 Инструкции по развертыванию образцов пакетов моделей см. в разделе [Развертывание образцов моделей и данных](../master-data-services/master-data-services-installation-and-configuration.md#deploySample). Вы можете развернуть эти образцы пакетов моделей с помощью [средства MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
> [!IMPORTANT]  
>  **Пример обновления в[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**  
>   
>  Образцы пакетов были обновлены для поддержки перечисленных ниже новых возможностей.  
>   
>  -   Отображение связей "многие ко многим".  
>   
>      Дополнительные сведения см. в разделе [Связь "многие ко многим" в образце модели](../master-data-services/show-many-to-many-relationships-in-derived-hierarchies-master-data-services.md#M2MSample).  

> -   Ограничение допустимых значений для атрибутов на основе домена.  
>   
>      Дополнительные сведения см. в разделе [Создание атрибута на основе домена (службы Master Data Services)](../master-data-services/create-a-domain-based-attribute-master-data-services.md).  
> -   Обязательное утверждение изменений сущности.  
>   
>      Дополнительные сведения см. в разделе [Требуется утверждение (службы Master Data Services)](../master-data-services/approval-required-master-data-services.md).  
> -   Использование операторов Not и Else в бизнес-правилах  
>   
>      Дополнительные сведения см. в разделе [Примеры бизнес-правил](../master-data-services/business-rule-examples-master-data-services.md).  
> -   Реализация пользовательского индекса  
>   
>      Дополнительные сведения см. в разделе [Пользовательский индекс (Master Data Services)](../master-data-services/custom-index-master-data-services.md).  
 

 
 В Master Data Services пакет находится в XML-файл, содержащий развертываемую структуру модели и при необходимости данные из модели. Пакеты модели используются для перемещения копий моделей из одной среды служб MDS в другую либо для создания моделей в существующей среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Развертывание пакета развертывания модели при помощи MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  

