---
title: "Удаление атрибута (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Master Data Services], deleting
- deleting attributes [Master Data Services]
ms.assetid: ec3e66f7-0e35-43d7-a80d-64899948ebfe
caps.latest.revision: "6"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1709151bed92738c5080013396969fd9c4d84e7c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="delete-an-attribute-master-data-services"></a>Удаление атрибута (службы Master Data Services)
  Операция удаления атрибута в службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]без возможности восстановления удаляет атрибут и все связанные с ним значения.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-an-attribute"></a>Удаление атрибута  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Управление сущностью** выберите строку сущности, для которой необходимо создать атрибут.  
  
4.  Нажмите **Атрибуты**.  
  
5.  На странице **Управление атрибутами** выполните одно из следующих действий:  
  
    -   Если атрибут предназначен для конечных элементов, в списке **Типы членов** выберите **Конечный элемент** .  
  
    -   Если атрибут предназначен для консолидированных элементов, в списке **Типы членов** выберите **Консолидированный элемент** .  
  
    -   Если атрибут предназначен для коллекций, в списке **Типы членов** выберите **Коллекция** .  
  
6.  Выберите строку для атрибута, который необходимо удалить.  
  
    > [!NOTE]  
    >  Удалить атрибуты «Имя» и «Код» нельзя.  
  
7.  Щелкните **Удалить**.  
  
8.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Атрибуты (службы Master Data Services)](../master-data-services/attributes-master-data-services.md)   
 [Атрибуты на основе домена (службы Master Data Services)](../master-data-services/domain-based-attributes-master-data-services.md)   
 [Создание текстового атрибута (службы Master Data Services)](../master-data-services/create-a-text-attribute-master-data-services.md)   
 [Создание атрибута на основе домена (службы Master Data Services)](../master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
