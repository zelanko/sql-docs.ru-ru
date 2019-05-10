---
title: Подтверждение конкретных элементов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 5b0d7a9965d1453441384b09690be7ac97a7f36c
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65484965"
---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a>Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]бизнес-правила можно применять выборочно, если требуется обновить или проверить подмножество элементов с использованием бизнес-правил.  
  
> [!NOTE]  
>  Инструкции о том, как применить бизнес-правила ко всем элементам в версии модели, см. в разделе [проверка версии на соответствие бизнес-правила &#40;службы Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md).  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   как минимум требуется разрешение **Обновление** на объект модели, к которому применяются бизнес-правила.  
  
### <a name="to-apply-business-rules-selectively"></a>Выборочное применение бизнес-правил  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в раскрывающемся списке **Модель** .  
  
2.  Выберите версию в раскрывающемся списке **Версия** .  
  
3.  Откройте вкладку **Обозреватель** .  
  
4.  На панели меню наведите курсор на пункт **Сущности** и щелкните имя сущности, содержащей элементы, к которым требуется применить правила.  
  
5.  Нажмите кнопку **Применить правила**. Бизнес-правила применяются только к элементам, отображенным в сетке.  
  
## <a name="see-also"></a>См. также  
 [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)   
 [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
  
