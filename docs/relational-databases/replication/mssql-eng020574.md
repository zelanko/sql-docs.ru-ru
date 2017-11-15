---
title: "MSSQL_ENG020574 | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG02574 error
ms.assetid: 4e98f8de-287c-4090-81ee-dc8f80dfa6a1
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ff57dd45db47b24ebefddec17179d68f5466821
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqleng020574"></a>MSSQL_ENG020574
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|20574|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Ошибка проверки данных подписки подписчика "%s" на статью "%s" в публикации "%s".|  
  
## <a name="explanation"></a>Объяснение  
 Было проверено соответствие данных на подписчике данным на издателе, данные не совпали; таким образом, проверка завершилась неуспешно. Дополнительные сведения о проверке см. в разделе [Validate Replicated Data](../../relational-databases/replication/validate-replicated-data.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Рекомендуется сделать следующее.  
  
-   Определите причину ошибки проверки.  
  
-   Исправьте основную проблему, вызвавшую ошибку.  
  
-   Устраните конвергенцию данных, повторно инициализировав подписку или применив другой способ.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
