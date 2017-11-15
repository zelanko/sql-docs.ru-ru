---
title: "Значения функции HOST_NAME Values | Документация Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c14e995d8e5f27ec5df6bda0d605c5f6a662386a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="hostname-values"></a>Значения функции HOST_NAME
  Публикации слиянием с параметризованными фильтрами используют функции SUSER_SNAME() или HOST_NAME() для фильтрации данных. Функция задается в мастере создания публикаций или диалоговом окне **Свойства публикации** .  
  
 По умолчанию функция HOST_NAME() возвращает имя компьютера, подключающегося к издателю. При использовании параметризованных фильтров принято заменять это значение, указав новое значение на данной странице мастера. В этом случае функция HOST_NAME() будет возвращать указанное значение вместо имени компьютера. Дополнительные сведения см. в главе "Переопределение значения функции HOST_NAME()" в статье [Параметризованные фильтры строк](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
> [!NOTE]  
>  Если переопределить функцию HOST_NAME(), все вызовы этой функции будут возвращать указанное значение. Убедитесь, что другие приложения не зависят от того, возвращает ли функция HOST_NAME() имя компьютера.  
  
## <a name="options"></a>Параметры  
 **Свойства подписки**  
 Введите значения для каждого подписчика в столбце **Значение HOST_NAME** или оставьте значение по умолчанию, которое соответствует имени компьютера подписчика.  
  
## <a name="see-also"></a>См. также:  
 [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Просмотр и изменение свойств подписки по запросу](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Просмотр и изменение свойств принудительной подписки](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [HOST_NAME (Transact-SQL)](../../t-sql/functions/host-name-transact-sql.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
