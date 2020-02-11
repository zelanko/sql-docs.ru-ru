---
title: Блокировка версии
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 693eeda37e65dbf1d83fdf59eaf546e711827b7e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728057"
---
# <a name="lock-a-version-master-data-services"></a>Блокировка версии (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]блокировка версии модели препятствует изменениям элементов модели и их атрибутов.  
  
> [!NOTE]  
>  Если версия заблокирована, суперпользователи и администраторы модели по-прежнему могут добавлять, изменять и удалять элементы. Другие пользователи с разрешениями для модели могут только просматривать элементы.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Версия должна быть в состоянии **Открыта**.  
  
-   Необходимо иметь разрешение на доступ к функциональной области "Управление версиями". Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### <a name="to-lock-a-version"></a>Блокировка версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На странице **Управление версиями** выберите строки для версии, которую необходимо заблокировать.  
  
3.  Выберите пункт **Блокировка**.  
  
4.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Проверка версии на соответствие бизнес-правилам &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [Фиксация &#40;версии Master Data Services&#41;](../master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Версии &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)   
 [Разблокировка версии Master Data Services &#40;&#41;](../master-data-services/unlock-a-version-master-data-services.md)  
  
  
