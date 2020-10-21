---
description: Изменение типа атрибута (надстройка MDS для Excel)
title: Изменение типа атрибута
ms.custom: microsoft-excel-add-in
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1fd0e7f0acbe6792a5d303d50ef66014ebc5c1cf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "92257585"
---
# <a name="change-the-attribute-type-mds-add-in-for-excel"></a>Изменение типа атрибута (надстройка MDS для Excel)

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]администраторы могут изменить тип атрибута, если тип данных или количество допустимых символов являются неверными.  
  
 Если необходимо изменить тип атрибута для создания ограниченного списка (атрибут на основе домена), см. раздел [Создание атрибута на основе домена (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/create-a-domain-based-attribute-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  Нельзя изменить тип или длину столбцов **Имя** или **Код**.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональным областям **Администрирование системы** и **Обозреватель** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../../master-data-services/administrators-master-data-services.md).  
  
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
 [Master Data Services &#40;атрибутов&#41;](../../master-data-services/attributes-master-data-services.md)   
 [Построение модели (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/building-a-model-mds-add-in-for-excel.md)  
  
  
