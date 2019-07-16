---
title: Добавление нескольких условий к бизнес-правилу (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bc678925ca35260131b318a1c3f674f5157a1fe5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68047839"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a>Добавление нескольких условий к бизнес-правилу (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Чтобы в среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]создать более сложное бизнес-правило, к нему с помощью операторов **AND** и **OR** можно добавить несколько условий.  
  
> [!NOTE]  
>  Если в создаваемом бизнес-правиле используется оператор **OR** , рассмотрите возможность создания отдельного правила для каждой из условных инструкций, которые можно применить независимо. При необходимости правила можно исключать, что повышает гибкость и упрощает устранение неполадок.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Должно существовать бизнес-правило. Дополнительные сведения см. в разделе [Создание и публикация бизнес-правила (службы Master Data Services)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a>Добавление нескольких условий в бизнес-правило  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Бизнес-правила** в раскрывающемся списке **Модель** выберите модель.  
  
4.  Из раскрывающегося списка **Сущность** выберите сущность.  
  
5.  Из раскрывающегося списка **Типы элементов** выберите тип элемента.  
  
6.  Щелкните строку, где указано бизнес-правило, которое требуется изменить.  
  
7.  Нажмите кнопку **Изменить**.  
  
8.  В блоке **Если** слева от раскрывающегося списка логических операторов выберите **И/ИЛИ/НЕ**.  
  
9. Нажмите кнопку **Добавить**. Отобразится панель.  
  
10. Из раскрывающегося списка **Атрибут** выберите атрибут.  
  
11. В раскрывающемся списке **Оператор** выберите условие.  
  
12. Заполните необходимые поля.  
  
13. Нажмите кнопку **Сохранить**. В сетку **If** будет добавлена новая строка.  
  
14. При необходимости добавьте дополнительные условия, выполнив шаги 8–13.  
  
    > [!TIP]  
    >  Чтобы удалить условие, щелкните его правой кнопкой мыши и выберите команду **Удалить**.  
  
    > [!TIP]  
    >  Можно выбрать несколько условий и щелчком правой кнопкой мыши сгруппировать их внутри логического оператора. Кроме того, можно разгруппировать условия, содержащиеся в определенном логическом операторе.  
  
## <a name="see-also"></a>См. также  
 [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)   
 [Изменение имени бизнес-правила (службы Master Data Services)](../master-data-services/change-a-business-rule-name-master-data-services.md)   
 [Настройка в бизнес-правилах отправки уведомлений (службы Master Data Services)](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
