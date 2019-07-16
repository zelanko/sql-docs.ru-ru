---
title: ГДЕ ограничения предложения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, WHERE clause limitations
- WHERE clause limitations [ODBC]
ms.assetid: 46b54f74-e4a3-4318-87cf-8a97c38a2718
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bb6194d93e545526a850443f5e97074d88e7e1b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67911427"
---
# <a name="where-clause-limitations"></a>Ограничения предложения WHERE
Максимальное количество предложений в предложении WHERE — 40.  
  
 Столбцы LONGVARBINARY и LONGVARCHAR можно сравнивать с литералы до 255 символов в длину, но нельзя сравнивать с помощью параметров.
