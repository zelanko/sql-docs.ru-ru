---
title: Фиксация версии
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0fa359de1daa844fbcce073b0c67efdd5f721b37
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73728591"
---
# <a name="commit-a-version-master-data-services"></a>Фиксация версии (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]фиксация версии модели препятствует изменениям элементов модели и их атрибутов. Открыть зафиксированную версию нельзя.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Версия должна иметь состояние **Заблокирована**. Дополнительные сведения см. в статье [Блокировка версии (службы Master Data Services)](../master-data-services/lock-a-version-master-data-services.md).  
  
-   Все элементы должны пройти проверку.  
  
-   Необходимо иметь разрешение на доступ к функциональной области "Управление версиями". Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### <a name="to-commit-a-version"></a>Фиксация версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На странице **Управление версиями** в строке меню щелкните **Проверить версию**.  
  
3.  На странице **Проверка версии** выберите модель и версию, которые необходимо зафиксировать.  
  
4.  Нажмите кнопку **Зафиксировать**.  
  
5.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Создание флага версии (службы Master Data Services)](../master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [Назначение флага версии (службы Master Data Services)](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [Копирование версии (службы Master Data Services)](../master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a>См. также раздел  
 [Версии (службы Master Data Services)](../master-data-services/versions-master-data-services.md)  
  
  
