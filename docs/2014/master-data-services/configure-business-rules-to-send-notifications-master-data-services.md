---
title: Настройка бизнес-правил для отправки уведомлений (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], configuring notifications
- e-mail [Master Data Services], configuring business rules
- notifications [Master Data Services], configuring business rules
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: b0ea6e215b5192d1b9e84ed252708b188d5c5a59
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65483954"
---
# <a name="configure-business-rules-to-send-notifications-master-data-services"></a>Настройка в бизнес-правилах отправки уведомлений (службы Master Data Services)
  Бизнес-правила для отправки уведомлений в службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]настраивают в том случае, если нужно уведомлять пользователей об изменениях значений атрибутов.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональным областям **Администрирование системы** и **Разрешения пользователей и групп** . Если отсутствуют разрешения для функциональной области **Разрешения пользователей и групп** , то пользователь не сможет просмотреть список пользователей и групп, которым необходимо отправить уведомления.  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](administrators-master-data-services.md).  
  
-   Уже должно существовать бизнес-правило, использующее действие по проверке. Дополнительные сведения см. в разделе [Создание и публикация бизнес-правила (службы Master Data Services)](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
-   Пользователь или группа, получающие уведомления, должны иметь разрешения не ниже **Только для чтения** для атрибута, проверка которого завершилась ошибкой. Пользователи или группы, которым явно или неявно отказано в разрешении на атрибут, получат по электронной почте соответствующее сообщение, но не смогут получить доступ к атрибуту в службах [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   Если сообщение электронной почты отправляется группе, то это сообщение получат только те члены группы, которые имеют доступ к службам [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
### <a name="to-configure-business-rules-to-send-notifications"></a>Настройка бизнес-правил для отправки уведомлений  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Обслуживание бизнес-правил** выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  Из **тип члена** выберите тип элемента.  
  
6.  Выберите из списка **Атрибут** атрибут или оставьте **Все**по умолчанию.  
  
7.  В сетке, в строке бизнес-правила, дважды щелкните **уведомления** поля.  
  
8.  Во вложенном меню выберите пользователя или группу, куда необходимо отправлять уведомление.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   Примените бизнес-правила к данным с помощью одной из следующих процедур:  
  
    -   [Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   Настройте протокол электронной почты следующим образом.  
  
    -   [Настройка уведомления электронной почты (службы Master Data Services)](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
## <a name="see-also"></a>См. также  
 [Уведомления (службы Master Data Services)](../../2014/master-data-services/notifications-master-data-services.md)   
 [Настройка уведомления электронной почты (службы Master Data Services)](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
  
