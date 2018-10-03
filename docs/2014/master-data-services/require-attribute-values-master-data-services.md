---
title: Запрос значений атрибута (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], requiring attribute values
- attributes [Master Data Services], requiring values
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1e4c2932102892326ad159d5db1901873d1f22d6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072824"
---
# <a name="require-attribute-values-master-data-services"></a>Запрос значений атрибута (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]значения атрибута запрашиваются для гарантии завершенности основных данных.  
  
> [!NOTE]  
>  Если у элемента не хватает значения атрибута на основе домена, то этот элемент не отображается в производной иерархии, основанной на этих связях.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-require-attribute-values"></a>Запрос значения атрибута  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Обслуживание бизнес-правил** выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  В списке **Тип элемента** выберите тип элемента, к которому будет применяться бизнес-правило.  
  
6.  Выберите из списка **Атрибут** атрибут или оставьте **Все**по умолчанию.  
  
7.  Нажмите **Добавить бизнес-правило**.  
  
8.  Нажмите **Изменить выбранное бизнес-правило**.  
  
9. На панели **Компоненты** разверните узел **Действия** .  
  
10. Нажмите кнопку **требуется** и перетащите его на значок **ЗАТЕМ** области **действие** метки.  
  
11. На панели **Атрибуты** щелкните атрибут и перетащите его на значок **Выбор атрибута** панели **Изменение действия** .  
  
12. На панели **Изменение действия** нажмите кнопку **Сохранить элемент**.  
  
13. Нажмите кнопку **Назад**.  
  
14. По желанию на странице **Обслуживание бизнес-правил** дважды щелкните ячейку столбца **Имя**, **Описание**или **Уведомление** , чтобы обновить значение.  
  
15. Нажмите кнопку **Опубликовать бизнес-правила**.  
  
16. В диалоговом окне подтверждения нажмите кнопку **ОК**. Состояние правила изменится на **Активно**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   Примените бизнес-правила к данным с помощью одной из следующих процедур:  
  
    -   [Проверка конкретных членов, соответствие бизнес-правилам &#40;службы Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Проверка версии на соответствие бизнес-правила &#40;службы Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>См. также  
 [Бизнес-правила &#40;службы Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Производные иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
