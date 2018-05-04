---
title: SQLSetScrollOptions (для настольных баз данных драйверы) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6014ce55b2de2279c060361ed7e6131fd7e8b030
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (драйверы для настольных баз данных)
Прямой и статические курсоры поддерживаются для SQL_CONCUR_READ_ONLY.  
  
 Только управляемые набором ключей курсоры поддерживаются для *fConcurrency* аргумент SQL_CONCUR_LOCK.  
  
 *FConcurrency* аргумент SQL_CONCUR_ROWVER не поддерживается.  
  
 Динамические курсоры и смешанного курсоры не поддерживаются.
