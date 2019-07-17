---
title: Включение новых типов данных путем установки ExtendedAnsiSQL | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 88f11adcab09dbe6964bfd67a944912fc185bccb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031122"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Включение новых типов данных путем установки ExtendedAnsiSQL
Два новых типа данных доступны в базах данных Jet 4.0, при включении флага ExtendedAnsiSQL: SQL_DECIMAL и SQL_NUMERIC. По умолчанию точность и масштаб — 18 и 0 соответственно. Данные, доступные через ODBC, который типизируется как SQL_DECIMAL или SQL_NUMERIC будет сопоставляться с Microsoft Jet Decimal, а не валюты.  
  
 При выключенном флаг ExtendedAnsiSQL нельзя создавать таблицы с десятичным или числовым типам, и эти типы не будут отображаться в SQLGetTypeInfo(). Тем не менее если таблица содержит новые типы данных, они могут использоваться с типами правильные данные.
