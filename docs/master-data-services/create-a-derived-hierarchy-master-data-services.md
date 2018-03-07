---
title: "Создание производной иерархии (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- derived hierarchies, creating
- creating derived hierarchies [Master Data Services]
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d402500e440711717da7d7f58bbb1e3fb5ac413
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="create-a-derived-hierarchy-master-data-services"></a>Создание производной иерархии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]производные иерархии создаются, если необходима многоуровневая иерархия, гарантирующая, что элементы располагаются на правильном уровне. Производные иерархии опираются на имеющиеся в модели связи атрибутов на основе домена.  
  
> [!NOTE]  
>  Если значение атрибута на основе домена отсутствует для какого-либо элемента, он не включается в производную иерархию. Сведения о том, как сделать значение атрибута на основе домена обязательным для всех элементов, см. в разделе [Запрос значений атрибута (службы Master Data Services)](../master-data-services/require-attribute-values-master-data-services.md).  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-derived-hierarchy"></a>Создание производной иерархии  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню наведите указатель на пункт **Управление** и выберите команду **Производные иерархии**.  
  
3.  На странице **Обслуживание производной иерархии** выберите модель из списка **Модель** .  
  
4.  Нажмите кнопку **Добавить**.  
  
5.  В поле **Имя производной иерархии** на странице **Добавление производной иерархии** введите имя иерархии.  
  
    > [!TIP]  
    >  Используйте имя, описывающее уровни иерархии, например **Продукт: от подкатегории к категории**.  
  
6.  Нажмите кнопку **Сохранить производную иерархию**.  
  
7.  На панели **Доступные сущности и иерархии** страницы **Изменить производную иерархию** щелкните сущность или иерархию и перетащите ее в область **Drop Parent Here** (Перетащите сюда родительский элемент) на панели **Текущие уровни** .  
  
8.  Перетаскивайте сущности или иерархии, пока не завершите создание иерархии.  
  
9. Нажмите кнопку **Назад**.  
  
## <a name="see-also"></a>См. также:  
 [Производные иерархии (службы Master Data Services)](../master-data-services/derived-hierarchies-master-data-services.md)   
 [Производные иерархии с явными ограничениями (службы Master Data Services)](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Атрибуты на основе домена (службы Master Data Services)](../master-data-services/domain-based-attributes-master-data-services.md)  
  
  
