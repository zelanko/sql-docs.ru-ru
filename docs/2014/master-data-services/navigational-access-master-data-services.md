---
title: Навигационный доступ (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 20f3e8f8d51231f823fe43a8aeff4e606a10ffa2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087204"
---
# <a name="navigational-access-master-data-services"></a>Навигационный доступ (службы Master Data Services)
  Навигационный доступ применяется к модели объекта безопасности, которая назначается на вкладке **Модель** .  
  
 Навигационный доступ — это доступ к уровням выше того, который был назначен системой безопасности.  
  
 В этом примере разрешения назначаются на сущность, поэтому навигационный доступ предоставляется на уровне модели.  
  
 ![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **Сущности**  
  
 При назначении разрешения на сущность, ее конечные или консолидированные элементы, навигационный доступ означает возможность чтения и обновления имени и кода для всех элементов. Предоставляется также возможность считывать имя модели.  
  
 **Атрибуты**  
  
 При назначении разрешения на атрибут навигационный доступ означает возможность чтения и обновления имени и кода для всех элементов сущности. Предоставляется также возможность считывать имя модели.  
  
 **Коллекции**  
  
 При назначении разрешений на коллекции это будет возможность чтения и обновления имени, кода, описания и идентификатора владельца. Предоставляется также возможность считывать имя модели.  
  
## <a name="see-also"></a>См. также  
 [Способ определения разрешений &#40;службы Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)  
  
  
