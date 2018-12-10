---
title: Отслеживание изменений (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: fbaf6c28b551b65473784e231716c58f974e7962
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52395367"
---
# <a name="change-tracking-master-data-services"></a>Отслеживание изменений (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно использовать группы отслеживания изменений для выполнения действий при изменении значения атрибутов. Используйте отслеживание изменений, если неизвестно, каким будет новое значение, но необходимо узнать, произошло ли какое-либо изменение.  
  
## <a name="configuring-change-tracking"></a>Настройка отслеживания изменений  
 Для настройки отслеживания изменений добавьте атрибут в группу отслеживания изменений. Группа может содержать один или несколько атрибутов. Далее создайте бизнес-правило, определяющее, какое действие будет предпринято в случае, если атрибуты в группе изменяются.  
  
> [!NOTE]  
>  Бизнес-правила, отслеживающие изменения, считают промежуточные (импортированные) данные, измененными.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Добавление атрибутов в группу отслеживания изменений.|[Добавление атрибутов в группу отслеживания изменений (службы Master Data Services)](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Создание бизнес-правила для инициации действий на основе изменений атрибута.|[Инициирование действия на основе значения атрибута (службы Master Data Services)](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Проверка (службы Master Data Services)](../master-data-services/validation-master-data-services.md)  
  
-   [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
-   [Атрибуты (службы Master Data Services)](../master-data-services/attributes-master-data-services.md)  
  
  
