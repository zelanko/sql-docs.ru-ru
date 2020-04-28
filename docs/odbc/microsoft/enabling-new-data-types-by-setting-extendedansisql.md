---
title: Включение новых типов данных с помощью параметра ExtendedAnsiSQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], enabling new data types
ms.assetid: f2865543-7fff-44fa-9a6a-968bec33acdc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b703c5c14c4743e13feee139d16e5dfeb3c24c63
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303415"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Включение новых типов данных путем установки ExtendedAnsiSQL
При включении флага ExtendedAnsiSQL в базах данных Jet 4,0 доступны два новых типа данных: SQL_DECIMAL и SQL_NUMERIC. Точность и масштаб по умолчанию равны 18 и 0 соответственно. Данные, доступные через ODBC, которые введены как SQL_DECIMAL или SQL_NUMERIC, будут сопоставляться с десятичной запятой Microsoft Jet вместо Currency.  
  
 Если флаг ExtendedAnsiSQL отключен, нельзя создавать таблицы с десятичными или числовыми типами, и эти типы не будут отображаться в SQLGetTypeInfo (). Однако если таблица содержит новые типы данных, их можно использовать с правильными типами данных.
