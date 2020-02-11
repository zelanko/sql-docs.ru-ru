---
title: Построение модели (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8ae26ec3-c5d5-4c4f-a810-2951a7454439
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ee3473ba16ad3a03a95065aea94888654db53187
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479338"
---
# <a name="building-a-model-mds-add-in-for-excel"></a>Построение модели (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]администраторы могут выполнять сокращенный набор административных функций, доступных в веб-приложении [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
 Администраторы могут выполнять следующие задачи по созданию моделей в [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] :  
  
-   Создание сущностей. Дополнительные сведения о сущностях см. в разделе [Entities &#40;Master Data Services&#41;](../entities-master-data-services.md).  
  
-   Создание атрибутов всех типов, включая атрибуты на основе домена. Дополнительные сведения об атрибутах см. в разделах [Attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md) и [Domain-Based Attributes &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md).  
  
 Администратор должен создавать модель с помощью веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или веб-службы. Затем с помощью [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] можно создавать сущности и атрибуты в модели. Дополнительные сведения об объектах модели см. в разделе [Models &#40;Master Data Services&#41;](../models-master-data-services.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
 Однако большинство административных задач все равно необходимо выполнять в веб-приложении [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или с помощью веб-службы. В следующей таблице показаны средства, с помощью которых администраторы могут выполнять задачи в MDS.  
  
|Описание задачи|Инструмент|Раздел|  
|----------------------|----------|-----------|  
|Создание моделей.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]веб-приложение или веб-служба|[Создание &#40;модели Master Data Services&#41;](../create-a-model-master-data-services.md)|  
|Создание сущности.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]веб-приложение, веб-служба или[!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[Создание сущности &#40;надстройка MDS для Excel&#41;](create-an-entity-mds-add-in-for-excel.md)|  
|Создание атрибута на основе домена.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]веб-приложение, веб-служба или[!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[Создание атрибута на основе домена &#40;надстройка MDS для Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|Создание групп атрибутов.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]веб-приложение или веб-служба|[Создание группы атрибутов &#40;Master Data Services&#41;](../create-an-attribute-group-master-data-services.md)|  
|Создание бизнес-правил.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]веб-приложение или веб-служба|[Создание и публикация бизнес-правила &#40;Master Data Services&#41;](../create-and-publish-a-business-rule-master-data-services.md)|  
|Создание представлений подписки.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]веб-приложение или веб-служба|[Создание представления подписки &#40;Master Data Services&#41;](../create-a-subscription-view-to-export-data-master-data-services.md)|  
|Создание иерархий.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]веб-приложение или веб-служба|[Создание производной иерархии &#40;Master Data Services&#41;](../create-a-derived-hierarchy-master-data-services.md)<br /><br /> [Создание явной иерархии &#40;Master Data Services&#41;](../create-an-explicit-hierarchy-master-data-services.md)|  
|Создание коллекций.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]веб-приложение или веб-служба|[Создание Master Data Services &#40;коллекции&#41;](../create-a-collection-master-data-services.md)|  
|Создание версий данных.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]веб-приложение или веб-служба|[Блокировка &#40;версии Master Data Services&#41;](../lock-a-version-master-data-services.md)|  
|Развертывание моделей.|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , веб-служба или средство MDSModelDeploy.|[Создание пакета развертывания модели при помощи MDSModelDeploy](../create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Модели &#40;Master Data Services&#41;](../models-master-data-services.md)  
  
-   [Сущности &#40;Master Data Services&#41;](../entities-master-data-services.md)  
  
-   [Master Data Services &#40;атрибутов&#41;](../attributes-master-data-services.md)  
  
-   [Атрибуты на основе домена &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md)  
  
-   [Группы атрибутов &#40;Master Data Services&#41;](../attribute-groups-master-data-services.md)  
  
-   [Бизнес-правила &#40;Master Data Services&#41;](../business-rules-master-data-services.md)  
  
-   [Экспорт Master Data Services &#40;данных&#41;](../overview-exporting-data-master-data-services.md)  
  
-   [Иерархии &#40;Master Data Services&#41;](../hierarchies-master-data-services.md)  
  
-   [&#40;коллекций Master Data Services&#41;](../collections-master-data-services.md)  
  
-   [Версии &#40;Master Data Services&#41;](../versions-master-data-services.md)  
  
-   [Master Data Services &#40;безопасности&#41;](../security-master-data-services.md)  
  
-   [Развертывание моделей &#40;Master Data Services&#41;](../deploying-models-master-data-services.md)  
  
  
