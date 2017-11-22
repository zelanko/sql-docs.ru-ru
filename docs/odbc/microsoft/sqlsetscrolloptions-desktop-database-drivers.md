---
title: "SQLSetScrollOptions (для настольных баз данных драйверы) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4b1c1a395b6915c79a6f30509f7fbb4c507dd8ba
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (драйверы для настольных баз данных)
Прямой и статические курсоры поддерживаются для SQL_CONCUR_READ_ONLY.  
  
 Только управляемые набором ключей курсоры поддерживаются для *fConcurrency* аргумент SQL_CONCUR_LOCK.  
  
 *FConcurrency* аргумент SQL_CONCUR_ROWVER не поддерживается.  
  
 Динамические курсоры и смешанного курсоры не поддерживаются.
