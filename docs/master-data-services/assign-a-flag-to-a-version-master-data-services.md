---
title: Назначение флага версии
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], assigning flags
- versions [Master Data Services], assigning flags
ms.assetid: 6629ec7e-32e7-4a1e-8b31-eb43c5923766
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4e8f69d473ff15be3105c8dcef5f51edf30f4302
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729789"
---
# <a name="assign-a-flag-to-a-version-master-data-services"></a>Назначение флага версии (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]назначается флаг версии, чтобы указать версию, которую следует использовать пользователям или системам-подписчикам.  
  
> [!NOTE]  
>  Флаг можно назначить только одной версии в каждый момент времени. Если назначить флаг, уже назначенный другой версии, то он переместится к выбранной версии.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Нужно создать флаг версии для назначения. Дополнительные сведения см. в статье [Create a Version Flag &#40;Master Data Services&#41;](../master-data-services/create-a-version-flag-master-data-services.md).  
  
-   Необходимо иметь разрешение на доступ к функциональной области "Управление версиями". Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### <a name="to-assign-a-flag-to-a-version"></a>Назначение флага версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На странице **Управление версиями** в строке версии, которой необходимо назначить флаг, дважды щелкните ячейку в столбце **Флаг** .  
  
3.  Выберите из списка флаг, который нужно назначить.  
  
    > [!NOTE]  
    >  Если нужный флаг недоступен, то, возможно, он доступен только для **зафиксированных** версий. Чтобы удостовериться в этом, перейдите на страницу **Управление флагами версии** и просмотрите поле **Только зафиксированные версии** флага.  
  
4.  Нажмите клавишу ВВОД, чтобы сохранить изменение.  
  
## <a name="see-also"></a>См. также:  
 [Создание флага версии &#40;Master Data Services&#41;](../master-data-services/create-a-version-flag-master-data-services.md)   
 [Версии &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)  
  
  
