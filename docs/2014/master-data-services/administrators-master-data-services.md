---
title: Администраторы (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 146834648164e49632a62352d684a6da66a09e12
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65480010"
---
# <a name="administrators-master-data-services"></a>Администраторы (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] существует два типа администраторов: администраторы модели и системные администраторы служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
## <a name="model-administrators"></a>Администраторы модели  
 В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], администратор модели — пользователь, имеющий **обновление** разрешение, назначенное объекту модели верхнего уровня на **объекты модели** вкладку и не имеющий других назначенных разрешений.  
  
-   Если пользователь имеет доступ к функциональной области **Обозреватель** , то он может добавлять, удалять и обновлять все основные данные в этой области.  
  
-   Если пользователь имеет доступ к другим функциональным областям, то он может выполнять все административные задачи, доступные в функциональной области.  
  
 Каждая модель может иметь несколько администраторов. Каждый пользователь может быть администратором одной, нескольких или всех моделей в развертывании [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Сделать пользователя администратором модели можно в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] либо с помощью программных средств. Дополнительные сведения см. в разделе [Создание администратора модели (службы Master Data Services)](create-a-model-administrator-master-data-services.md).  
  
## <a name="master-data-services-system-administrator"></a>Системный администратор служб Master Data Services  
 Может быть только один системный администратор служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Системный администратор — это пользователь, указанный для **учетной записи администратора** при создании [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] базы данных.  
  
 Системный администратор служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]:  
  
-   Автоматически имеет доступ ко всем функциональным областям.  
  
-   Можно добавить, удалить и обновлять все основные данные для всех моделей в **Explorer** функциональной области.  
  
 Пользователя, назначенного в качестве системного администратора, можно изменить. Дополнительные сведения см. в разделе [изменить учетную запись системного администратора &#40;службы Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
## <a name="comparing-administrator-types"></a>Сравнение типов администраторов  
  
|Тип администратора|Описание|  
|------------------------|-----------------|  
|Системный администратор служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|Разрешения, назначенные в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], не влияют на доступ администратора.<br /><br /> Автоматически имеет **обновления** разрешение для всех моделей.<br /><br /> Автоматически имеет доступ ко всем функциональным областям.<br /><br /> В таблице mdm.tblUser, значение в **идентификатор** столбец **1**.|  
|Администратор модели|Разрешения, заданные в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], определяют, является ли пользователь администратором модели.<br /><br /> Может быть администратором модели на основе разрешений, назначенных ему явно, либо на основе разрешений, полученных в результате членства в некоторой группе.<br /><br /> Не является администратором только для моделей, имеющих **обновления** разрешение, назначенное объекту модели верхнего уровня и не имеет других разрешений.<br /><br /> Имеет доступ только к тем функциональным областям, к которым разрешен доступ.<br /><br /> В таблице mdm.tblUser, значение в **идентификатор** столбец не является **1**.|  
  
## <a name="see-also"></a>См. также  
 [Создание администратора модели (службы Master Data Services)](create-a-model-administrator-master-data-services.md)   
 [Изменить учетную запись системного администратора &#40;службы Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)   
 [Создание базы данных служб Master Data Services](install-windows/create-a-master-data-services-database.md)   
 [Уведомления (службы Master Data Services)](../../2014/master-data-services/notifications-master-data-services.md)  
  
  
