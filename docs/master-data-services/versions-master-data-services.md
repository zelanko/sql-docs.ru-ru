---
title: "Версии (службы Master Data Services) | Документы Майкрософт"
ms.custom: SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version flags [Master Data Services], about version flags
- versions [Master Data Services]
- version flags [Master Data Services]
- versions [Master Data Services], version flags
ms.assetid: 752ec96d-53d7-4160-8ed2-92e0324645f3
caps.latest.revision: "9"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a34f0a2c975911fce99d60afeaf7a57123556e93
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="versions-master-data-services"></a>Версии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно создать несколько версий основных данных в модели. Версии могут быть заблокированы до проведения проверки данных и будут зафиксированы после проверки данных. Зафиксированные версии образуют запись аудита об изменениях. Каждая созданная версия содержит все элементы, значения атрибутов, элементы иерархии, отношения в иерархии и коллекции для модели.  
  
## <a name="when-to-use-versions"></a>Использование версий  
 Версии используются:  
  
-   для ведения доступной для аудита записи основных данных при их изменении;  
  
-   предотвращения изменений пользователями и обеспечения допустимости данных в соответствии с бизнес-правилами;  
  
-   блокировки модели для использования системами-подписчиками;  
  
-   проверки разных иерархий без немедленной их реализации.  
  
> [!NOTE]  
>  При изменении структуры модели, например при создании новой сущности или атрибута на основе домена, это изменение применяется ко всем версиям. Если просматривается более ранняя версия модели, то сущность или атрибут отображается, но для него отсутствуют данные.  
  
## <a name="version-flags"></a>Флаги версии  
 Когда версия готова для пользователей или системы-подписчика, можно установить флаг для идентификации версии. При необходимости этот флаг можно переносить от версии к версии. Флаги помогают пользователям и системам-подписчикам определять используемую версию модели.  
  
## <a name="workflow-for-version-management"></a>Рабочий процесс для управления версией  
 Используйте следующий рабочий процесс для управления версиями:  
  
1.  Начальная версия создается автоматически при создании модели и наполнении базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] основными данными компании. На основании разрешений пользователи могут при необходимости вносить изменения в эту версию.  
  
2.  Когда необходимо зафиксировать версию модели, заблокируйте ее, чтобы только администраторы модели могли обновлять данные. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md). Если настраиваются уведомления, то администратору модели по электронной почте направляются уведомления каждый раз, когда изменяется состояние версии. Дополнительные сведения см. в разделе [Настройка уведомления электронной почты (службы Master Data Services)](../master-data-services/configure-email-notifications-master-data-services.md).  
  
3.  Примените бизнес-правила к данным заблокированной версии и просмотрите все ошибки, обнаруженные при проверке. При необходимости можно внести отсутствующие данные или восстановить транзакции, которые привели к возникновению ошибки. Можно также разблокировать версию, чтобы пользователи могли вносить изменения.  
  
4.  После успешной проверки всех данных зафиксируйте версию и пометьте для использования системами-подписчиками. Вносить изменения в зафиксированную версию нельзя.  
  
5.  Скопируйте зафиксированную версию и уведомите пользователей, что они могут начать работать с новой версией модели.  
  
## <a name="sequential-or-simultaneous-versions"></a>Последовательные или одновременные версии  
 Можно создавать последовательные или одновременные версии модели.  
  
-   **Последовательные версии.** Каждый раз при фиксации версии можно создать новую копию и назначить версии следующий последовательный номер. Например, можно скопировать **Версию 7** модели и назвать копию **Версия 8**.  
  
-   **Одновременные версии.** При необходимости работать с одной или несколькими версиями данных одновременно создайте одновременные версии модели. Это полезно, когда в компании происходят реорганизации или слияния, которые осуществляются в ходе обычной деятельности компании, и необходимо определить, как новые основные данные подойдут к существующим структурам.  
  
    > [!NOTE]  
    >  Параметр в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] определяет возможность копирования для всех версий или только для зафиксированных. Для создания одновременных версий необходимо выполнить настройку [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , чтобы можно было скопировать все версии. Этот параметр также присутствует в таблице системных настроек. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Изменение имени существующей версии.|[Изменение имени версии (службы Master Data Services)](../master-data-services/change-a-version-name-master-data-services.md)|  
|Блокирование версии, чтобы изменять ее данные могли только администраторы.|[Блокировка версии (службы Master Data Services)](../master-data-services/lock-a-version-master-data-services.md)|  
|Разблокирование версии, чтобы изменять ее данные могли пользователи.|[Разблокировка версии (службы Master Data Services)](../master-data-services/unlock-a-version-master-data-services.md)|  
|Фиксирование версии после проверки всех данных.|[Фиксация версии (службы Master Data Services)](../master-data-services/commit-a-version-master-data-services.md)|  
|Создание нового флага для обозначения версии.|[Создание флага версии (службы Master Data Services)](../master-data-services/create-a-version-flag-master-data-services.md)|  
|Изменение имени для существующего флага версии.|[Изменение имени флага версии (службы Master Data Services)](../master-data-services/change-a-version-flag-name-master-data-services.md)|  
|Назначение существующего флага для версии.|[Назначение флага версии (службы Master Data Services)](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)|  
|Создание новой копии для существующей версии|[Копирование версии (службы Master Data Services)](../master-data-services/copy-a-version-master-data-services.md)|  
|Удаление существующей версии.|[Удаление версии (службы Master Data Services)](../master-data-services/delete-a-version-master-data-services.md)|  
|Очистка обратимо удаленных элементов из версии|[Очистка элементов версии (Master Data Services)](../master-data-services/purge-version-members-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Отмена транзакции (службы Master Data Services)](../master-data-services/reverse-a-transaction-master-data-services.md)  
  
-   [Уведомления (службы Master Data Services)](../master-data-services/notifications-master-data-services.md)  
  
-   [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
  
