---
title: Удаление группы атрибутов
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting attribute groups [Master Data Services]
- attribute groups [Master Data Services], deleting
ms.assetid: f915e89b-629d-4725-aea6-a7f051978244
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 78ba8b955fe0702a5b1737c1de24426d586f9ffa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "73729364"
---
# <a name="delete-an-attribute-group-master-data-services"></a>Удаление группы атрибутов (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно удалить группу атрибутов, если больше не нужна вкладка для отображения в функциональной области **Обозреватель** в среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   **Примечание.** Если группы атрибутов существуют, то атрибуты, не принадлежащие ни к одной группе, не отображаются в окне **Обозреватель**. Если групп атрибутов не существует, то отображаются все атрибуты.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-an-attribute-group"></a>Удаление группы атрибутов  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Управление моделью** выберите модель в сетке и щелкните **сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) выберите в сетке строку сущности, для которой необходимо изменить группу атрибутов.  
  
4.  Щелкните **Группы атрибутов**.  
  
5.  На странице **Управление группами атрибутов** выберите тип элемента из раскрывающегося списка **Типы элементов** , чтобы развернуть узел **Конечный**, **Консолидированный**или **Коллекция**в зависимости от типа удаляемой группы.  
  
6.  Щелкните группу атрибутов, которую необходимо удалить.  
  
7.  Щелкните **Удалить**.  
  
8.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Группы атрибутов &#40;Master Data Services&#41;](../master-data-services/attribute-groups-master-data-services.md)   
 [Создание группы атрибутов (службы Master Data Services)](../master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
