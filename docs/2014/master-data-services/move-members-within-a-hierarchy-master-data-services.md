---
title: Перемещение элементов в иерархии (Master Data Services) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d5e8bf5a041458614422b3c89666ea3ffc9f5a86
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101991"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a>Перемещение элементов в иерархии (службы Master Data Services)
  В службах [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] перемещение элементов в иерархии требуется для того, чтобы изменить местоположение элементов или родительский элемент.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   Для явных иерархий необходимо иметь как минимум **обновление** разрешения на сущность.  
  
-   Для производных иерархий необходимо иметь как минимум **обновление** для модели и все атрибуты на основе домена, используемой в иерархии.  
  
### <a name="to-move-members-within-a-hierarchy"></a>Перемещение элементов в иерархии  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в списке **Модель** .  
  
2.  Выберите версию из списка **Версия** .  
  
3.  Нажмите кнопку **Браузер**.  
  
4.  В строке меню наведите курсор на **иерархий** и нажмите кнопку *hierarchy_name*.  
  
5.  В **иерархии** области, где в древовидной структуре отображается иерархия, установите флажок для каждого элемента, который требуется переместить.  
  
6.  В верхней части **иерархии** области, нажмите кнопку **Вырезать**.  
  
7.  В **иерархии** панель, установите флажок для элемента, который требуется переместить элементы.  
  
8.  Нажмите кнопку **вставить**.  
  
    > [!NOTE]  
    >  В производных иерархиях элементы можно перемещать только на том же уровне. Кроме того, нельзя изменить порядок сортировки элементов.  
  
## <a name="see-also"></a>См. также  
 [Перемещение элементов явной иерархии с помощью промежуточного процесса &#40;службы Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)   
 [Производные иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [Явные иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  