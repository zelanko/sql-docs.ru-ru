---
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
ms.openlocfilehash: e035e3ec53c5b5494c029d6840b9f5c836821209
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299864"
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
  
 *плюс-знак* :: =*+*  
  
 *минус-Sign* :: =-  
  
 *digit* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *period* :: =.
