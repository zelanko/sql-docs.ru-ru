---
title: Модели
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], about models
- models [Master Data Services]
ms.assetid: 9f862a3d-25ab-41e9-b833-1db99959e825
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6bee1ab1716eac70d51006b8bb4315b204be67ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73727946"
---
# <a name="models-master-data-services"></a>Модели (службы основных данных)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Модели — это самый высокий уровень организации данных в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Модель определяет структуру данных в решении управления основными данными. Модель содержит следующие объекты:  
  
-   Сущности  
  
-   Атрибуты и группы атрибутов  
  
-   Производные и явные иерархии  
  
-   Коллекции  
  
 Модели организуют структуру основных данных. Реализация [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] может иметь одну или несколько моделей, которые объединяют схожие данные. В общем случае основные понятия могут быть сгруппированы одним из четырех способов: по лицам, местам, предметам или понятиям. Например, можно создать модель «Продукт» для данных, связанных с продуктами, или модель «Клиент»для данных, связанных с клиентами.  
  
 Пользователям и группам можно давать разрешения на просмотр и обновление объектов внутри модели. Если модели не назначено разрешение, она не отображается.  
  
 В любой момент времени можно создать копии основных данных в модели. Эти копии называются версиями.  
  
 При определении модели в тестовой среде ее можно развернуть с соответствующими данными или без них в рабочей среде. Это устраняет необходимость повторного создания моделей в рабочей среде.  
  
## <a name="how-models-relate-to-other-objects"></a>Связь моделей с другими объектами  
 В модели содержатся сущности. Сущности содержат атрибуты, явные иерархии и коллекции. Атрибуты можно объединять в группы. Атрибуты на основе домена существуют, когда сущность используется как атрибут для другой сущности.  
  
 На рисунке отображены связи между объектами модели.  
  
 ![Объекты в модели служб Master Data Services](../master-data-services/media/mds-conc-model-circles.gif "Объекты в модели служб Master Data Services")  
  
> [!NOTE]  
>  Производные иерархии — это тоже объекты модели, но на рисунке они не показаны. Производные иерархии происходят от связей атрибутов на основе домена, существующих между сущностями. Дополнительные сведения см. в разделе [Производные иерархии (службы Master Data Services)](../master-data-services/derived-hierarchies-master-data-services.md).  
  
 Основные данные — это данные, содержащиеся в объектах модели. В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]основные данные хранятся в виде элементов сущностей.  
  
 Объекты моделей находятся в функциональной области **Администрирование системы** пользовательского интерфейса [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
## <a name="model-example"></a>Пример модели  
 В следующем примере объекты в модели «Продукт» логически группируют данные, связанные с продуктом.  
  
 ![Пример основных данных модели «Продукт»](../master-data-services/media/mds-conc-model.gif "Пример основных данных модели «Продукт»")  
  
 Другие распространенные модели:  
  
-   «Счета» — может включать такие сущности, как балансы, счета прибылей, статистика и тип счета;  
  
-   клиенты — может включать в себя такие сущности, как пол, образование, занятость и семейное положение;  
  
-   географический регион — может включать в себя такие сущности, как почтовые коды, города, округа, районы, республики, края, страны и континенты.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание модели для организации основных данных.|[Создание &#40;модели Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md)|  
|Изменение имени существующей модели.|[Изменение &#40;модели Master Data Services&#41;](../master-data-services/edit-model-master-data-services.md)|  
|Удаление существующей модели.|[Удаление &#40;модели Master Data Services&#41;](../master-data-services/delete-a-model-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Обзор Master Data Services &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
  
-   [Сущности &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
-   [Master Data Services &#40;атрибутов&#41;](../master-data-services/attributes-master-data-services.md)  
  
-   [Развертывание моделей &#40;Master Data Services&#41;](../master-data-services/deploying-models-master-data-services.md)  
  
-   [Разрешения объекта модели &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
