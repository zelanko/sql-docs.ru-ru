---
title: Изменить учетную запись системного администратора (Master Data Services) | Документация Майкрософт
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66054139"
---
# <a name="change-the-system-administrator-account-master-data-services"></a>Изменение учетной записи системного администратора (службы Master Data Services)
  Можно изменить учетную запись, используется в качестве [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] системному администратору.  
  
> [!WARNING]  
>  После завершения этой процедуры учетная запись прежнего системного администратора будет удалена.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо добавить имя пользователя нового системного администратора к списку пользователей [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Дополнительные сведения см. в разделе [Добавление пользователя &#40;службы Master Data Services&#41;](add-a-user-master-data-services.md).  
  
-   У пользователя должны быть разрешения на просмотр mdm.tblUser и на выполнение хранимой процедуры mds.udpSecurityMemberProcessRebuildModel в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Дополнительные сведения см. в разделе [Защита объектов базы данных (службы Master Data Services)](../../2014/master-data-services/database-object-security-master-data-services.md).  
  
### <a name="to-change-the-administrator-account"></a>Изменение учетной записи администратора  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  В mdm.tblUser найдите пользователя, который будет новым администратором и скопируйте значение в `SID` столбца.  
  
3.  Создайте новый запрос.  
  
4.  Введите следующий текст, заменив *"Домен\имя_пользователя"* с именем пользователя нового администратора и *SID* со значением, скопированным на шаге 2.  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  Выполните запрос.  
  
## <a name="see-also"></a>См. также  
 [Администраторы (службы Master Data Services)](../../2014/master-data-services/administrators-master-data-services.md)  
  
  
