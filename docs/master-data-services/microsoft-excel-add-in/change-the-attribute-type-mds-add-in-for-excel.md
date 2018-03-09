---
title: "Изменение типа атрибута (надстройка MDS для Excel) | Документы Майкрософт"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: microsoft-excel-add-in
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ede0bc3fbc929686d8e1f083a1762cae6a621f5d
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="change-the-attribute-type-mds-add-in-for-excel"></a>Изменение типа атрибута (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]администраторы могут изменить тип атрибута, если тип данных или количество допустимых символов являются неверными.  
  
 Если необходимо изменить тип атрибута для создания ограниченного списка (атрибут на основе домена), см. раздел [Создание атрибута на основе домена (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/create-a-domain-based-attribute-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  Нельзя изменить тип или длину столбцов **Имя** или **Код**.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональным областям **Администрирование системы** и **Обозреватель** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](../../master-data-services/administrators-master-data-services.md).  
  
-   должны быть существующие модель, сущность и атрибут.  
  
### <a name="to-change-the-attribute-type"></a>Изменение типа атрибута  
  
1.  В Excel загрузите сущность, содержащую столбец (атрибут), который необходимо изменить. Дополнительные сведения см. в разделе [Экспорт данных в Excel из служб Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md).  
  
2.  Щелкните любую ячейку в столбце, который подлежит изменению.  
  
3.  В группе **Построить модель** нажмите кнопку **Свойства атрибута**.  
  
4.  В диалоговом окне **Свойства атрибута** при необходимости обновите параметры.  
  
5.  Нажмите кнопку **ОК**.  
  
## <a name="what-happens-when-you-change-the-attribute-type"></a>Что происходит при изменении типа атрибута  
 Если есть какая-либо зависимость от атрибута, например на атрибут ссылается бизнес-правило MDS или производная иерархия, изменить тип данных этого атрибута нельзя. Появится ошибка с сообщением, что тип атрибута изменить нельзя, поскольку на него ссылается объект.  
  
 Если во время преобразования типов данных для значений атрибутов появляются ошибки, MDS делает следующее:  
  
-   Изменяет тип данных атрибута.  
  
-   Создает копию атрибута с суффиксом _old, которая содержит предыдущие значения. Такой атрибут называется устаревшим.  
  
## <a name="see-also"></a>См. также:  
 [Атрибуты (службы Master Data Services)](../../master-data-services/attributes-master-data-services.md)   
 [Построение модели (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/building-a-model-mds-add-in-for-excel.md)  
  
  
