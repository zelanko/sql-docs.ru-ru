---
title: Превращение группы атрибутов в видимую для пользователей
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b2f6cc27-dbc9-4f3f-961e-e81e76375248
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 26ad0e3d481b5d09a3105645af5705a3bd99cdbf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "73729067"
---
# <a name="make-an-attribute-group-visible-to-users-master-data-services"></a>Превращение группы атрибутов в видимую для пользователей (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]сделайте группу атрибутов видимой для пользователей или групп, если необходимо, чтобы у пользователей присутствовали вкладки над сеткой в функциональной области **Обозреватель** .  
  
 При создании группы атрибутов она автоматически скрыта от всех пользователей, кроме того, кто ее создал.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Должна существовать хотя бы одна группа атрибутов. Дополнительные сведения см. в статье [Создание группы атрибутов (службы Master Data Services)](../master-data-services/create-an-attribute-group-master-data-services.md).  
  
### <a name="to-make-an-attribute-group-visible-to-users"></a>Превращение группы атрибутов в видимую для пользователей  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Управление моделью** выберите модель в сетке и щелкните **сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) выберите в сетке строку сущности, для которой необходимо изменить группу атрибутов.  
  
4.  Щелкните **Группы атрибутов**.  
  
5.  На странице **Управление группами атрибутов** выберите тип элемента из раскрывающегося списка **Типы элементов** , чтобы развернуть узел **Конечный**, **Консолидированный** или **Коллекция**в зависимости от типа группы, которую нужно сделать видимой.  
  
6.  Выберите в сетке группу атрибутов, которую необходимо изменить, а затем нажмите **Изменить**.  
  
7.  Выберите пользователя или группу в поле **Доступные** и щелкните стрелку **Добавить** . Чтобы добавить все, щелкните стрелку **Добавить все** .  
  
8.  Выберите команду **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Группы атрибутов &#40;Master Data Services&#41;](../master-data-services/attribute-groups-master-data-services.md)   
 [Создание группы атрибутов (службы Master Data Services)](../master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
