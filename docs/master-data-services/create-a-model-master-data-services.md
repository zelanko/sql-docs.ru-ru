---
title: Создание модели
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], creating models
- creating models [Master Data Services]
ms.assetid: 9bb3b3b3-bde8-44aa-ad62-eaae21188141
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 730e18fca866891d62b68d321ec13e4be5da59bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728480"
---
# <a name="create-a-model-master-data-services"></a>Создание модели (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]модель создается для того, чтобы содержать объекты.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-model"></a>Создание модели  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Представление модели** в строке меню наведите указатель мыши на **Управление** и щелкните **Модели**.  
  
3.  На странице **Управление моделями** щелкните **Добавить**. С правой стороны появится панель.  
  
4.  В поле **Имя** введите имя модели.  
  
5.  В поле **Описание** введите описание модели (необязательно).  
  
6.  В поле **Продолжительность хранения журнала** выберите один из вариантов для сохранения данных журнала. Значение по умолчанию — **Системный параметр**, что означает, что значение наследуется от системных параметров в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
     Чтобы переопределить системный параметр и не удалить данные журнала транзакций, выберите **НЕТ**. Чтобы сохранить только данные журнала за последний день и удалить данные за все предыдущие дни, выберите **ДА** и в поле **Дни** установите значение 0. Чтобы сохранить данные журнала за определенное число дней, выберите **ДА** и в поле **Дни** укажите необходимое число дней.  
  
7.  По желанию выберите параметр **Создать сущность с именем модели** для создания сущности с тем же именем, что и у модели.  
  
8.  Нажмите **Сохранить модель**.  
  
 Для каждой созданной модели в сетке создается строка с восемью столбцами. Ниже перечислены эти восемь столбцов.  
  
-   **Состояние**: состояние модели. При нажатии кнопки **сохранить модель** отображается изображение ![обновления](../master-data-services/media/mds-model-status-updating.png "Обновляется") , которое указывает на то, что модель обновляется. При возникновении ошибок при создании или изменении модели отображается изображение ![ошибки](../master-data-services/media/mds-model-status-error.png "Ошибка") . В противном случае отображается состояние "ОК" и появляется изображение ![ОК](../master-data-services/media/mds-model-status-ok.png "OK") .  
  
-   **Имя**. имя модели.  
  
-   **Описание**: описание модели.  
  
-   **Срок хранения журнала**(в днях): количество дней, в течение которых журнал сохраняется для модели.  
  
-   **Кем создано**: имя пользователя, создавшего модель.  
  
-   **Дата и время создания**: Дата и время создания модели.  
  
-   **Кем Обновлено**: имя пользователя, который последним обновил модель.  
  
-   **Обновленные Дата и время**: Дата и время последнего обновления модели.  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Создание сущности &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Модели &#40;Master Data Services&#41;](../master-data-services/models-master-data-services.md)   
 [Сущности &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)   
 [Удаление &#40;модели Master Data Services&#41;](../master-data-services/delete-a-model-master-data-services.md)   
 [Изменение &#40;модели Master Data Services&#41;](../master-data-services/edit-model-master-data-services.md)   
 [Master Data Services &#40;транзакций&#41;](../master-data-services/transactions-master-data-services.md)  
  
  
