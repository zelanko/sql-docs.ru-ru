---
title: Блокировка версии (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: e38a4c75ad6cf8c65d7120e0eb98163f7ee0fccc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482876"
---
# <a name="lock-a-version-master-data-services"></a>Блокировка версии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]блокировка версии модели препятствует изменениям элементов модели и их атрибутов.  
  
> [!NOTE]  
>  Если версия заблокирована, администраторы модели могут по-прежнему добавлять, изменять и удалять элементы. Другие пользователи с разрешениями для модели могут только просматривать элементы.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](administrators-master-data-services.md).  
  
-   Версия должна быть в состоянии **Открыта**.  
  
### <a name="to-lock-a-version"></a>Блокировка версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На странице **Управление версиями** выберите строки для версии, которую необходимо заблокировать.  
  
3.  Выберите пункт **Блокировка**.  
  
4.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Проверка версии на соответствие бизнес-правилам &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [Фиксация &#40;версии Master Data Services&#41;](../../2014/master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Версии &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Разблокировка версии Master Data Services &#40;&#41;](../../2014/master-data-services/unlock-a-version-master-data-services.md)  
  
  
