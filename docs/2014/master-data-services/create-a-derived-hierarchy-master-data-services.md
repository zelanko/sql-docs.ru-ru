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
ms.openlocfilehash: 7c831ab360f2cbe4b32834ae2a280b961d2bac1e
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971874"
---
# <a name="create-a-derived-hierarchy-master-data-services"></a>Создание производной иерархии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]производные иерархии создаются, если необходима многоуровневая иерархия, гарантирующая, что элементы располагаются на правильном уровне. Производные иерархии опираются на имеющиеся в модели связи атрибутов на основе домена.  
  
> [!NOTE]  
>  Если значение атрибута на основе домена отсутствует для какого-либо элемента, он не включается в производную иерархию. Сведения о том, как сделать значение атрибута на основе домена обязательным для всех элементов, см. в разделе [Запрос значений атрибута (службы Master Data Services)](require-attribute-values-master-data-services.md).  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-derived-hierarchy"></a>Создание производной иерархии  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **представление модели** в строке меню наведите указатель мыши на пункт **Управление** и щелкните **производные иерархии**.  
  
3.  На странице **Обслуживание производной иерархии** выберите модель из списка **Модель** .  
  
4.  Нажмите кнопку **Добавить производную иерархию**.  
  
5.  В поле **Имя производной иерархии** на странице **Добавление производной иерархии** введите имя иерархии.  
  
    > [!TIP]  
    >   Используйте имя, описывающее уровни иерархии, например **Продукт: от подкатегории к категории**.  
  
6.  Нажмите кнопку **Сохранить производную иерархию**.  
  
7.  На странице **изменение производной иерархии** на панели **Доступные сущности и иерархии** щелкните сущность или иерархию и перетащите ее на панель **текущие уровни** .  
  
8.  Перетаскивайте сущности или иерархии, пока не завершите создание иерархии.  
  
9. Нажмите кнопку **Назад**.  
  
## <a name="see-also"></a>См. также:  
 [Производные иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [Производные иерархии с явно заданными ограничениями &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Атрибуты на основе домена (службы Master Data Services)](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
  
