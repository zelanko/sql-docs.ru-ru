---
title: Создание флага версии (службы Master Data Services) | Документы Майкрософт
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
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cea2d431b213d6b62106fff5c0c15c588e1b115d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195421"
---
# <a name="create-a-version-flag-master-data-services"></a>Создание флага версии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]флаг версии создается, чтобы назначить версию. Флаг может указывать на то, какую версию следует использовать пользователям или системам-подписчикам.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-version-flag"></a>Создание флага версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На панели меню страницы **Управление версиями** наведите курсор на **Управление** и выберите **Флаги**.  
  
3.  На странице **Управление флагами версий** выберите модель в поле **Модель** , для которой нужно создать флаг.  
  
4.  Нажмите кнопку **Добавить**.  
  
5.  В поле **Имя** введите имя.  
  
6.  В поле **Описание** введите описание.  
  
7.  В поле **Только зафиксированные версии** выберите **True** , чтобы указать, что флаг может назначаться только версиям со статусом **Зафиксированная** . Выберите **False** , чтобы указать, что флаг может назначаться версиям с любым состоянием.  
  
8.  Нажмите кнопку **Сохранить**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Назначение флага версии &#40;службы Master Data Services&#41;](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a>См. также  
 [Версии &#40;службы Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Изменение имени флага версии &#40;службы Master Data Services&#41;](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  