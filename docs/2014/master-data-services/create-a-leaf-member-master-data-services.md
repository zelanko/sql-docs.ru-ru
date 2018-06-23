---
title: Создание конечного элемента (службы Master Data Services) | Документы Майкрософт
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
- leaf members [Master Data Services], creating
- creating leaf members [Master Data Services]
- members [Master Data Services], creating leaf members
ms.assetid: 0499d3b3-d508-4d43-a740-19cf53ade9f1
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8db1358fc13310c56b6486af73eed694e8423cc2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195616"
---
# <a name="create-a-leaf-member-master-data-services"></a>Создание конечного элемента (службы Master Data Services)
  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], конечный элемент создается, если требуется добавить в систему основные данные и не используются промежуточные таблицы или [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] для импорта данных.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   Необходимо иметь как минимум **обновление** разрешение на конечный объект модели для сущности, нужно добавить элемент.  
  
### <a name="to-create-a-leaf-member"></a>Создание конечного элемента  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в списке **Модель** .  
  
2.  Если вы пользователь, выберите открытую версию из списка **Версия** . Если вы являетесь администратором, выберите версию в открытом или блокированном состоянии из списка **Версия** .  
  
3.  Нажмите кнопку **Браузер**.  
  
4.  В строке меню наведите указатель на пункт **Сущности** и щелкните имя сущности, к которой нужно добавить элемент.  
  
5.  Нажмите кнопку **Добавить элемент**.  
  
6.  Заполните поля в области **Сведения** .  
  
7.  Необязательный параметр. В поле **Заметки** введите комментарий о том, для чего добавлен элемент. Заметку могут просматривать все пользователи, которые имеют доступ к элементу.  
  
8.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Загрузка или обновление членов в Master Data Services с помощью промежуточного процесса](add-update-and-delete-data-master-data-services.md)   
 [Создание объединенного элемента &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)   
 [Члены &#40;службы Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)  
  
  