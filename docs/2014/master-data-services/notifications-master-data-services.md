---
title: Уведомления (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- notifications [Master Data Services]
- notifications [Master Data Services], about notifications
- e-mail [Master Data Services]
- e-mail [Master Data Services], about e-mail notifications
ms.assetid: d7ad32d5-9fe5-48fd-8c61-0b00c0aff082
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8213976a69f360fe13fa9d085919992e3daadf4b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36094592"
---
# <a name="notifications-master-data-services"></a>Уведомления (службы Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] можно настроить для отправки уведомления по электронной почте при сбое проверки бизнес-правил или изменении состояния версии модели изменилось.  
  
## <a name="how-notifications-are-sent"></a>Способ отправки уведомлений  
 Уведомления настраиваются в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Уведомления отправляются в сообщениях электронной почты с помощью компонента Database Mail в экземпляре компонента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] , в котором размещена база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения о компоненте Database Mail см. в разделе [Объекты конфигурации компонента Database Mail](../relational-databases/database-mail/database-mail-configuration-objects.md) электронной документации по [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="when-notifications-are-sent"></a>Время отправки уведомлений  
 После настройки уведомлений автоматические уведомления могут отправляться по электронной почте в следующие экземпляры.  
  
|Экземпляр|Описание|  
|--------------|-----------------|  
|Проверка данных на соответствие бизнес-правилам завершилась с ошибкой|Если значение атрибута не прошло проверку на соответствие бизнес-правилам, то для отправки почтовых сообщений потребуется настроить бизнес-правила по отдельности. Дополнительные сведения см. в разделе [Configure Business Rules to Send Notifications &#40;Master Data Services&#41;](configure-business-rules-to-send-notifications-master-data-services.md).|  
|Изменения состояния версии модели|Пользователи, являющиеся администраторами модели, автоматически получают уведомления о каждом изменении состояния версии модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).|  
  
## <a name="system-settings"></a>Системные настройки  
 В [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] есть параметры, влияющие на рассылку уведомлений. Эти параметры можно настроить в программе [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] или непосредственно в таблице системных параметров в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Настройка [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] для отправки уведомлений.|[Настройка уведомлений по электронной почте &#40;службы Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md)|  
|Настройка [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] для отправки уведомлений при изменении значений атрибутов.|[Настройка бизнес-правила для отправки уведомлений &#40;службы Master Data Services&#41;](configure-business-rules-to-send-notifications-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Бизнес-правила &#40;службы Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [Версии &#40;службы Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [Устранение неполадок в уведомлениях по электронной почте (службы Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)  
  
  