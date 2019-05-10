---
title: Навигационный доступ (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 942fe720fb4ba0e1dc65f2b6f918b3e5c1f985a8
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488049"
---
# <a name="navigational-access-master-data-services"></a>Навигационный доступ (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Навигационный доступ применяется к модели объекта безопасности, которая назначается на вкладке **Модель** .  
  
 Навигационный доступ — это доступ к уровням выше того, который был назначен системой безопасности.  
  
 В этом примере разрешения назначаются на сущность, поэтому навигационный доступ предоставляется на уровне модели.  
  
 ![mds_conc_inheritance_model](../master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **Сущности**  
  
 При назначении разрешения на сущность, ее конечные или консолидированные элементы, навигационный доступ означает возможность чтения и обновления имени и кода для всех элементов. Предоставляется также возможность считывать имя модели.  
  
 **Атрибуты**  
  
 При назначении разрешения на атрибут навигационный доступ означает возможность чтения и обновления имени и кода для всех элементов сущности. Предоставляется также возможность считывать имя модели.  
  
 **Коллекции**  
  
 При назначении разрешений на коллекции это будет возможность чтения и обновления имени, кода, описания и идентификатора владельца. Предоставляется также возможность считывать имя модели.  
  
## <a name="see-also"></a>См. также:  
 [Способ определения разрешений (службы Master Data Services)](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
