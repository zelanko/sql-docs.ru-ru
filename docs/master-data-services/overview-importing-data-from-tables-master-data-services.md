---
title: 'Обзор: импорт данных из таблиц (службы Master Data Services) | Документы Майкрософт'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- staging process [Master Data Services], about staging process
- importing data [Master Data Services]
- staging process [Master Data Services]
ms.assetid: 181d1e22-379c-45d1-b03c-e1e22ff14164
caps.latest.revision: 21
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6ba2e669edc4c5a09ba0003afa21a83934598b0a
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="overview-importing-data-from-tables-master-data-services"></a>Обзор: импорт данных из таблиц (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  После создания модели для данных в службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно добавлять данные и вносить в них изменения.   Используются промежуточные таблицы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , хранимые процедуры и диспетчер основных данных.  
  
 Дополнительные сведения о добавлении и изменении данных см. в разделе [Импорт данных из таблиц (службы Master Data Services)](../master-data-services/import-data-from-tables-master-data-services.md).  
  
> [!NOTE]  
>  Также можно использовать [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]для добавления данных в репозиторий MDS (база данных[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ) из Excel. Дополнительные сведения см. в разделе [Обзор импорта данных из Excel (надстройка MDS для Excel)](../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md).  
  
 При добавлении или изменении данных можно выполнять следующие действия.  
  
-   Загружать и обновлять элементы и обновлять значения атрибутов  
  
-   Деактивировать или удалять элементы  
  
-   Перемещать элементы явной иерархии  
  
 Добавление и обновление данных включает следующие основные задачи.  
  
1.  Загрузка данных в промежуточные таблицы в базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Загрузка данных из промежуточных таблиц в соответствующие таблицы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
     Для загрузки данных используются промежуточные хранимые процедуры или [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
> [!NOTE]  
>  В [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]прекращена поддержка промежуточных процедур [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] .  
  
## <a name="deactivating-and-deleting-members-mds"></a>Деактивация и удаление элементов (MDS)  
 Отключение означает, что элемент может быть активирован повторно. Если элемент включен повторно, то его атрибуты и членство в иерархиях и коллекциях восстанавливаются. Все предыдущие транзакции являются неизменными. Транзакции отключения отслеживаются администраторами в функциональной области **Управление версиями** диспетчера основных данных.  
  
 Удаление означает окончательное удаление элемента из системы. Все транзакции для элемента, все связи и все атрибуты будут окончательно удалены.  
  
> [!NOTE]  
>  Использовать промежуточное хранение данных для повторной активации элементов невозможно. Повторную активацию необходимо выполнять вручную в диспетчере основных данных. Дополнительные сведения см. в разделе [Повторная активация элемента или коллекции (службы Master Data Services)](../master-data-services/reactivate-a-member-or-collection-master-data-services.md).  
>   
>  Промежуточное хранение нельзя использовать для удаления или деактивации коллекций. Дополнительные сведения о деактивации коллекций вручную см. в разделе [Удаление элемента или коллекции (службы Master Data Services)](../master-data-services/delete-a-member-or-collection-master-data-services.md).  
  
## <a name="moving-explicit-hierarchy-members-mds"></a>Перемещение элементов явной иерархии (MDS)  
 При массовом изменении местоположения элементов в явных иерархиях можно назначать элементы следующим образом.  
  
-   Объединенный элемент в качестве родителя другого объединенного элемента.  
  
-   Объединенный элемент в качестве родителя конечного элемента.  
  
-   Конечный элемент в качестве одноуровневого элемента для другого конечного или объединенного элемента.  
  
-   Объединенный элемент в качестве одноуровневого элемента для другого конечного или объединенного элемента.  
  
## <a name="staging-tables-and-stored-procedures-mds"></a>Промежуточные таблицы и хранимые процедуры (MDS)  
 База данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] включает следующие типы промежуточных таблиц, которые можно заполнять данными.  
  
-   [Конечный элемент таблицы элементов (службы Master Data Services)](../master-data-services/leaf-member-staging-table-master-data-services.md)  
  
-   [Промежуточная таблица консолидированных элементов (службы Master Data Services)](../master-data-services/consolidated-member-staging-table-master-data-services.md)  
  
-   [Промежуточная таблица связей (службы Master Data Services)](../master-data-services/relationship-staging-table-master-data-services.md)  
  
 Для каждой сущности в модели есть промежуточная таблица. Имя таблицы обозначает соответствующую сущность и ее тип, например конечный элемент. На этом изображении показаны промежуточные таблицы для сущностей валюты, клиента и продукта.  
  
 ![Промежуточные таблицы в базе данных MDS](../master-data-services/media/mds-staging-tables.png "Промежуточные таблицы в базе данных MDS")  
  
 Имя таблицы указывается при создании сущности и не может быть изменено. Если имя промежуточной таблицы содержит _1 (или другое число), то на момент создания сущности уже существовала другая таблица с тем же именем.  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] включает следующие типы промежуточных хранимых процедур.  
  
-   stg.udp_\<имя>_Leaf  
  
-   stg.udp_\<имя>_Consolidated  
  
-   stg.udp_\<имя>_Relationship  
  
 Для каждой сущности в модели есть три хранимые процедуры, которые соответствуют конечному элементу, объединенному элементу и промежуточным таблицам связей.  На следующем изображении показаны промежуточные хранимые процедуры для сущностей валюты, клиента и продукта.  
  
 ![Промежуточные хранимые процедуры в базе данных MDS](../master-data-services/media/mds-staging-storedprocedures.png "Промежуточные хранимые процедуры в базе данных MDS")  
  
 Дополнительные сведения о хранимых процедурах см. в разделе [Промежуточная хранимая процедура (службы Master Data Services)](../master-data-services/staging-stored-procedure-master-data-services.md).  
  
## <a name="logging-transactions-mds"></a>Регистрация транзакций (MDS)  
 Все транзакции, происходящие при импорте или обновлении данных или связей, можно регистрировать. Параметр хранимой процедуры позволяет такую регистрацию. При запуске промежуточного процесса с помощью [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]регистрация не осуществляется.  
  
 В [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]параметр **Регистрация промежуточных транзакций** не применяется к этому методу промежуточной обработки данных.  
  
## <a name="related-content"></a>См. также  
  
-   [Проверка (службы Master Data Services)](../master-data-services/validation-master-data-services.md)  
  
-   [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
  
