---
description: Синтаксис числовых литералов
title: Синтаксис числового литерала | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be87238f1663bcf9b12d40cb90521bb404a25af3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425016"
---
# <a name="numeric-literal-syntax"></a>Синтаксис числовых литералов
Для числовых литералов в ODBC используется следующий синтаксис:  
  
 *числовой литерал* :: =- *numeric-Literal &#124; без знака-числового литерала*  
  
 *знак-numeric-Literal* :: = [*знак*] *без знака — числовой литерал*  
  
 *неподписанный-numeric-Literal* :: = *СОВПАД-numeric-Literal &#124; приблизительный числовой литерал*  
  
 *СОВПАД-numeric-Literal* :: = *без знака-целое число* [*точка*[*без знака-целое*]] *&#124;периода без знака — целое число*  
  
 *знак* :: = *плюс-знак &#124; минус-знак*  
  
 Примерное значение экспоненты " *приблизительный-числовой литерал* :: = *мантисса E* "  
  
 *мантисса* :: = *СОВПАД-numeric-Literal*  
  
 *экспонента* :: = *целое число со знаком*  
  
 *знак-целое* :: = [*знак*] без *знака — целое число*  
  
 *без знака — целое число* :: = *цифра...*  
  
 *плюс-знак* :: = *+*  
  
 *минус-Sign* :: =-  
  
 *digit* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *period* :: =.
