---
title: Удаление элемента или коллекции
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], deleting
- leaf members [Master Data Services], deleting
- deleting members [Master Data Services]
- members [Master Data Services], deleting
- consolidated members [Master Data Services], deleting
ms.assetid: 519130a7-4226-4d71-9124-d2ee0ce7e5bd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 789b372660e7df5282c700f57654162288dabb78
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729375"
---
# <a name="delete-a-member-or-collection-master-data-services"></a>Удаление элемента или коллекции (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В службах [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]элементы и коллекции следует удалять, когда в них больше нет необходимости. Если необходимо удалить большое количество элементов, лучше воспользоваться промежуточными таблицами. Дополнительные сведения см. в разделе [Импорт данных из таблиц (службы Master Data Services)](../master-data-services/import-data-from-tables-master-data-services.md).  
  
> [!NOTE]  
>  Невозможно удалить элемент, если он используется в качестве значения атрибута на основе домена для другого элемента.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   Для элементов необходимо как минимум разрешение **Удаление** для конечного объекта модели, из которого нужно удалить элемент.  
  
-   Для коллекций необходимо как минимум разрешение **Обновление** на удаляемый конечный объект коллекции.  
  
### <a name="to-delete-a-member-or-collection"></a>Удаление элемента или коллекции  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в списке **Модель** .  
  
2.  Выберите версию из списка **Версия** .  
  
3.  Нажмите кнопку **Браузер**.  
  
4.  Для удаления  
  
    -   конечного элемента в строке меню наведите указатель мыши на **Сущности** и щелкните имя сущности, содержащей элемент;  
  
    -   объединенного элемента в строке меню наведите указатель мыши на **Иерархии** и щелкните имя иерархии, содержащей элемент. Затем щелкните узел в иерархии, содержащий элемент.  
  
    -   коллекции в строке меню наведите указатель мыши на **Коллекции** и щелкните имя сущности, содержащей коллекцию.  
  
5.  Щелкните в сетке строку удаляемого элемента или коллекции.  
  
6.  Нажмите кнопку **Удалить элемент**, **Удалить**или **Удалить коллекцию**.  
  
7.  Администраторы сущности также получат возможность очистить (необратимо удалить) все обратимо удаленные элементы в версии сущности.  
  
8.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также раздел  
 [Повторная активация элемента или коллекции (службы Master Data Services)](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)   
 [Элементы (службы Master Data Services)](../master-data-services/members-master-data-services.md)   
 [Коллекции (службы Master Data Services)](../master-data-services/collections-master-data-services.md)  
  
  
