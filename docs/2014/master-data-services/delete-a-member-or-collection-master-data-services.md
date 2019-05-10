---
title: Удаление элемента или коллекции (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: f3164bca23e709fd434c6ba7850ec21179a076ef
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65479714"
---
# <a name="delete-a-member-or-collection-master-data-services"></a>Удаление элемента или коллекции (службы Master Data Services)
  В службах [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]элементы и коллекции следует удалять, когда в них больше нет необходимости. Если необходимо удалить большое количество элементов, лучше воспользоваться промежуточным процессом. Дополнительные сведения см. в разделе [деактивировать или удалить членов группы с помощью промежуточного процесса &#40;службы Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).  
  
> [!NOTE]  
>  Невозможно удалить элемент, если он используется в качестве значения атрибута на основе домена для другого элемента.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   Для элементов, необходимо иметь как минимум **обновления** разрешение для конечного объекта модели, можно удалить элемент из.  
  
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
  
7.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Повторная активация элемента или коллекции (службы Master Data Services)](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)   
 [Элементы (службы Master Data Services)](../../2014/master-data-services/members-master-data-services.md)   
 [Коллекции (службы Master Data Services)](../../2014/master-data-services/collections-master-data-services.md)  
  
  
