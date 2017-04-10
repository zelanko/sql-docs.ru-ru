---
title: "Примеры: пакеты развертывания моделей (службы Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "02/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "службы master data services"
  - "образец"
ms.assetid: 9b31b7b6-319b-4840-b67d-eb383e7762b1
caps.latest.revision: 21
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 20
---
# Примеры: пакеты развертывания моделей (службы Master Data Services)
  Примеры пакетов модели с данными входят в комплект установки [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Расположение по умолчанию для файлов пакетов — \<диск>\Program Files\Microsoft SQL Server\130\Master Data Services\Samples\Packages.  
  
 Инструкции по развертыванию образцов пакетов моделей см. в разделе [Развертывание образцов моделей и данных](../sql-server/media/master-data-services.png#deploySample). Вы можете развернуть эти образцы пакетов моделей с помощью [средства MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
> [!IMPORTANT]  
>  **Примеры обновлений в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**  
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
  
 В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] пакет представляет собой XML-файл, содержащий развертываемую структуру модели и (необязательно) данные этой модели. Пакеты модели используются для перемещения копий моделей из одной среды служб MDS в другую либо для создания моделей в существующей среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
## См. также:  
 [Развертывание пакета развертывания модели при помощи MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  