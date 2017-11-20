---
title: "Включение новых типов данных, задав ExtendedAnsiSQL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extendedANSISQL [ODBC], enabling new data types
ms.assetid: f2865543-7fff-44fa-9a6a-968bec33acdc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5161224a5d4fe3f0bf2af200a5cff3e1ea4e1008
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Включение новых типов данных, задав ExtendedAnsiSQL
Два новых типа данных доступны в базы данных Jet 4.0, если установлен флаг ExtendedAnsiSQL: SQL_DECIMAL и SQL_NUMERIC. По умолчанию точность и масштаб, 18 и 0 соответственно. Доступ к ней через ODBC, который типизируется как SQL_DECIMAL или SQL_NUMERIC данных будет сопоставлен Microsoft Jet десятичное вместо валюты.  
  
 При отключении флаг ExtendedAnsiSQL нельзя создавать таблицы с десятичным или числовым типам, и эти типы не будут отображаться в SQLGetTypeInfo(). Тем не менее если таблица содержит новые типы данных, их можно использовать с типами данных.

