---
title: Проверка (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98eb49e7-b190-4a21-8316-08c07cde14ed
caps.latest.revision: 12
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 51cd2182820113030bdeb060ddc17997d93c2fda
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="validation-master-data-services"></a>Проверка (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]данные проверяются для обеспечения их точности. Одни проверки происходят автоматически, а другие основываются на бизнес-правилах, созданных администраторами.  
  
## <a name="when-data-validation-occurs"></a>Время проведения проверки данных  
 Проверка происходит в разное время и отображается по-разному в веб-приложении [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
|Тип проверки|Кто определяет стандарты|Когда происходят|Отображается в веб-интерфейсе диспетчера основных данных как|Отображается в надстройке Excel как|Сохраняются ли данные в репозитории MDS?|  
|---------------------|-----------------------------|--------------------|---------------------------------------------------|-------------------------------------------|------------------------------------------|  
|Проверка бизнес-правил|Администратор MDS|Автоматически при добавлении или изменении данных пользователем<br /><br /> Вручную, когда пользователь применяет бизнес-правила.<br /><br /> Вручную, когда администратор в функциональной зоне **Управление версиями** веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] проверяет версию на соответствие бизнес-правилам.|Ошибки проверки|ValidationStatus|Да|  
|Проверка типа данных и содержимого|Администратор служб MDS при создании объектов модели (например, длины атрибутов или типов данных)|Автоматически при добавлении или изменении данных пользователем|Ошибки ввода данных|InputStatus|нет|  
|Проверка типа данных и содержимого|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] либо [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|Автоматически при добавлении или изменении данных пользователем|Ошибки ввода данных|InputStatus|нет|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание бизнес-правил и их публикация для проверки данных на соответствие этим правилам.|[Создание и публикация бизнес-правила (службы Master Data Services)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|Проверка версии данных на соответствие бизнес-правилам. Только администратор.|[Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)|  
|Проверка конкретных подмножеств данных на соответствие бизнес-правилам. Все пользователи с разрешением на доступ к функциональной области **Обозреватель** .|[Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|Проверка конкретных подмножеств данных на соответствие бизнес-правилам. Все пользователи с разрешением на доступ к функциональной области **Обозреватель** с помощью [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].|[Применение бизнес-правил (надстройка MDS для Excel)](../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
  
## <a name="see-also"></a>См. также:  
 [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
  
