---
title: "Изменение отслеживания (Master Data Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6851da978ab681f0236bc9737e7f628c0089abe0
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="change-tracking-master-data-services"></a>Отслеживание изменений (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно использовать группы отслеживания изменений для выполнения действий при изменении значения атрибутов. Используйте отслеживание изменений, если неизвестно, каким будет новое значение, но необходимо узнать, произошло ли какое-либо изменение.  
  
## <a name="configuring-change-tracking"></a>Настройка отслеживания изменений  
 Для настройки отслеживания изменений добавьте атрибут в группу отслеживания изменений. Группа может содержать один или несколько атрибутов. Далее создайте бизнес-правило, определяющее, какое действие будет предпринято в случае, если атрибуты в группе изменяются.  
  
> [!NOTE]  
>  Бизнес-правила, отслеживающие изменения, считают промежуточные (импортированные) данные, измененными.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Добавление атрибутов в группу отслеживания изменений.|[Добавление атрибутов в группу отслеживания изменений & #40; Службы Master Data Services & #41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Создание бизнес-правила для инициации действий на основе изменений атрибута.|[Запуск действия в зависимости от значения атрибута & #40; Службы Master Data Services & #41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Проверка & #40; Службы Master Data Services & #41;](../master-data-services/validation-master-data-services.md)  
  
-   [Бизнес-правила & #40; Службы Master Data Services & #41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [Атрибуты & #40; Службы Master Data Services & #41;](../master-data-services/attributes-master-data-services.md)  
  
  
