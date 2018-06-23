---
title: MSSQL_ENG014157 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014157 error
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: eccf8c32c5e84bd658ef29fc0176f03fd4e77be4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192426"
---
# <a name="mssqleng014157"></a>MSSQL_ENG014157
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14157|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Подписка, созданная подписчиком "%s" на издателе "%s", истекла и была удалена.|  
  
## <a name="explanation"></a>Объяснение  
 Подписчик должен синхронизироваться с издателем в течение времени, указанного в сроке хранения публикации. Если подписчик не будет синхронизирован в указанный период, то срок действия подписки истечет. Дополнительные сведения см. в разделе [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Прежде чем подписчик сможет снова получать изменения данных, подписка должна быть создана и инициализирована заново:  
  
-   Дополнительные сведения о создании подписок см. в статье [Подписка на публикации](subscribe-to-publications.md).  
  
-   Сведения об инициализации подписок см. в [этой статье](initialize-a-subscription.md).  
  
 Если в базе данных подписки содержатся изменения, которые не были синхронизированы с издателем, при помощи [tablediff Utility](../../tools/tablediff-utility.md) можно определить, какие строки в базах данных публикации и подписки отличаются.  
  
 Срок действия подписок можно продлить, увеличив срок хранения публикации. Не рекомендуется задавать слишком большое значение, поскольку это может привести к хранению большего объема данных и метаданных, что оказывает отрицательное влияние на производительность. Дополнительные сведения см. в разделе [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)  
  
  