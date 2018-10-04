---
title: Синтаксисе числовых литералов | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18b1c144e84bf0be5aaeb68b66660f7bc7865ade
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601542"
---
# <a name="numeric-literal-syntax"></a>Синтаксис числовых литералов
Для числовых литералов в ODBC используется следующий синтаксис:  
  
 *числовой литерал* :: = *автоматический numeric-literal &#124; unsigned-numeric-literal*  
  
 *автоматический numeric-literal* :: = [*входа*] *unsigned-numeric-literal*  
  
 *неподписанные numeric-literal* :: = *точные числовые литералов &#124; приблизительных числовых литералов*  
  
 *точные числовые литералов* :: = *unsigned integer* [*период*[*unsigned integer*]]  *&#124;периода unsigned integer*  
  
 *знак* :: = *плюс &#124; минус*  
  
 *Приблизительное числовое литералов* :: = *показатель степени мантиссы E*  
  
 *мантисса* :: = *точные числовые литералов*  
  
 *показатель степени* :: = *автоматический целое число*  
  
 *автоматический целое число* :: = [*входа*] *unsigned integer*  
  
 *unsigned integer* :: = *цифра...*  
  
 *плюс* :: = *+*  
  
 *минус* :: = -  
  
 *цифра* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *период* :: =.
