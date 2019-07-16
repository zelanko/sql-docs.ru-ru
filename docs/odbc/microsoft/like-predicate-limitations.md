---
title: Ограничения предиката LIKE | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8cd3cebfcf20df2f8a3a786ea66fd28dd76307c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119710"
---
# <a name="like-predicate-limitations"></a>Ограничения предиката LIKE
Если данные в столбце длиннее 255 символов, LIKE сравнения будет зависеть только первые 255 символов.  
  
 LIKE используется в процедуре поддерживается только шаблоны констант. Драйверы для баз данных Desktop поддерживают SQL-92 как сопоставление шаблонов.  
  
 Не поддерживается использование предложение escape в предикате LIKE.  
  
 Не следует выполнять сравнение LIKE на столбец, содержащий данные типа данных числовой или число с плавающей запятой. Результаты могут быть непредсказуемыми. Дополнительные сведения см. в разделе *Microsoft Jet Database Engine Programmer's Guide*.
