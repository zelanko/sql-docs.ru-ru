---
title: Подтверждение версии, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- validating versions [Master Data Services]
- validating versions [Master Data Services], about validating versions
- versions [Master Data Services], validating
- business rules [Master Data Services], applying to all members
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: e33526df02cff22adbd56bfbfc2f25cef1c1c052
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482312"
---
# <a name="validate-a-version-against-business-rules-master-data-services"></a>Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]проверьте версию на применение бизнес-правил ко всем элементам версии модели.  
  
 В этой процедуре объясняется, как использовать веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] для проверки данных. Если имеется разрешение в базе данных MDS, вместо этого можно использовать хранимую процедуру. Дополнительные сведения см. в разделе [Проверка хранимых процедур (службы Master Data Services)](validation-stored-procedure-master-data-services.md).  
  
> [!NOTE]  
>  Чтобы версию можно было зафиксировать, все элементы должны успешно пройти проверку.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../../2014/master-data-services/administrators-master-data-services.md).  
  
-   Версия должна быть в состоянии **Открыта** или **Заблокирована**.  
  
-   На странице **Проверка версий** должны существовать элементы, состояние которых отличается от **Проверка успешно пройдена**.  
  
### <a name="to-validate-a-version"></a>Проверка версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На странице **Управление версиями** в строке меню щелкните **Проверить версию**.  
  
3.  На странице **Проверка версий** выберите модель и версию, которые необходимо проверить.  
  
4.  Выберите **Проверить**.  
  
5.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
    > [!NOTE]  
    >  Когда исчезнет индикатор выполнения, проверка версии будет закончена.  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Блокировка &#40;версии Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Состояния проверки &#40;Master Data Services&#41;](../../2014/master-data-services/validation-statuses-master-data-services.md)   
 [Master Data Services &#40;хранимой процедуры проверки&#41;](validation-stored-procedure-master-data-services.md)   
 [Версии &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Бизнес-правила &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Проверка конкретных членов на соответствие бизнес-правилам &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  
