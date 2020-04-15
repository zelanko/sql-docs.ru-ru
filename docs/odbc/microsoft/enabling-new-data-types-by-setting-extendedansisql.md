---
title: Включение новых типов данных путем установки РасширенныйAnsiS'L (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303415"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Включение новых типов данных путем установки ExtendedAnsiSQL
Два новых типа данных доступны в базах данных Jet 4.0 при включении флага ExtendedAnsiS'L: SQL_DECIMAL и SQL_NUMERIC. Точность и масштаб по умолчанию составляют 18 и 0 соответственно. Данные, доступные через ODBC, которые набраны как SQL_DECIMAL или SQL_NUMERIC будут отображены на Microsoft Jet Decimal вместо валюты.  
  
 При выключении флага ExtendedAnsiS'L нельзя создавать таблицы с десятичными или числовыми типами, и эти типы не будут отображаться в S'LGetTypeInfo(). Однако, если таблица содержит новые типы данных, они могут быть использованы с правильными типами данных.
