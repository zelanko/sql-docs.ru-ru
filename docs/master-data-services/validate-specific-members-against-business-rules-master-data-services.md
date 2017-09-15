---
title: "Подтверждение конкретных элементов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services) | Документы Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 293a1a5f1614df67cd1a28d88a432cc55a3927b7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a>Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]бизнес-правила можно применять выборочно, если требуется обновить или проверить подмножество элементов с использованием бизнес-правил.  
  
> [!NOTE]  
>  Инструкции о том, как применить бизнес-правила ко всем элементам в версии модели, см. в разделе [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   как минимум требуется разрешение **Обновление** на объект модели, к которому применяются бизнес-правила.  
  
### <a name="to-apply-business-rules-selectively"></a>Выборочное применение бизнес-правил  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в раскрывающемся списке **Модель** .  
  
2.  Выберите версию в раскрывающемся списке **Версия** .  
  
3.  Откройте вкладку **Обозреватель** .  
  
4.  На панели меню наведите курсор на пункт **Сущности** и щелкните имя сущности, содержащей элементы, к которым требуется применить правила.  
  
5.  Нажмите кнопку **Применить правила**. Бизнес-правила применяются только к элементам, отображенным в сетке.  
  
## <a name="see-also"></a>См. также:  
 [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)   
 [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
  
