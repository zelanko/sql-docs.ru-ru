---
title: "Наборы изменений (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f227c49a-ed46-4e0f-8992-83093456cf94
caps.latest.revision: "13"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4ac9a4b15d48f9c5f9ac9a25a932d9acec798e31
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="changesets-master-data-services"></a>Наборы изменений (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] теперь поддерживает возможность сохранения любых ожидающих изменений в сущности в качестве набора изменений. Существует два сценария использования этой возможности.  
  
-   **Сохранение изменений, если функция "Требуется утверждение" включена администратором сущности**  
  
     Если администратор сущности указал, что изменения в данную сущность требуют утверждения перед фиксацией, эти изменения должны сохраняться в новом или существующем наборе изменений перед отправкой на утверждение.  Дополнительные сведения см. в разделе [Требуется утверждение (службы Master Data Services)](../master-data-services/approval-required-master-data-services.md).  
  
     Потребуется выполнить описанный ниже рабочий процесс.  
  
    1.  Создайте набор изменений. Набор изменений находится в открытом состоянии. См. раздел [Создание набора изменений (Master Data Services)](../master-data-services/create-a-changeset-master-data-services.md)  
  
    2.  Примените набор изменений и добавьте в него изменения. См. раздел [Применение и обновление набора изменений (Master Data Services)](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
    3.  Отправьте набор изменений администратору сущности на утверждение. Набор изменений находится в состоянии ожидания. См. раздел [Фиксация или отправка набора изменений (Master Data Services)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
    4.  Администратор сущности получает по электронной почте уведомление о том, что набор изменений ожидает утверждения. Если администратор сущности утверждает набор изменений, набор переходит в состояние "Утверждено". См. раздел [Утверждение или отклонение набора изменений (Master Data Services)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
    5.  Утвержденный набор изменений фиксируется автоматически. Если изменений успешно зафиксировано, набор изменений переходит в состояние "Зафиксировано".  
  
-   **Изменения локального пользователя**  
  
     Если нужно сохранить локальные изменения, чтобы их можно было использовать или извлечь позднее, для этого можно воспользоваться наборами изменений.  
  
     Потребуется выполнить описанный ниже рабочий процесс.  
  
    1.  Создайте набор изменений. Набор изменений находится в открытом состоянии. См. раздел [Создание набора изменений (Master Data Services)](../master-data-services/create-a-changeset-master-data-services.md)  
  
    2.  Примените набор изменений и добавьте в него изменения. См. раздел [Применение и обновление набора изменений (Master Data Services)](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
    3.  Когда все будет готово, можно зафиксировать набор изменений. См. раздел [Фиксация или отправка набора изменений (Master Data Services)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Создание набора изменений (Master Data Services)](../master-data-services/create-a-changeset-master-data-services.md)   
 [Применение и обновление набора изменений (службы Master Data Services)](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [Фиксация или отправка набора изменений (Master Data Services)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [Утверждение или отклонение набора изменений (службы Master Data Services)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)   
 [Управление наборами изменений (службы Master Data Services)](../master-data-services/manage-changesets-master-data-services.md)  
  
  
