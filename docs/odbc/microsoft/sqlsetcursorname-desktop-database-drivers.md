---
title: "SQLSetCursorName (для настольных баз данных драйверы) | Документы Microsoft"
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
helpviewer_keywords: SQLSetCursorName function [ODBC], Desktop Database Drivers
ms.assetid: 9bd7c87b-d99d-4e23-b2db-868d3b461c94
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eb398e51768ea9261e360c3ce7088b4ee30ec128
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (драйверы для настольных баз данных)
Так как драйвер не поддерживает позиционированного обновления или удаления, WHERE CURRENT OF *cursorname* синтаксис, **SQLSetCursorName** поддерживается, но не может использоваться для позиционированных обновлений. Он может использоваться только при включенном библиотеку курсоров и приложение использует **SQLExtendedFetch**.
