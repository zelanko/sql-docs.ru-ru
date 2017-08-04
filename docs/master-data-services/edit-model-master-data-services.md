---
title: "Изменение модели (Master Data Services) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models [Master Data Services], changing name
ms.assetid: 399eed32-7c61-4239-9c06-996a65219518
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 08291f09ed7bc172fe22534e82b79ecc47ce55e1
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="edit-model-master-data-services"></a>Изменение модели (Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно изменить имя и описание модели и указать, сколько дней необходимо хранить журналы транзакций.  
  
 Дополнительные сведения см. в разделе [Транзакции (службы Master Data Services)](../master-data-services/transactions-master-data-services.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
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
  
 В столбце **Состояние** в сетке отображается состояние операции с моделью. При нажатии кнопки **сохранить модель** кнопки, ![обновление](../master-data-services/media/mds-model-status-updating.png "обновление") изображение, указывает, что модель обновляется. При наличии ошибок при создании или изменении модели, ![ошибка](../master-data-services/media/mds-model-status-error.png "ошибка") изображение. В противном случае отображается состояние "ОК" и появляется изображение ![ОК](../master-data-services/media/mds-model-status-ok.png "ОК") .  
  
## <a name="see-also"></a>См. также:  
 [Создать модель &#40; Службы Master Data Services &#41;](../master-data-services/create-a-model-master-data-services.md)   
 [Удалить модель &#40; Службы Master Data Services &#41;](../master-data-services/delete-a-model-master-data-services.md)   
 [Модели (службы Master Data Services)](../master-data-services/models-master-data-services.md)  
  
  
