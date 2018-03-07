---
title: "Журнал изменений элемента (службы Master Data Services) | Документы Майкрософт"
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
ms.assetid: 113069c5-12e6-48ec-b443-b42e14f77308
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26509a91e02f0afdcdae721d2268ae6c88d792cb
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="member-revision-history-master-data-services"></a>Журнал изменений элемента (Master Data Services)
  Если тип журнала транзакций сущностей является элементом, то при каждом изменении элемента записывается журнал изменений элемента.  
  
 Сведения о типах журналов транзакций см. в разделе [Изменение типа журнала транзакций сущности (Master Data Services)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
 Журналы изменений элемента записываются, когда происходят следующие изменения.  
  
-   Элементы создаются, удаляются, повторно активируются или очищаются.  
  
-   Изменяются значения атрибутов.  
  
-   Элементы перемещаются в иерархии или коллекции.  
  
## <a name="view-and-manage-revision-history-by-entity"></a>Просмотр и управление журналом изменений по сущности  
 В функциональной области обозревателя можно просмотреть изменения всех элементов в сущности. При наличии разрешений на обновление можно выполнить откат элемента до предыдущей версии.  
  
 **Просмотр и управление журналом изменений**  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]выберите модель и версию, а затем нажмите кнопку **Обозреватель**.  
  
2.  Выберите сущность в меню **Сущности** .  
  
3.  Чтобы просмотреть историю изменений сущности, щелкните **Просмотр журнала** .  
  
4.  Чтобы отфильтровать данные, щелкните **Фильтр** .  
  
5.  Щелкните заголовок столбца, чтобы сортировать данные.  
  
6.  При наличии разрешений на обновление щелкните **Отменить изменения элемента** , чтобы выполнить откат до выбранной версии.  
  
## <a name="view-and-manage-revision-history-by-member"></a>Просмотр и управление журналом изменений по элементу  
 При наличии разрешений на чтение для определенного элемента в функциональной области обозревателя можно просмотреть его изменения. При наличии разрешений на обновление можно выполнить откат элемента до предыдущей версии или добавить заметки к изменению.  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]выберите модель и версию, а затем нажмите кнопку **Обозреватель**.  
  
2.  Выберите сущность в меню **Сущности** .  
  
3.  Выберите элемент.  
  
4.  В правой области щелкните **Просмотр журнала** .  
  
## <a name="log-retention-setting"></a>Настройка хранения журнала  
 Вы можете настроить длительность хранения данных журнала. Для этого необходимо определить свойство **Срок хранения журнала в днях** в системных параметрах базы данных [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , а также задать значение **Продолжительность хранения журнала** при создании или изменении модели.  
  
## <a name="related-task"></a>Связанная задача  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Откат журнала изменений элемента|[Откат журнала изменений элемента (Master Data Services)](../master-data-services/rollback-member-revision-history-master-data-services.md)|  
  
## <a name="see-also"></a>См. также:  
 [Создание модели (службы Master Data Services)](../master-data-services/create-a-model-master-data-services.md)   
 [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md)  
  
  
