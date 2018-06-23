---
title: Удаление атрибута (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [Master Data Services], deleting
- deleting attributes [Master Data Services]
ms.assetid: ec3e66f7-0e35-43d7-a80d-64899948ebfe
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9c1317806b4d0d6e5a52082b7fc343e3fe28cd1a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096190"
---
# <a name="delete-an-attribute-master-data-services"></a>Удаление атрибута (службы Master Data Services)
  Операция удаления атрибута в службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]без возможности восстановления удаляет атрибут и все связанные с ним значения.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-delete-an-attribute"></a>Удаление атрибута  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Представление модели** в строке меню наведите курсор на **Управление** и щелкните **Сущности**.  
  
3.  На странице **Обслуживание сущности** выберите модель из списка **Модель** .  
  
4.  Выберите строку сущности, содержащую атрибут, который необходимо удалить.  
  
5.  Щелкните **Изменить выбранную сущность**.  
  
6.  На **изменение сущности** щелкните атрибут, который требуется удалить.  
  
    > [!NOTE]  
    >  Удалить атрибуты «Имя» и «Код» нельзя.  
  
7.  Нажмите кнопку **удалить выбранный атрибут**.  
  
8.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
9. В дополнительном диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Атрибуты &#40;службы Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)   
 [Атрибуты на основе домена &#40;службы Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md)   
 [Создание текстового атрибута &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)   
 [Создание атрибута на основе домена &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  