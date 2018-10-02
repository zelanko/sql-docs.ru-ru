---
title: Запрос значений атрибута (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
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
ms.openlocfilehash: 7fea1898e2f497a523a38f4da97a16f3f8110d07
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631472"
---
# <a name="require-attribute-values-master-data-services"></a>Запрос значений атрибута (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]значения атрибута запрашиваются для гарантии завершенности основных данных.  
  
> [!NOTE]  
>  Если у элемента не хватает значения атрибута на основе домена, то этот элемент не отображается в производной иерархии, основанной на этих связях.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-require-attribute-values"></a>Запрос значения атрибута  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Бизнес-правила** в раскрывающемся списке **Модель** выберите модель.  
  
4.  Из раскрывающегося списка **Сущность** выберите сущность.  
  
5.  Из раскрывающегося списка **Тип элемента** выберите тип элемента, к которому будет применяться бизнес-правило.  
  
6.  Нажмите кнопку **Добавить**.  
  
7.  Введите имя бизнес-правила в поле **Имя** .  
  
8.  При необходимости в поле **Описание** введите описание бизнес-правила.  
  
9. В разделе **Then** нажмите кнопку **Добавить**. Отобразится панель.  
  
10. Из раскрывающегося списка **Оператор** выберите **необходимое действие**.  
  
11. Из раскрывающегося списка **Атрибут** выберите атрибут.  
  
12. Нажмите кнопку **Сохранить**. В сетку **Then** будет добавлена новая строка.  
  
13. Нажмите кнопку **Сохранить**.  
  
14. Нажмите кнопку **Опубликовать все**.  
  
15. В диалоговом окне подтверждения нажмите кнопку **ОК**. Значение в столбце **Состояние бизнес-правила** изменится на **Активно**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   Примените бизнес-правила к данным с помощью одной из следующих процедур:  
  
    -   [Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)   
 [Производные иерархии (службы Master Data Services)](../master-data-services/derived-hierarchies-master-data-services.md)  
  
  
