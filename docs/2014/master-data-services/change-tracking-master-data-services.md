---
title: Отслеживание изменений (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7b4b7d9d9d153456ca471196c6480465d057e412
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65483523"
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
|Добавление атрибутов в группу отслеживания изменений.|[Добавление атрибутов в группу Отслеживание изменений &#40;Master Data Services&#41;](add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Создание бизнес-правила для инициации действий на основе изменений атрибута.|[Инициируйте действия на основе изменений значений атрибутов &#40;Master Data Services&#41;](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Master Data Services &#40;проверки&#41;](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [Бизнес-правила &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [Master Data Services &#40;атрибутов&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
