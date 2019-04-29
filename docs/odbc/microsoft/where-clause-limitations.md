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
manager: craigg
ms.openlocfilehash: e883d585db0fe11e92b188b2cfc26db9fff415fe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057775"
---
# <a name="where-clause-limitations"></a>Ограничения предложения WHERE
Максимальное количество предложений в предложении WHERE — 40.  
  
 Столбцы LONGVARBINARY и LONGVARCHAR можно сравнивать с литералы до 255 символов в длину, но нельзя сравнивать с помощью параметров.
