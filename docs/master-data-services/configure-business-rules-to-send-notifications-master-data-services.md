---
title: "Настройка бизнес-правил для отправки уведомлений (службы Master Data Services) | Документы Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules [Master Data Services], configuring notifications
- e-mail [Master Data Services], configuring business rules
- notifications [Master Data Services], configuring business rules
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
caps.latest.revision: 10
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 85497539d3b90b2098cba5994117c08d44afe87c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="configure-business-rules-to-send-notifications-master-data-services"></a>Настройка в бизнес-правилах отправки уведомлений (службы Master Data Services)
  Бизнес-правила для отправки уведомлений в службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]настраивают в том случае, если нужно уведомлять пользователей об изменениях значений атрибутов.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Необходимо иметь разрешение на доступ к функциональным областям **Администрирование системы** и **Разрешения пользователей и групп** . Если отсутствуют разрешения для функциональной области **Разрешения пользователей и групп** , то пользователь не сможет просмотреть список пользователей и групп, которым необходимо отправить уведомления.  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Уже должно существовать бизнес-правило, использующее действие по проверке. Дополнительные сведения см. в разделе [Создание и публикация бизнес-правила (службы Master Data Services)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
-   Пользователь или группа, получающие уведомления, должны иметь разрешения не ниже **Только для чтения** для атрибута, проверка которого завершилась ошибкой. Пользователи или группы, которым явно или неявно отказано в разрешении на атрибут, получат по электронной почте соответствующее сообщение, но не смогут получить доступ к атрибуту в службах [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   Если сообщение электронной почты отправляется группе, то это сообщение получат только те члены группы, которые имеют доступ к службам [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
### <a name="to-configure-business-rules-to-send-notifications"></a>Настройка бизнес-правил для отправки уведомлений  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Бизнес-правила** выберите модель из списка **Модель** .  
  
4.  Из раскрывающегося списка **Сущность** выберите сущность.  
  
5.  Из раскрывающегося списка **Типы элементов** выберите тип элемента.  
  
6.  В сетке выберите строку бизнес-правила, которое нужно изменить, и щелкните **Изменить**.  
  
7.  Установите флажок **Отправлять уведомления** и из раскрывающегося списка выберите пользователя или группу, которым будут отправляться уведомления по электронной почте.  
  
8.  Нажмите кнопку **Сохранить**.  
  
9. Нажмите кнопку **Опубликовать все**.  
  
10. В диалоговом окне подтверждения нажмите кнопку **ОК**. Значение в столбце **Business Rule State** изменится на **Активно** , а в столбце **Уведомление** отобразится пользователь или группа, выбранные для отправки уведомлений.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   Примените бизнес-правила к данным с помощью одной из следующих процедур:  
  
    -   [Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   Настройте протокол электронной почты следующим образом.  
  
    -   [Настройка уведомления электронной почты (службы Master Data Services)](../master-data-services/configure-email-notifications-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Уведомления (службы Master Data Services)](../master-data-services/notifications-master-data-services.md)   
 [Настройка уведомления электронной почты (службы Master Data Services)](../master-data-services/configure-email-notifications-master-data-services.md)  
  
  

