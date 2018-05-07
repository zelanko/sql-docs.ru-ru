---
title: SQLSpecialColumns (для настольных баз данных драйверы) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Desktop Database Drivers
ms.assetid: 3de66fdf-053b-4354-979d-e76a5a5e975f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aebdcc1d45584ec0fa7d287715e2defc8ef278fb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (драйверы для настольных баз данных)
Уникальный индекс будет возвращаться (при наличии) для флага SQL_BEST_ROWID в *fColType*. Результирующий набор не возвращается для флага SQL_ROWVER.  
  
 Все идентификаторы строк имеют область SQL_SCOPE_CURROW.  
  
 Соответствие шаблону не поддерживается для любого *szTableQualifier* или *szTableName* аргумент.
