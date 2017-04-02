---
title: "Откат журнала изменений элемента (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d39d3474-20e7-429f-9c8d-fcc4eb0854fc
caps.latest.revision: 5
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 5
---
# Откат журнала изменений элемента (Master Data Services)
  Запись в журнал изменений элемента осуществляется каждый раз при изменении элемента. Существует возможность откатить журнал изменений элемента к предыдущей версии.  
  
## Предварительные требования  
  
-   Необходимо иметь разрешение на обновление хотя бы одного из атрибутов выбранного элемента. При откате журнала изменений все значения атрибутов, которые могут быть обновлены, откатываются к значениям предыдущей версии.  
  
-   Журнал изменений доступен, только если типом журнала транзакций сущности является элемент.  
  
 **Откат журнала изменений элемента**  
  
1.  В диспетчере основных данных откройте обозреватель.  
  
2.  Выберите сущность и элемент для отката.  
  
3.  Щелкните **Просмотр журнала**.  
  
4.  Выберите версию для отката и нажмите **Откат**.  
  
## См. также:  
 [Журнал изменений элемента (Master Data Services)](../master-data-services/member-revision-history-master-data-services.md)   
 [Изменение типа журнала транзакций сущности (Master Data Services)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
  