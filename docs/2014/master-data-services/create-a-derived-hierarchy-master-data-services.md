---
title: Создание производной иерархии (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, creating
- creating derived hierarchies [Master Data Services]
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 90ecf9d2f9c677351a4c199414be25d753fe5346
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65479962"
---
# <a name="create-a-derived-hierarchy-master-data-services"></a>Создание производной иерархии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]производные иерархии создаются, если необходима многоуровневая иерархия, гарантирующая, что элементы располагаются на правильном уровне. Производные иерархии опираются на имеющиеся в модели связи атрибутов на основе домена.  
  
> [!NOTE]  
>  Если значение атрибута на основе домена отсутствует для какого-либо элемента, он не включается в производную иерархию. Сведения о том, как сделать значение атрибута на основе домена обязательным для всех элементов, см. в разделе [Запрос значений атрибута (службы Master Data Services)](require-attribute-values-master-data-services.md).  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../../2014/master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-derived-hierarchy"></a>Создание производной иерархии  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На **представление модели** страницы, на панели меню наведите указатель мыши на **управление** и нажмите кнопку **производные иерархии**.  
  
3.  На странице **Обслуживание производной иерархии** выберите модель из списка **Модель** .  
  
4.  Нажмите кнопку **Добавить производную иерархию**.  
  
5.  В поле **Имя производной иерархии** на странице **Добавление производной иерархии** введите имя иерархии.  
  
    > [!TIP]  
    >  Используйте имя, описывающее уровни иерархии, например **Продукт: от подкатегории к категории**.  
  
6.  Нажмите кнопку **Сохранить производную иерархию**.  
  
7.  На **изменить производную иерархию** странице **доступные сущности и иерархии** панели щелкните сущность или иерархию и перетащите его на значок **текущие уровни** области.  
  
8.  Перетаскивайте сущности или иерархии, пока не завершите создание иерархии.  
  
9. Нажмите кнопку **Назад**.  
  
## <a name="see-also"></a>См. также  
 [Производные иерархии (службы Master Data Services)](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [Производные иерархии с явными ограничениями (службы Master Data Services)](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Атрибуты на основе домена (службы Master Data Services)](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
  
