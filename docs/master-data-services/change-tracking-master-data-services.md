---
title: Отслеживание изменений (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 2a0eed4be0b2469a0bb9157fbc9406937aaed269
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="change-tracking-master-data-services"></a>Отслеживание изменений (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно использовать группы отслеживания изменений для выполнения действий при изменении значения атрибутов. Используйте отслеживание изменений, если неизвестно, каким будет новое значение, но необходимо узнать, произошло ли какое-либо изменение.  
  
## <a name="configuring-change-tracking"></a>Настройка отслеживания изменений  
 Для настройки отслеживания изменений добавьте атрибут в группу отслеживания изменений. Группа может содержать один или несколько атрибутов. Далее создайте бизнес-правило, определяющее, какое действие будет предпринято в случае, если атрибуты в группе изменяются.  
  
> [!NOTE]  
>  Бизнес-правила, отслеживающие изменения, считают промежуточные (импортированные) данные, измененными.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Добавление атрибутов в группу отслеживания изменений.|[Добавление атрибутов в группу отслеживания изменений (службы Master Data Services)](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Создание бизнес-правила для инициации действий на основе изменений атрибута.|[Инициирование действия на основе значения атрибута (службы Master Data Services)](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Проверка (службы Master Data Services)](../master-data-services/validation-master-data-services.md)  
  
-   [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
-   [Атрибуты (службы Master Data Services)](../master-data-services/attributes-master-data-services.md)  
  
  
