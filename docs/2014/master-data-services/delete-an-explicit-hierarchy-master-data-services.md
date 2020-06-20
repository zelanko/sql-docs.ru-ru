---
title: Удаление явной иерархии (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: db4a6a51164fbcdfd62a542cba9e48a58438d0ed
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84950724"
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a>Удаление явной иерархии (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]явные иерархии удаляются тогда, когда в них отпадает необходимость.  
  
> [!WARNING]  
>  При удалении явной иерархии все консолидированные элементы в этой иерархии также удаляются. Если удаляются все явные иерархии для сущности, то все коллекции для этой сущности также удаляются и сущность перестает поддерживать явные иерархии и коллекции.  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-delete-an-explicit-hierarchy"></a>Удаление явной иерархии  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Представление модели** в строке меню наведите курсор на **Управление** и щелкните **Сущности**.  
  
3.  На странице **Обслуживание сущности** выберите модель из списка **Модель** .  
  
4.  Выберите строку сущности, содержащую явную иерархию, которую необходимо удалить.  
  
5.  Щелкните **Изменить выбранную сущность**.  
  
6.  На странице **Изменение сущности** на панели **явные иерархии** щелкните явную иерархию, которую нужно удалить.  
  
7.  Нажмите кнопку **Удалить выбранную иерархию**.  
  
8.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
9. В дополнительном диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Создание явной иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [Явные иерархии (службы Master Data Services)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
