---
title: Построение модели (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8ae26ec3-c5d5-4c4f-a810-2951a7454439
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 0076abb28b486627d12c177d7f301b274239225c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62764663"
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
|Создание моделей.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или веб-служба|[Создание модели (службы Master Data Services)](../create-a-model-master-data-services.md)|  
|Создание сущности.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , веб-служба или [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[Создание сущности (надстройка MDS для Excel)](create-an-entity-mds-add-in-for-excel.md)|  
|Создание атрибута на основе домена.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , веб-служба или [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[Создание атрибута на основе домена (надстройка MDS для Excel)](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|Создание групп атрибутов.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или веб-служба|[Создание группы атрибутов (службы Master Data Services)](../create-an-attribute-group-master-data-services.md)|  
|Создание бизнес-правил.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или веб-служба|[Создание и публикация бизнес-правила (службы Master Data Services)](../create-and-publish-a-business-rule-master-data-services.md)|  
|Создание представлений подписки.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или веб-служба|[Создание представления подписки &#40;службы Master Data Services&#41;](../create-a-subscription-view-to-export-data-master-data-services.md)|  
|Создание иерархий.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или веб-служба|[Создание производной иерархии (службы Master Data Services)](../create-a-derived-hierarchy-master-data-services.md)<br /><br /> [Создание явной иерархии (службы Master Data Services)](../create-an-explicit-hierarchy-master-data-services.md)|  
|Создание коллекций.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или веб-служба|[Создание коллекции (службы Master Data Services)](../create-a-collection-master-data-services.md)|  
|Создание версий данных.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или веб-служба|[Блокировка версии (службы Master Data Services)](../lock-a-version-master-data-services.md)|  
|Развертывание моделей.|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , веб-служба или средство MDSModelDeploy.|[Создание пакета развертывания модели при помощи MDSModelDeploy](../create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Модели (службы Master Data Services)](../models-master-data-services.md)  
  
-   [Сущности (службы Master Data Services)](../entities-master-data-services.md)  
  
-   [Атрибуты (службы Master Data Services)](../attributes-master-data-services.md)  
  
-   [Атрибуты на основе домена (службы Master Data Services)](../domain-based-attributes-master-data-services.md)  
  
-   [Группы атрибутов (службы Master Data Services)](../attribute-groups-master-data-services.md)  
  
-   [Бизнес-правила (службы Master Data Services)](../business-rules-master-data-services.md)  
  
-   [Экспорт данных &#40;службы Master Data Services&#41;](../overview-exporting-data-master-data-services.md)  
  
-   [Иерархии (службы Master Data Services)](../hierarchies-master-data-services.md)  
  
-   [Коллекции (службы Master Data Services)](../collections-master-data-services.md)  
  
-   [Версии (службы Master Data Services)](../versions-master-data-services.md)  
  
-   [Безопасность (службы Master Data Services)](../security-master-data-services.md)  
  
-   [Развертывание моделей (службы Master Data Services)](../deploying-models-master-data-services.md)  
  
  
