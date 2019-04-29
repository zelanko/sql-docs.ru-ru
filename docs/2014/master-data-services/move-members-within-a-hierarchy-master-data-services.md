---
title: Перемещение элементов в иерархии (Master Data Services) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 96f3c1232f1124ef5f2cd9e77d89fa06607392c7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923441"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a>Перемещение элементов в иерархии (службы Master Data Services)
  В службах [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] перемещение элементов в иерархии требуется для того, чтобы изменить местоположение элементов или родительский элемент.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   Для явных иерархий необходимо иметь как минимум **обновления** разрешения на сущность.  
  
-   Для производных иерархий необходимо иметь как минимум **обновления** для модели и все атрибуты на основе домена, используемой в иерархии.  
  
### <a name="to-move-members-within-a-hierarchy"></a>Перемещение элементов в иерархии  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в списке **Модель** .  
  
2.  Выберите версию из списка **Версия** .  
  
3.  Нажмите кнопку **Браузер**.  
  
4.  На панели меню наведите указатель мыши на **иерархий** и нажмите кнопку *hierarchy_name*.  
  
5.  В **иерархии** области, где иерархия отображается в виде древовидной структуры, установите флажок для каждого элемента, который требуется переместить.  
  
6.  В верхней части **иерархии** панели щелкните **Вырезать**.  
  
7.  В **иерархии** области установите флажок для элемента, который вы хотите переместить элементы.  
  
8.  Нажмите кнопку **вставить**.  
  
    > [!NOTE]  
    >  В производных иерархиях элементы можно перемещать только на том же уровне. Кроме того, нельзя изменить порядок сортировки элементов.  
  
## <a name="see-also"></a>См. также  
 [Перемещение элементов явной иерархии с помощью промежуточного процесса &#40;службы Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)   
 [Производные иерархии (службы Master Data Services)](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [Явные иерархии (службы Master Data Services)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
