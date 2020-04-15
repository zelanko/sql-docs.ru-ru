---
title: Числовой литературный синтаксис Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299864"
---
# <a name="numeric-literal-syntax"></a>Синтаксис числовых литералов
Следующий синтаксис используется для цифровых букв в ODBC:  
  
 *числов-буквальный* ::" *подписанный-числов-буквальный &#124; неподписанных-число-буквальных*  
  
 *подписан-числов-буквальный* :: «*знак*» - *неподписанный числовиальный*  
  
 *неподписанный-числовиальный (цифровой)":* *точно-числово-буквальный &#124; приблизительно-числово-буквальный*  
  
 *точно-числов-буквальный* :: *»неподписанный-integer* »*период*»*неподписанный-integer* *&#124;период unsigned-integer*  
  
 *знак* ::" *плюс-знак &#124; минус-знак*  
  
 *приблизительно-числов-буквальный::* *гницу E экспонента*  
  
 *мантисса* ::: *точно-числов-буквальный*  
  
 *экспонент* ::» *подписан-integer*  
  
 *подписано-integer* :::*знак*- *неподписанный-integer*  
  
 *неподписанных-integer* :: *» цифра ...*  
  
 *плюс-знак* ::»*+*  
  
 *минус-знак* ::" -  
  
 *цифра* ::» 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *период* ::» .
