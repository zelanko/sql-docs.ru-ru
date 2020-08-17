---
description: 'Примеры SQL Server: пакеты развертывания моделей (MDS)'
title: Примеры пакетов развертывания модели
ms.custom: ''
ms.date: 07/28/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
keywords:
- службы master data services
- sample
ms.assetid: 9b31b7b6-319b-4840-b67d-eb383e7762b1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 70375fd359e56081267f2478a582281d96c253eb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88342380"
---
# <a name="sql-server-examples-model-deployment-packages-mds"></a>Примеры SQL Server: пакеты развертывания моделей (MDS)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Примеры пакетов модели с данными входят в комплект установки [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. По умолчанию эти файлы пакета находятся в папке \<drive> \Program FILES\MICROSOFT SQL Server\130\master Data Data Services\Samples\Packages.  
  
 Инструкции по развертыванию образцов пакетов моделей см. в разделе [Развертывание образцов моделей и данных](../master-data-services/master-data-services-installation-and-configuration.md#deploySample). Вы можете развернуть эти образцы пакетов моделей с помощью [средства MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
> [!IMPORTANT]
>  **Обновления примеров в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**  
> 
>  Образцы пакетов были обновлены для поддержки перечисленных ниже новых возможностей.  
> 
>  -   Отображение связей "многие ко многим".  
> 
>      Дополнительные сведения см. в разделе [Связь "многие ко многим" в образце модели](../master-data-services/show-many-to-many-relationships-in-derived-hierarchies-master-data-services.md#M2MSample).  
> 
> -   Ограничение допустимых значений для атрибутов на основе домена.  
> 
>      Дополнительные сведения см. в разделе [Создание атрибута на основе домена (службы Master Data Services)](../master-data-services/create-a-domain-based-attribute-master-data-services.md).  
> -   Обязательное утверждение изменений сущности.  
> 
>      Дополнительные сведения см. в разделе [утверждение Required &#40;Master Data Services&#41;](../master-data-services/approval-required-master-data-services.md).  
> -   Использование операторов Not и Else в бизнес-правилах  
> 
>      Дополнительные сведения см. в разделе [Примеры бизнес-правил](../master-data-services/business-rule-examples-master-data-services.md).  
> -   Реализация пользовательского индекса  
> 
>      Дополнительные сведения см. в разделе [Пользовательский индекс (Master Data Services)](../master-data-services/custom-index-master-data-services.md).  
 

 
 В службах Master Data Services пакет представляет собой XML-файл, содержащий развертываемую структуру модели и (необязательно) данные этой модели. Пакеты модели используются для перемещения копий моделей из одной среды служб MDS в другую либо для создания моделей в существующей среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Развертывание пакета развертывания модели при помощи MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  
