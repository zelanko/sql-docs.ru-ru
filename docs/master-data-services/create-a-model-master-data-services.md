---
title: Создание модели (службы Master Data Services) | Документы Майкрософт
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
manager: craigg
ms.openlocfilehash: 5c55db7072020f715882912b46cac0e9219cbbf9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65477055"
---
# <a name="create-a-model-master-data-services"></a>Создание модели (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]модель создается для того, чтобы содержать объекты.  
  
## <a name="prerequisites"></a>предварительные требования  
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
  
-   **Состояние**: состояние модели. При нажатии кнопки **Сохранить модель** появляется изображение ![Обновляется](../master-data-services/media/mds-model-status-updating.png "Обновляется"), которое указывает, что модель обновляется. При наличии ошибок во время создания или изменения модели появляется изображение ![Ошибка](../master-data-services/media/mds-model-status-error.png "Ошибка"). В противном случае отображается состояние "ОК" и появляется изображение ![ОК](../master-data-services/media/mds-model-status-ok.png "ОК") .  
  
-   **Имя**: Имя модели.  
  
-   **Описание**: Описание модели.  
  
-   **Хранение журнала в днях**: количество дней, в течение которого хранится журнал для модели.  
  
-   **Кем создано**: имя пользователя, создавшего модель.  
  
-   **Дата и время создания**: дата и время, когда была создана модель.  
  
-   **Кем обновлено**: имя последнего пользователя, обновившего модель.  
  
-   **Дата и время обновления**: дата и время последнего обновления модели.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Создание сущности (службы Master Data Services)](../master-data-services/create-an-entity-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Модели (службы Master Data Services)](../master-data-services/models-master-data-services.md)   
 [Сущности (службы Master Data Services)](../master-data-services/entities-master-data-services.md)   
 [Удаление модели (службы Master Data Services)](../master-data-services/delete-a-model-master-data-services.md)   
 [Изменение модели (Master Data Services)](../master-data-services/edit-model-master-data-services.md)   
 [Транзакции (службы Master Data Services)](../master-data-services/transactions-master-data-services.md)  
  
  
