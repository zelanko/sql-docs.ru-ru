---
title: "Подтверждение версии, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating versions [Master Data Services]
- validating versions [Master Data Services], about validating versions
- versions [Master Data Services], validating
- business rules [Master Data Services], applying to all members
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
caps.latest.revision: 8
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 2a31c8b91872276636addc25c673f07ba5b11bc7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="validate-a-version-against-business-rules-master-data-services"></a>Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]проверьте версию на применение бизнес-правил ко всем элементам версии модели.  
  
 В этой процедуре объясняется, как использовать веб-приложение [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] для проверки данных. Если имеется разрешение в базе данных MDS, вместо этого можно использовать хранимую процедуру. Дополнительные сведения см. в разделе [Проверка хранимых процедур (службы Master Data Services)](../master-data-services/validation-stored-procedure-master-data-services.md).  
  
> [!NOTE]  
>  Чтобы версию можно было зафиксировать, все элементы должны успешно пройти проверку.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Версия должна быть в состоянии **Открыта** или **Заблокирована**.  
  
-   На странице **Проверка версий** должны существовать элементы, состояние которых отличается от **Проверка успешно пройдена**.  
  
### <a name="to-validate-a-version"></a>Проверка версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На странице **Управление версиями** в строке меню щелкните **Проверить версию**.  
  
3.  На странице **Проверка версий** выберите модель и версию, которые необходимо проверить.  
  
4.  Нажмите кнопку **Проверить**.  
  
5.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
    > [!NOTE]  
    >  Когда исчезнет индикатор выполнения, проверка версии будет закончена.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Блокировка версии (службы Master Data Services)](../master-data-services/lock-a-version-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Состояния проверки (службы Master Data Services)](../master-data-services/validation-statuses-master-data-services.md)   
 [Проверка хранимых процедур (службы Master Data Services)](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Версии (службы Master Data Services)](../master-data-services/versions-master-data-services.md)   
 [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)   
 [Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  
