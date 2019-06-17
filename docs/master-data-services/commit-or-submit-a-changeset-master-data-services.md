---
title: Фиксация или отправка набора изменений (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d323bbac-c8d4-4d2f-a7d2-a597e8b53e2d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: a316174a4550260a7ed6243a9e1ae93127ef510b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65484452"
---
# <a name="commit-or-submit-a-changeset-master-data-services"></a>Фиксация или отправка набора изменений (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Набор изменений — это совокупность ожидающих изменений основных данных. Если изменения сущности не требуют утверждения администратором, набор изменений можно зафиксировать. Если изменения сущности требуют утверждения администратором, набор изменений можно отправить на утверждение.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** . Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Если изменения сущности не требуют утверждения администратором, набор изменений можно зафиксировать, только если вы являетесь его владельцем, а сам набор находится в открытом состоянии.  
  
-   Если изменения сущности требуют утверждения администратором, набор изменений можно отправить на утверждение, только если вы являетесь его владельцем, а сам набор находится в открытом или отклоненном состоянии.  
  
## <a name="to-commit-a-local-changeset"></a>Фиксация локального набора изменений  
 Параметр фиксации доступен только для локальных наборов изменений в сущностях, для которых администратор сущностей не включил обязательное утверждение.  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель и версию, а затем щелкните **Обозреватель**.  
  
2.  Щелкните сущность в меню **Сущности** .  
  
3.  В области справа выберите **Наборы изменений** и дважды щелкните набор изменений, который следует зафиксировать.  
  
4.  Нажмите кнопку **Зафиксировать**.  
  
## <a name="to-submit-a-changeset"></a>Отправка набора изменений  
 Параметр отправки доступен только для наборов изменений в сущностях, для которых администратор сущностей не включил обязательное утверждение.  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель и версию, а затем щелкните **Обозреватель**.  
  
2.  Щелкните сущность в меню **Сущности** .  
  
3.  В области справа выберите **Наборы изменений** и дважды щелкните набор изменений, который следует отправить.  
  
4.  Щелкните **Отправить**.  
  
## <a name="next-steps"></a>Next Steps  
 [Утверждение или отклонение набора изменений (Master Data Services)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Создание набора изменений (Master Data Services)](../master-data-services/create-a-changeset-master-data-services.md)   
 [Применение и обновление набора изменений (службы Master Data Services)](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [Утверждение или отклонение набора изменений (Master Data Services)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  
