---
title: Изменение модели
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], changing name
ms.assetid: 399eed32-7c61-4239-9c06-996a65219518
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 89fa4dea57c4936a2d6a51e08f48668215ba53a2
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73728206"
---
# <a name="edit-model-master-data-services"></a>Изменение модели (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно изменить имя и описание модели и указать, сколько дней необходимо хранить журналы транзакций.  
  
 Дополнительные сведения см. в разделе [Транзакции (службы Master Data Services)](../master-data-services/transactions-master-data-services.md).  
  
## <a name="prerequisites"></a>необходимые компоненты  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-change-a-model"></a>Изменение модели  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Представление модели** в строке меню наведите указатель мыши на **Управление** и щелкните **Модели**.  
  
3.  На странице **Управление моделями** в сетке выберите строку модели, имя или описание которой необходимо изменить.  
  
4.  Нажмите кнопку **Изменить**.  
  
5.  Введите новое имя модели в поле **Имя** .  
  
6.  В поле **Описание** введите новое описание модели.  
  
7.  В поле **Продолжительность хранения журнала** выберите один из вариантов для сохранения данных журнала. Значение по умолчанию — **Системный параметр**, что означает, что значение наследуется от системных параметров в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
     Чтобы переопределить системный параметр и не удалить данные журнала транзакций, выберите **НЕТ**. Чтобы сохранить только данные журнала за последний день и удалить данные за все предыдущие дни, выберите **ДА** и в поле **Дни** установите значение 0. Чтобы сохранить данные журнала за определенное число дней, выберите **ДА** и в поле **Дни** укажите необходимое число дней.  
  
8.  Нажмите **Сохранить модель**.  
  
 В столбце **Состояние** в сетке отображается состояние операции с моделью. При нажатии кнопки **сохранить модель** отображается изображение ![обновления](../master-data-services/media/mds-model-status-updating.png "Обновить") , которое указывает на то, что модель обновляется. При возникновении ошибок при создании или изменении модели отображается изображение ![ошибки](../master-data-services/media/mds-model-status-error.png "Error") . В противном случае отображается состояние "ОК" и появляется изображение ![ОК](../master-data-services/media/mds-model-status-ok.png "OK") .  
  
## <a name="see-also"></a>См. также статью  
 [Создание модели (службы Master Data Services)](../master-data-services/create-a-model-master-data-services.md)   
 [Удаление модели (службы Master Data Services)](../master-data-services/delete-a-model-master-data-services.md)   
 [Модели (службы Master Data Services)](../master-data-services/models-master-data-services.md)  
  
  
