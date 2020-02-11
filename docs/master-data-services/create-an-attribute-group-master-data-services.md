---
title: Создание группы атрибутов
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 534e8bed6596c9b15e05ec179ece3d37a64b15ac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728439"
---
# <a name="create-an-attribute-group-master-data-services"></a>Создание группы атрибутов (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]группы атрибутов создаются, когда нужно отобразить атрибуты на отдельных вкладках сетки **обозревателя** .  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Требуется хотя бы один атрибут. Дополнительные сведения см. в статье [Создание текстового атрибута (службы Master Data Services)](../master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-create-an-attribute-group"></a>Создание группы атрибутов  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) выберите в сетке строку сущности, для которой необходимо создать группу атрибутов.  
  
4.  Щелкните **Группы атрибутов**.  
  
5.  На странице "Управление группами атрибутов" выполните одно из следующих действий, а затем нажмите кнопку **Добавить**.  
  
     Если группа атрибутов предназначена для конечных элементов, выберите пункт **Конечный** из раскрывающегося списка **Типы элементов** в верхней части страницы.  
  
     Если группа атрибутов предназначена для консолидированных элементов, из раскрывающегося списка **Типы элементов** выберите пункт **Консолидированный** .  
  
     Если группа атрибутов предназначена для коллекций, из раскрывающегося списка **Типы элементов** выберите **Коллекция** .  
  
6.  Выберите **Конечные группы**, **Консолидированные группы**или **Группы коллекций** , чтобы создать группу атрибутов для конечных элементов, объединенных элементов или коллекций соответственно.  
  
7.  Введите имя группы атрибутов в поле **Имя** . Это имя отображается на вкладке в **обозревателе**.  
  
8.  Чтобы добавить атрибут, щелкните атрибут в поле **Доступные атрибуты** , а затем щелкните стрелку **Добавить** . Чтобы добавить все атрибуты, щелкните стрелку **Добавить все** .  
  
9. Можно изменить порядок атрибутов слева направо, щелкая стрелки **Вверх** и **Вниз** .  
  
10. Выберите пользователей в поле **Доступные пользователи** , затем щелкните стрелку **Добавить** . Чтобы добавить всех пользователей, щелкните стрелку **Добавить все** .  
  
11. Выберите группы в поле **Доступные группы** , затем щелкните стрелку **Добавить** . Чтобы добавить все группы, щелкните стрелку **Добавить все** .  
  
12. Выберите команду **Сохранить**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Сделать группу атрибутов видимой для пользователей &#40;Master Data Services&#41;](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Группы атрибутов &#40;Master Data Services&#41;](../master-data-services/attribute-groups-master-data-services.md)   
 [Master Data Services &#40;атрибутов&#41;](../master-data-services/attributes-master-data-services.md)   
 [Изменение имени группы атрибутов &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-group-name-master-data-services.md)   
 [Удаление группы атрибутов &#40;Master Data Services&#41;](../master-data-services/delete-an-attribute-group-master-data-services.md)   
 [Конечные разрешения &#40;Master Data Services&#41;](../master-data-services/leaf-permissions-master-data-services.md)   
   
  
  
