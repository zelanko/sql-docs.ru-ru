---
title: Удаление явной иерархии (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: bfbc515c888e41d0ab216e3c0a7e56a5d2c4c8c4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103984"
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a>Удаление явной иерархии (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]явные иерархии удаляются тогда, когда в них отпадает необходимость.  
  
> [!WARNING]  
>  При удалении явной иерархии все консолидированные элементы в этой иерархии также удаляются. Если удаляются все явные иерархии для сущности, то все коллекции для этой сущности также удаляются и сущность перестает поддерживать явные иерархии и коллекции.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-delete-an-explicit-hierarchy"></a>Удаление явной иерархии  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Представление модели** в строке меню наведите курсор на **Управление** и щелкните **Сущности**.  
  
3.  На странице **Обслуживание сущности** выберите модель из списка **Модель** .  
  
4.  Выберите строку сущности, содержащую явную иерархию, которую необходимо удалить.  
  
5.  Щелкните **Изменить выбранную сущность**.  
  
6.  На **изменение сущности** странице **явных иерархий** области, выберите удаляемую явную иерархию.  
  
7.  Нажмите кнопку **удалить выбранную иерархию**.  
  
8.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
9. В дополнительном диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Создание явной иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [Явные иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
