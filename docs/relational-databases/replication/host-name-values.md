---
description: Значения функции HOST_NAME
title: Значения функции HOST_NAME Values | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 32926ab1c2e5dcd2c97d296d07c5fab725793f47
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427956"
---
# <a name="host_name-values"></a>Значения функции HOST_NAME
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Публикации слиянием с параметризованными фильтрами используют функции SUSER_SNAME() или HOST_NAME() для фильтрации данных. Функция задается в мастере создания публикаций или диалоговом окне **Свойства публикации** .  
  
По умолчанию функция HOST_NAME() возвращает имя компьютера, подключающегося к издателю. При использовании параметризованных фильтров принято заменять это значение, указав новое значение на данной странице мастера. В этом случае функция HOST_NAME() будет возвращать указанное значение вместо имени компьютера. Дополнительные сведения см. в главе "Переопределение значения функции HOST_NAME()" в статье [Параметризованные фильтры строк](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
> [!NOTE]  
>  Если переопределить функцию HOST_NAME(), все вызовы этой функции будут возвращать указанное значение. Убедитесь, что другие приложения не зависят от того, возвращает ли функция HOST_NAME() имя компьютера.  
  
## <a name="options"></a>Параметры  
 **Свойства подписки**  
 Введите значения для каждого подписчика в столбце **Значение HOST_NAME** или оставьте значение по умолчанию, которое соответствует имени компьютера подписчика.  
  
## <a name="see-also"></a>См. также:  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Просмотр и изменение свойств подписки по запросу](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Просмотр и изменение свойств принудительной подписки](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [HOST_NAME (Transact-SQL)](../../t-sql/functions/host-name-transact-sql.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
