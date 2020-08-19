---
description: Добавить подписчик, отличный от подписчика SQL Server
title: Добавление подписчика, отличного от подписчика SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b2bb31950f257054279fc9d9ad354f48b50b9ca4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423658"
---
# <a name="add-non-sql-server-subscriber"></a>Добавить подписчик, отличный от подписчика SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Репликация поддерживает принудительные подписки на моментальные снимки и публикации транзакций для подписчиков Oracle и IBM DB2.  
  
## <a name="options"></a>Параметры  
 **Тип добавляемого подписчика:**  
 Выберите подписчик Oracle или подписчик IBM DB2. Дополнительные сведения о поддержке таких подписчиков см. в статье [Подписчики, отличные от подписчиков SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
 **Имя источника данных**  
 Данное имя позволяет найти базу данных в сети. Строка соединения с базой данных, формируемая репликацией, содержит имя источника данных, имя входа, пароль и параметры соединения, указанные на странице **Безопасность агента распространителя** данного мастера.  
  
> [!NOTE]
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не проверяет имя источника данных и строку подключения, пока агент распространителя не попытается инициализировать подписку.  
  
## <a name="see-also"></a>См. также  
 [Создание подписки для подписчика, отличного от подписчика SQL Server](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
