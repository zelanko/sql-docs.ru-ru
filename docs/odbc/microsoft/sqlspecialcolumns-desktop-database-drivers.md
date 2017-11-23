---
title: "SQLSpecialColumns (для настольных баз данных драйверы) | Документы Microsoft"
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
helpviewer_keywords: SQLSpecialColumns function [ODBC], Desktop Database Drivers
ms.assetid: 3de66fdf-053b-4354-979d-e76a5a5e975f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 295a5a048335cc9828ad49b02c51a7e01805a094
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (драйверы для настольных баз данных)
Уникальный индекс будет возвращаться (при наличии) для флага SQL_BEST_ROWID в *fColType*. Результирующий набор не возвращается для флага SQL_ROWVER.  
  
 Все идентификаторы строк имеют область SQL_SCOPE_CURROW.  
  
 Соответствие шаблону не поддерживается для любого *szTableQualifier* или *szTableName* аргумент.
