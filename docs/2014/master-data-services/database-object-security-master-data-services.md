---
title: Защита объектов базы данных (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], object security
- security [Master Data Services], database objects
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 5195df44c591f4c605cfd33aa6bb9934c7d54908
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163505"
---
# <a name="database-object-security-master-data-services"></a>Защита объектов базы данных (службы Master Data Services)
  В базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] данные хранятся во многих таблицах базы данных, а также отображаются в представлениях. Информация, которая может быть защищена в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , видна пользователям, у которых есть доступ к базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 В частности, в модели Employee могут содержаться сведения о заработной плате сотрудников, а в модели Account может присутствовать финансовая информация компании. В пользовательском интерфейсе [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] можно запретить пользователям доступ к этим моделям, но пользователи с доступом к базе данных все равно смогут просматривать такие данные.  
  
 Пользователям можно предоставлять разрешения на объекты базы данных, чтобы они могли работать с определенными частями данных. Дополнительные сведения о предоставлении разрешений см. в разделе [GRANT, предоставление разрешений на объект (Transact-SQL)](/sql/t-sql/statements/grant-object-permissions-transact-sql). Дополнительные сведения о настройке безопасности сервера SQL см. в разделе [Securing SQL Server](../relational-databases/security/securing-sql-server.md).  
  
 Для следующих задач необходим доступ к базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] :  
  
-   [Промежуточное сохранение данных](#Staging)  
  
-   [Проверка данных на соответствие бизнес-правилам](#rules)  
  
-   [Удаление версий](#Versions)  
  
-   [Немедленное применение разрешений для элементов иерархии](#Hierarchy)  
  
-   [Изменение учетной записи системного администратора](#SysAdmin)  
  
-   [Настройка параметров системы](#SysSettings)  
  
##  <a name="Staging"></a> Промежуточное сохранение данных  
 В следующей таблице каждый защищаемый объект имеет строку «name» в составе имени. Это указывает на имя промежуточной таблицы, которая определена при создании сущности. Дополнительные сведения см. в разделе [импорта данных &#40;службы Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
|Действие|Защищаемые объекты|Разрешения|  
|------------|----------------|-----------------|  
|Загрузить конечные элементы и их атрибуты в промежуточную таблицу.|stg.name_Leaf|Требуется: INSERT<br /><br /> Необязательно: SELECT и UPDATE|  
|Загрузить данные из конечной промежуточной таблицы в соответствующие таблицы базы данных MDS.|stg.udp_name_Leaf|EXECUTE|  
|Загрузить консолидированные элементы и их атрибуты в промежуточную таблицу.|stg.name_Consolidated|Требуется: INSERT<br /><br /> Необязательно: SELECT и UPDATE|  
|Загрузить данные из объединенной промежуточной таблицы в соответствующие таблицы базы данных MDS.|stg.udp_name_Consolidated|EXECUTE|  
|Загрузить связи конечных и консолидированных элементов друг в друга в явной иерархии в промежуточной таблице.|stg.name_Relationship|Требуется: INSERT<br /><br /> Необязательно: SELECT и UPDATE|  
|Загрузить данные из промежуточной таблицы связей в соответствующие таблицы базы данных MDS.|stg.udp_name_Relationship|EXECUTE|  
|Просмотреть ошибки, которые возникли при вставке данных из промежуточных таблиц в таблицы базы данных MDS.|stg.udp_name_Relationship|SELECT|  
  
 Дополнительные сведения см. в разделе [Импорт данных (службы Master Data Services)](overview-importing-data-from-tables-master-data-services.md).  
  
##  <a name="rules"></a> Проверка данных на соответствие бизнес-правилам  
  
|Действие|Защищаемый объект|Разрешения|  
|------------|---------------|-----------------|  
|Проверка версии данных на соответствие бизнес-правилам|MDM.udpValidateModel|EXECUTE|  
  
 Дополнительные сведения см. в разделе [Проверка хранимых процедур (службы Master Data Services)](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).  
  
##  <a name="Versions"></a> Удаление версий  
  
|Действие|Защищаемые объекты|Разрешения|  
|------------|----------------|-----------------|  
|Определение идентификатора версии, которую необходимо удалить|mdm.viw_SYSTEM_SCHEMA_VERSION|SELECT|  
|Удаление версии модели|mdm.udpVersionDelete|EXECUTE|  
  
 Дополнительные сведения см. в разделе [Удаление версии (службы Master Data Services)](../../2014/master-data-services/delete-a-version-master-data-services.md).  
  
##  <a name="Hierarchy"></a> Немедленное применение разрешений для элементов иерархии  
  
|Действие|Защищаемые объекты|Разрешения|  
|------------|----------------|-----------------|  
|Срочное применение разрешений для элемента|mdm.udpSecurityMemberProcessRebuildModel|EXECUTE|  
  
 Дополнительные сведения см. в разделе [Срочное применение разрешений для элемента (службы Master Data Services)](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
##  <a name="SysAdmin"></a> Изменение учетной записи системного администратора  
  
|Действие|Защищаемые объекты|Разрешения|  
|------------|----------------|-----------------|  
|Определение идентификатора безопасности (SID) нового администратора|mdm.tblUser|SELECT|  
|Изменение учетной записи администратора системы|mdm.udpSecuritySetAdministrator|EXECUTE|  
  
 Дополнительные сведения см. в разделе [изменить учетную запись системного администратора &#40;службы Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
##  <a name="SysSettings"></a> Настройка параметров системы  
 Эти параметры системы можно изменять, настраивая поведение в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Их можно настроить в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] или при наличии доступа на выполнение команды UPDATE изменять непосредственно в таблице базы данных mdm.tblSystemSetting. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>См. также  
 [Безопасность (службы Master Data Services)](../../2014/master-data-services/security-master-data-services.md)  
  
  
