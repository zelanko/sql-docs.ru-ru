---
title: "Нерекомендуемые функции служб Master Data Services | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
caps.latest.revision: "18"
author: smartysanthosh
ms.author: nagavo
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 094c028aef66d3573d14830b351b58d48c74850d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="deprecated-master-data-services-features"></a>Устаревшие функции Master Data Services
  В этом разделе описаны устаревшие функции компонента [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , которые по-прежнему доступны в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Эти функции будут удалены в следующем выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не следует использовать устаревшие функции в новых приложениях.  
  
## <a name="explicit-hierarchies-collections-and-related-components"></a>Явные иерархии, коллекции и связанные компоненты  
 Явные иерархии, коллекции и связанные компоненты являются устаревшими. Элементы, которые раньше моделировались как типы консолидированных элементов (родительские элементы явной иерархии) и типы элементов коллекции, будут моделироваться в производных иерархиях как конечные элементы. Ниже приведены новые возможности, которые поддерживают использование производных иерархий вместо явных иерархий.  
  
-   Рекурсивные производные иерархии теперь можно использовать, чтобы назначить элементу разрешения безопасности.  
  
     Явная иерархия — это аналог рекурсивной производной иерархии с одним нерекурсивным уровнем ниже рекурсивного уровня. Рекурсивная производная иерархия может быть сложной и включать уровни ниже и/или выше рекурсивного уровня.  
  
-   Теперь в обозревателе на странице производной иерархии отображаются неназначенные (неиспользуемые) элементы для каждого уровня иерархии. Неиспользуемые узлы сгруппированы по уровню иерархии. Элементы можно перемещать между неиспользуемыми и корневыми узлами путем перетаскивания или вырезания и вставки.  
  
     В окне системного администрирования неиспользуемые узлы отображаются на панели **Просмотр** . В разделе "Безопасность" неиспользуемые узлы отображаются на панели **Разрешения элементов иерархии** . Для любого элемента, будь то **корневой** или **неиспользуемый** узел, можно назначить разрешение. Кроме того, можно назначить разрешения для элементов **корневого**, **неиспользуемого**узла и **неиспользуемых** псевдоэлементов.  
  
-   Хранимая процедура mdm.udpConvertCollectionAndConsolidatedMembersToLeaf преобразует явные иерархии в рекурсивные производные иерархии, а консолидированные элементы и элементы коллекции — в конечные элементы.  
  
     Явные иерархии и типы консолидированных элементов и элементов коллекции по-прежнему поддерживаются, поэтому запускать хранимую процедуру необязательно. Но при использовании этих элементов рекомендуется запустить хранимую процедуру, так как они устарели.  
  
 Дополнительные сведения о явных иерархиях, коллекциях и консолидированных элементах см. в следующих разделах:  
  
-   [Явные иерархии (службы Master Data Services)](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [Коллекции (службы Master Data Services)](../master-data-services/collections-master-data-services.md)  
  
-   [Элементы (службы Master Data Services)](../master-data-services/members-master-data-services.md)  
  
## <a name="attribute-entity-transaction-log-type"></a>Типа журнала транзакций сущности "Атрибут"  
Тип журнала транзакций сущности "Атрибут" устарел; используйте тип "Элемент". Сведения о типах журнала транзакций сущности см. в следующем разделе:
* [Изменение типа журнала транзакций сущности (Master Data Services)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)
* [Журнал изменений элемента](../master-data-services/member-revision-history-master-data-services.md)
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись блога [Deprecated: Explicit Hierarchies and Collections](http://go.microsoft.com/fwlink/p/?LinkId=615373)(Устарелое. Явные иерархии и коллекции) на портале msdn.com.  
  
## <a name="see-also"></a>См. также:  
 [Неподдерживаемые функции служб Master Data Services](../master-data-services/discontinued-master-data-services-features.md)  
  
  
