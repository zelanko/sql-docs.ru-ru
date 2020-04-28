---
title: Ограничения предложения WHERE | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1699397db81d6fe702f60f6953fe7a0ae3726fe3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307565"
---
# <a name="where-clause-limitations"></a>Ограничения предложения WHERE
Максимальное число предложений в предложении WHERE равно 40.  
  
 Столбцы LONGVARBINARY и LONGVARCHAR можно сравнивать с литералами длиной до 255 символов, но не могут сравниваться с помощью параметров.
