---
title: Уведомления
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- notifications [Master Data Services]
- notifications [Master Data Services], about notifications
- e-mail [Master Data Services]
- e-mail [Master Data Services], about e-mail notifications
ms.assetid: d7ad32d5-9fe5-48fd-8c61-0b00c0aff082
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ec76228a4f8307813a2bb098b648133e065c5cd5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73727953"
---
# <a name="notifications-master-data-services"></a>Уведомления (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] можно настроить для отправки уведомлений по электронной почте при непрохождении проверки на соответствие бизнес-правилам, изменении состояния версии модели или изменении состояния набора изменений.  
  
## <a name="how-notifications-are-sent"></a>Способ отправки уведомлений  
 Уведомления настраиваются в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Уведомления отправляют сообщения электронной почты с помощью Database Mail на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] , где [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] размещается база данных. Дополнительные сведения о компоненте Database Mail см. в разделе [Объекты конфигурации компонента Database Mail](../relational-databases/database-mail/database-mail-configuration-objects.md) электронной документации по [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="when-notifications-are-sent"></a>Время отправки уведомлений  
 После настройки уведомлений автоматические уведомления могут отправляться по электронной почте в следующие экземпляры.  
  
|Экземпляр|Description|  
|--------------|-----------------|  
|Проверка данных на соответствие бизнес-правилам завершилась с ошибкой|Если значение атрибута не прошло проверку на соответствие бизнес-правилам, то для отправки почтовых сообщений потребуется настроить бизнес-правила по отдельности. В уведомлении содержатся следующие сведения:<br /><br /> Модель<br /><br /> Версия<br /><br /> Сущность<br /><br /> Код элемента<br /><br /> Проверка бизнес-правила завершилась сбоем<br /><br /> Ссылка на элемент, для которого значение атрибута не соответствует бизнес-правилу<br /><br /> Время выдачи уведомления<br /><br /> Дополнительные сведения см. в разделе [Настройка в бизнес-правилах отправки уведомлений (службы Master Data Services)](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md).|  
|Изменения состояния версии модели|Пользователи, являющиеся администраторами модели, автоматически получают уведомления о каждом изменении состояния версии модели. В уведомлении содержатся следующие сведения:<br /><br /> Модель<br /><br /> Версия<br /><br /> Предыдущее и новое состояние версии<br /><br /> Время выдачи уведомления<br /><br /> Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).|  
|Изменение состояния набора изменений|Каждый раз при изменении состояния набора изменений для сущности, которая требует утверждения, администраторы сущности и (или) владельцы набора изменений получают уведомления автоматически. В уведомлении содержатся следующие сведения:<br /><br /> Модель<br /><br /> Версия<br /><br /> Имя набора изменений<br /><br /> Предыдущее состояние<br /><br /> Новое состояние<br /><br /> Ссылка для применения набора изменений с целью просмотра и изменения ожидающих изменений.<br /><br /> Дополнительные сведения см. в разделе [наборы изменений &#40;Master Data Services&#41;](../master-data-services/changesets-master-data-services.md)|  
  
## <a name="system-settings"></a>Системные настройки  
 В [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] есть параметры, влияющие на рассылку уведомлений. Эти параметры можно настроить в программе [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] или непосредственно в таблице системных параметров в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Настройка [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] для отправки уведомлений.|[Настройка уведомлений по электронной почте &#40;Master Data Services&#41;](../master-data-services/configure-email-notifications-master-data-services.md)|  
|Настройка [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] для отправки уведомлений при изменении значений атрибутов.|[Настройка бизнес-правил для отправки уведомлений &#40;Master Data Services&#41;](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Бизнес-правила &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [Версии &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)  
  
-   [Устранение неполадок с уведомлениями по электронной почте (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)  
  
  
