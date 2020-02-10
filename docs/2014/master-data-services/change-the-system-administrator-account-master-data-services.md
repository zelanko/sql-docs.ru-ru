---
title: Изменение учетной записи системного администратора (Master Data Services) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], changing
ms.assetid: cf30312e-4338-49a7-90f0-6e4f7b431ff8
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 911bd20c7d232bca52fdf9dca294bd7a4924d984
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054139"
---
# <a name="change-the-system-administrator-account-master-data-services"></a>Изменение учетной записи системного администратора (службы Master Data Services)
  Можно изменить учетную запись пользователя, назначенную [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] системным администратором.  
  
> [!WARNING]  
>  После завершения этой процедуры учетная запись прежнего системного администратора будет удалена.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо добавить имя пользователя нового системного администратора к списку пользователей [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Дополнительные сведения см. [в разделе Добавление пользователя &#40;Master Data Services&#41;](add-a-user-master-data-services.md).  
  
-   У пользователя должны быть разрешения на просмотр mdm.tblUser и на выполнение хранимой процедуры mds.udpSecurityMemberProcessRebuildModel в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Дополнительные сведения см. в разделе [Защита объектов базы данных (службы Master Data Services)](../../2014/master-data-services/database-object-security-master-data-services.md).  
  
### <a name="to-change-the-administrator-account"></a>Изменение учетной записи администратора  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  В MDM. tblUser найдите пользователя, который будет новым администратором, и скопируйте значение в `SID` столбец.  
  
3.  Создайте новый запрос.  
  
4.  Введите следующий текст, заменив *domain \ user_name* именем пользователя и *идентификатором безопасности* нового администратора на значение, скопированное на шаге 2.  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  Выполните запрос.  
  
## <a name="see-also"></a>См. также:  
 [Администраторы &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)  
  
  
