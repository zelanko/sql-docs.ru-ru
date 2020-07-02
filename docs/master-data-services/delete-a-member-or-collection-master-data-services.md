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
ms.openlocfilehash: 613fa319c00ab100e52835faab1eafc33c07c9be
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811558"
---
# <a name="delete-a-member-or-collection-master-data-services"></a>Удаление элемента или коллекции (службы Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В службах [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]элементы и коллекции следует удалять, когда в них больше нет необходимости. Если необходимо удалить большое количество элементов, лучше воспользоваться промежуточными таблицами. Дополнительные сведения см. в разделе [Импорт данных из таблиц &#40;Master Data Services&#41;](../master-data-services/import-data-from-tables-master-data-services.md)  
  
> [!NOTE]  
>  Невозможно удалить элемент, если он используется в качестве значения атрибута на основе домена для другого элемента.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
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
  
## <a name="see-also"></a>См. также  
 [Повторная активация элемента или коллекции &#40;Master Data Services&#41;](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)   
 [Master Data Services &#40;членов&#41;](../master-data-services/members-master-data-services.md)   
 [Коллекции (службы Master Data Services)](../master-data-services/collections-master-data-services.md)  
  
  
