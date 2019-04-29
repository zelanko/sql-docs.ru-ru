---
title: Подтверждение конкретных элементов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c2cded1fccc1e6d6ee5229fbec0c786ab35170de
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923221"
---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a>Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]бизнес-правила можно применять выборочно, если требуется обновить или проверить подмножество элементов с использованием бизнес-правил.  
  
> [!NOTE]  
>  Инструкции о том, как применить бизнес-правила ко всем элементам в версии модели, см. в разделе [проверка версии на соответствие бизнес-правила &#40;службы Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   как минимум требуется разрешение **Обновление** на объект модели, к которому применяются бизнес-правила.  
  
### <a name="to-apply-business-rules-selectively"></a>Выборочное применение бизнес-правил  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в списке **Модель** .  
  
2.  Выберите версию из списка **Версия** .  
  
3.  Нажмите кнопку **Браузер**.  
  
4.  На панели меню наведите курсор на пункт **Сущности** и щелкните имя сущности, содержащей элементы, к которым требуется применить правила.  
  
5.  Нажмите кнопку **Применить бизнес-правила**. Бизнес-правила применяются только к элементам, отображенным в сетке.  
  
## <a name="see-also"></a>См. также  
 [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](validate-a-version-against-business-rules-master-data-services.md)   
 [Бизнес-правила (службы Master Data Services)](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
