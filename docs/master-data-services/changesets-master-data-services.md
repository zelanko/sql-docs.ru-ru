---
title: Наборы изменений
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f227c49a-ed46-4e0f-8992-83093456cf94
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6d8c277796f743b31dfb5df349352bb6c7470421
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728628"
---
# <a name="changesets-master-data-services"></a>Наборы изменений (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] теперь поддерживает возможность сохранения любых ожидающих изменений в сущности в качестве набора изменений. Существует два сценария использования этой возможности.  
  
-   **Изменяется, если администратор сущностей включил утверждение "обязательно".**  
  
     Если администратор сущности указал, что изменения в данную сущность требуют утверждения перед фиксацией, эти изменения должны сохраняться в новом или существующем наборе изменений перед отправкой на утверждение.  Дополнительные сведения см. в разделе [Требуется утверждение (службы Master Data Services)](../master-data-services/approval-required-master-data-services.md).  
  
     Потребуется выполнить описанный ниже рабочий процесс.  
  
    1.  Создайте набор изменений. Набор изменений находится в открытом состоянии. См. раздел [Создание набора изменений (Master Data Services)](../master-data-services/create-a-changeset-master-data-services.md)  
  
    2.  Примените набор изменений и добавьте в него изменения. См. раздел [Применение и обновление набора изменений &#40;службы Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
    3.  Отправьте набор изменений администратору сущности на утверждение. Набор изменений находится в состоянии ожидания. См. раздел [Фиксация или отправка набора изменений (Master Data Services)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
    4.  Администратор сущности получает по электронной почте уведомление о том, что набор изменений ожидает утверждения. Если администратор сущности утверждает набор изменений, набор переходит в состояние "Утверждено". См. раздел [Утверждение или отклонение набора изменений (Master Data Services)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
    5.  Утвержденный набор изменений фиксируется автоматически. Если изменений успешно зафиксировано, набор изменений переходит в состояние "Зафиксировано".  
  
-   **Изменения локальных пользователей**  
  
     Если нужно сохранить локальные изменения, чтобы их можно было использовать или извлечь позднее, для этого можно воспользоваться наборами изменений.  
  
     Потребуется выполнить описанный ниже рабочий процесс.  
  
    1.  Создайте набор изменений. Набор изменений находится в открытом состоянии. См. раздел [Создание набора изменений (Master Data Services)](../master-data-services/create-a-changeset-master-data-services.md)  
  
    2.  Примените набор изменений и добавьте в него изменения. См. раздел [Применение и обновление набора изменений &#40;службы Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
    3.  Когда все будет готово, можно зафиксировать набор изменений. См. раздел [Фиксация или отправка набора изменений (Master Data Services)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Создание набора изменений &#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)   
 [Примените и обновите набор изменений &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [Фиксация или отправка набора изменений &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [Утверждение или отклонение набора изменений &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)   
 [Управление наборами изменений &#40;Master Data Services&#41;](../master-data-services/manage-changesets-master-data-services.md)  
  
  
