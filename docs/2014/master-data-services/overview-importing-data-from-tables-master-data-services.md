---
title: Импорт данных (Master Data Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], about staging process
- importing data [Master Data Services]
- staging process [Master Data Services]
ms.assetid: 181d1e22-379c-45d1-b03c-e1e22ff14164
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 3d1ad35a40e4218bfef44daeec01ee03fc0c7c78
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175993"
---
# <a name="data-import-master-data-services"></a>Импорт данных (службы Master Data Services)
  После создания модели для данных в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно добавлять данные и вносить в них изменения в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .   Используются промежуточные таблицы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , хранимые процедуры и диспетчер основных данных.

 Можно [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]также использовать для добавления данных в репозиторий MDS ([!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] база данных). Дополнительные сведения см. в разделе [Publishing Data &#40;надстройка MDS для Excel&#41;](microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md).

 При добавлении или обновлении данных можно выполнять следующие действия.

-   Загружать и обновлять элементы и обновлять значения атрибутов

-   Деактивировать или удалять элементы

-   Перемещать элементы явной иерархии

 Добавление и обновление данных включает следующие основные задачи.

1.  Загрузка данных в промежуточные таблицы в базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .

2.  Загрузка данных из промежуточных таблиц в соответствующие таблицы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .

     Для загрузки данных используются промежуточные хранимые процедуры или [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .

> [!NOTE]
>  В [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]прекращена поддержка промежуточных процедур [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] .

## <a name="deactivating-and-deleting-members"></a>Деактивация и удаление элементов
 Отключение означает, что элемент может быть активирован повторно. Если элемент включен повторно, то его атрибуты и членство в иерархиях и коллекциях восстанавливаются. Все предыдущие транзакции являются неизменными. Транзакции отключения отслеживаются администраторами в функциональной области **Управление версиями** диспетчера основных данных.

 Удаление означает окончательное удаление элемента из системы. Все транзакции для элемента, все связи и все атрибуты будут окончательно удалены.

> [!NOTE]
>  Использовать промежуточное хранение данных для повторной активации элементов невозможно. Повторную активацию необходимо выполнять вручную в диспетчере основных данных. Дополнительные сведения см. в разделе [Повторная активация элемента или коллекции (службы Master Data Services)](reactivate-a-member-or-collection-master-data-services.md).
> 
>  Промежуточное хранение нельзя использовать для удаления или деактивации коллекций. Дополнительные сведения о деактивации коллекций вручную см. в разделе [Удаление элемента или коллекции (службы Master Data Services)](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md).

## <a name="moving-explicit-hierarchy-members"></a>Перемещение элементов явной иерархии
 При массовом изменении местоположения элементов в явных иерархиях можно назначать элементы следующим образом.

-   Объединенный элемент в качестве родителя другого объединенного элемента.

-   Объединенный элемент в качестве родителя конечного элемента.

-   Конечный элемент в качестве одноуровневого элемента для другого конечного или объединенного элемента.

-   Объединенный элемент в качестве одноуровневого элемента для другого конечного или объединенного элемента.

## <a name="staging-tables-and-stored-procedures"></a>Промежуточные таблицы и хранимые процедуры
 База данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] включает следующие типы промежуточных таблиц, которые можно заполнять данными.

-   [&#40;Master Data Services промежуточной таблицы элементов&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md)

-   [Промежуточная таблица консолидированного элемента &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)

-   [Промежуточная таблица связей &#40;Master Data Services&#41;](../../2014/master-data-services/relationship-staging-table-master-data-services.md)

 Для каждой сущности в модели есть промежуточная таблица. Имя таблицы обозначает соответствующую сущность и ее тип, например конечный элемент. На этом изображении показаны промежуточные таблицы для сущностей валюты, клиента и продукта.

 ![Промежуточные таблицы в базе данных MDS](../../2014/master-data-services/media/mds-stagingtables.png "Промежуточные таблицы в базе данных MDS")

 Имя таблицы указывается при создании сущности и не может быть изменено. Если имя промежуточной таблицы содержит _1 (или другое число), то на момент создания сущности уже существовала другая таблица с тем же именем.

 
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] включает следующие типы промежуточных хранимых процедур.

-   stg.udp_\<имя>_Leaf

-   stg.udp_\<имя>_Consolidated

-   stg.udp_\<имя>_Relationship

 Для каждой сущности в модели есть три хранимые процедуры, которые соответствуют конечному элементу, объединенному элементу и промежуточным таблицам связей.  На следующем изображении показаны промежуточные хранимые процедуры для сущностей валюты, клиента и продукта.

 ![Промежуточные хранимые процедуры в базе данных MDS](../../2014/master-data-services/media/mds-stagingstoredprocedures.png "Промежуточные хранимые процедуры в базе данных MDS")

 Дополнительные сведения о хранимых процедурах см. в разделе [Промежуточная хранимая процедура (службы Master Data Services)](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).

## <a name="logging-transactions"></a>Регистрация транзакций
 Все транзакции, происходящие при импорте или обновлении данных или связей, можно регистрировать. Параметр хранимой процедуры позволяет такую регистрацию. При запуске промежуточного процесса с помощью [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]регистрация не осуществляется.

 В [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]параметр **Регистрация промежуточных транзакций** не применяется к этому методу промежуточной обработки данных.

## <a name="related-content"></a>См. также

-   [Master Data Services &#40;проверки&#41;](../../2014/master-data-services/validation-master-data-services.md)

-   [Бизнес-правила &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)


