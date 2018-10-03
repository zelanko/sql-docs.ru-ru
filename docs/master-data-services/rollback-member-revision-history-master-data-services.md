---
title: Откат журнала изменений элемента (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: d39d3474-20e7-429f-9c8d-fcc4eb0854fc
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 4acdf97acba4951624df2b7eaa37e4769d608b3f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838342"
---
# <a name="rollback-member-revision-history-master-data-services"></a>Откат журнала изменений элемента (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Запись в журнал изменений элемента осуществляется каждый раз при изменении элемента. Существует возможность откатить журнал изменений элемента к предыдущей версии.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Необходимо иметь разрешение на обновление хотя бы одного из атрибутов выбранного элемента. При откате журнала изменений все значения атрибутов, которые могут быть обновлены, откатываются к значениям предыдущей версии.  
  
-   Журнал изменений доступен, только если типом журнала транзакций сущности является элемент.  
  
 **Откат журнала изменений элемента**  
  
1.  В диспетчере основных данных откройте обозреватель.  
  
2.  Выберите сущность и элемент для отката.  
  
3.  Щелкните **Просмотр журнала**.  
  
4.  Выберите версию для отката и нажмите **Откат**.  
  
## <a name="see-also"></a>См. также:  
 [Журнал изменений элемента (Master Data Services)](../master-data-services/member-revision-history-master-data-services.md)   
 [Изменение типа журнала транзакций сущности (службы Master Data Services)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
  
