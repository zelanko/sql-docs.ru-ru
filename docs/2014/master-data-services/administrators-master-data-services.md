---
title: Администраторы (службы Master Data Services) | Документы Майкрософт
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
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 11abfb4949bdd7917066ed785dd1014efc026e9a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098928"
---
# <a name="administrators-master-data-services"></a>Администраторы (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] существует два типа администраторов: администраторы модели и системные администраторы служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
## <a name="model-administrators"></a>Администраторы модели  
 В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], администратор модели — пользователя, имеющего **обновление** разрешение, назначенное объекту модели верхнего уровня на **объектов модели** вкладку и не имеющий других назначенных разрешений.  
  
-   Если пользователь имеет доступ к функциональной области **Обозреватель** , то он может добавлять, удалять и обновлять все основные данные в этой области.  
  
-   Если пользователь имеет доступ к другим функциональным областям, то он может выполнять все административные задачи, доступные в функциональной области.  
  
 Каждая модель может иметь несколько администраторов. Каждый пользователь может быть администратором одной, нескольких или всех моделей в развертывании [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Сделать пользователя администратором модели можно в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] либо с помощью программных средств. Дополнительные сведения см. в разделе [Create a Model Administrator &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md).  
  
## <a name="master-data-services-system-administrator"></a>Системный администратор служб Master Data Services  
 Может быть только один системный администратор служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Системный администратор — это пользователь, указанный для **учетной записи администратора** при создании [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] базы данных.  
  
 Системный администратор служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]:  
  
-   Автоматически имеет доступ ко всем функциональным областям.  
  
-   Добавление, удаление и обновлять все основные данные для всех моделей в **Explorer** функциональной области.  
  
 Пользователя, назначенного в качестве системного администратора, можно изменить. Дополнительные сведения см. в разделе [изменение учетной записи администратора системы &#40;службы Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
## <a name="comparing-administrator-types"></a>Сравнение типов администраторов  
  
|Тип администратора|Описание|  
|------------------------|-----------------|  
|Системный администратор служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|Разрешения, назначенные в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , не влияют на доступ администратора.<br /><br /> Автоматически имеет **обновление** доступ ко всем моделям.<br /><br /> Автоматически имеет доступ ко всем функциональным областям.<br /><br /> В таблице mdm.tblUser, значение в **идентификатор** столбец **1**.|  
|Администратор модели|Разрешения, заданные в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], определяют, является ли пользователь администратором модели.<br /><br /> Может быть администратором модели на основе разрешений, назначенных ему явно, либо на основе разрешений, полученных в результате членства в некоторой группе.<br /><br /> Является администратором только для моделей, имеющих **обновление** разрешение, назначенное объекту модели верхнего уровня и не имеет других разрешений.<br /><br /> Имеет доступ только к тем функциональным областям, к которым разрешен доступ.<br /><br /> В таблице mdm.tblUser, значение в **идентификатор** столбец не **1**.|  
  
## <a name="see-also"></a>См. также  
 [Создание администратора модели &#40;службы Master Data Services&#41;](create-a-model-administrator-master-data-services.md)   
 [Изменение учетной записи администратора системы &#40;службы Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)   
 [Создание базы данных служб Master Data Services](install-windows/create-a-master-data-services-database.md)   
 [Уведомления о &#40;службы Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md)  
  
  