---
title: Проверка (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 98eb49e7-b190-4a21-8316-08c07cde14ed
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 0ba00faa58a4ac37c2c1c574000b028333f2bd52
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308024"
---
# <a name="validation-master-data-services"></a>Проверка (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]данные проверяются для обеспечения их точности. Одни проверки происходят автоматически, а другие основываются на бизнес-правилах, созданных администраторами.  
  
## <a name="when-data-validation-occurs"></a>Время проведения проверки данных  
 Проверка происходит в разное время и отображается по-разному в веб-приложении [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
|Тип проверки|Кто определяет стандарты|Когда происходят|Отображается в веб-интерфейсе диспетчера основных данных как|Отображается в надстройке Excel как|Сохраняются ли данные в репозитории MDS?|  
|---------------------|-----------------------------|--------------------|---------------------------------------------------|-------------------------------------------|------------------------------------------|  
|Проверка бизнес-правил|Администратор MDS|Автоматически при добавлении или изменении данных пользователем<br /><br /> Вручную, когда пользователь применяет бизнес-правила.<br /><br /> Вручную, когда администратор в функциональной зоне **Управление версиями** веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] проверяет версию на соответствие бизнес-правилам.|Ошибки проверки|ValidationStatus|Да|  
|Проверка типа данных и содержимого|Администратор служб MDS при создании объектов модели (например, длины атрибутов или типов данных)|Автоматически при добавлении или изменении данных пользователем|Ошибки ввода данных|InputStatus|Нет|  
|Проверка типа данных и содержимого|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] либо [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|Автоматически при добавлении или изменении данных пользователем|Ошибки ввода данных|InputStatus|Нет|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание бизнес-правил и их публикация для проверки данных на соответствие этим правилам.|[Создание и публикация бизнес-правила &#40;службы Master Data Services&#41;](create-and-publish-a-business-rule-master-data-services.md)|  
|Проверка версии данных на соответствие бизнес-правилам. Только администратор.|[Проверка версии на соответствие бизнес-правила &#40;службы Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)|  
|Проверка конкретных подмножеств данных на соответствие бизнес-правилам. Все пользователи с разрешением на доступ к функциональной области **Обозреватель** .|[Проверка конкретных членов, соответствие бизнес-правилам &#40;службы Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|Проверка конкретных подмножеств данных на соответствие бизнес-правилам. Все пользователи с разрешением на доступ к функциональной области **Обозреватель** с помощью [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].|[Применение бизнес-правил &#40;надстройка MDS для Excel&#41;](microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
  
## <a name="see-also"></a>См. также  
 [Бизнес-правила &#40;службы Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
