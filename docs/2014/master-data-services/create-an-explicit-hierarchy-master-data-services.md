---
title: Создание явной иерархии (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 29d75b956b6d9be23bd17e3df705724d3876d583
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219494"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a>Создание явной иерархии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]явные иерархии создаются, если необходима неоднородная иерархия, элементы которой могут располагаться на любом уровне. Явные иерархии содержат элементы из одной сущности.  
  
 После создания явной иерархии в нее можно добавлять элементы в функциональной области **Обозреватель** .  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Для сущности необходимо разрешить использование явных иерархий и коллекций. Дополнительные сведения см. в разделе [активация сущности для явных иерархий и коллекций &#40;службы Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).  
  
### <a name="to-create-an-explicit-hierarchy"></a>Создание явной иерархии  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Представление модели** в строке меню наведите курсор на **Управление** и щелкните **Сущности**.  
  
3.  На странице **Обслуживание сущности** выберите модель из списка **Модель** .  
  
4.  Выберите строку сущности, для которой необходимо создать явную иерархию.  
  
5.  Щелкните **Изменить выбранную сущность**.  
  
6.  На **изменение сущности** странице **явных иерархий** панели щелкните **добавить явную иерархию**.  
  
7.  На **Добавление явной иерархии** странице **имя явной иерархии** поле, введите имя для иерархии.  
  
8.  По желанию снимите флажок **Обязательная иерархия** для создания необязательной иерархии. Дополнительные сведения о типах иерархий см. в разделе [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).  
  
9. Нажмите кнопку **сохранить иерархию**.  
  
10. На **изменение сущности** щелкните **сохранить сущность**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Создание объединенного элемента &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [Перемещение элементов в иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a>См. также  
 [Явные иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [Производные иерархии с явными ограничениями (службы Master Data Services)](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Изменение имени явной иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  
