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
manager: craigg
ms.openlocfilehash: 8035eed9e0aaff1f914f386b6d4bc9f2d65f9a0f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63192351"
---
# <a name="like-predicate-limitations"></a>Ограничения предиката LIKE
Если данные в столбце длиннее 255 символов, LIKE сравнения будет зависеть только первые 255 символов.  
  
 LIKE используется в процедуре поддерживается только шаблоны констант. Драйверы для баз данных Desktop поддерживают SQL-92 как сопоставление шаблонов.  
  
 Не поддерживается использование предложение escape в предикате LIKE.  
  
 Не следует выполнять сравнение LIKE на столбец, содержащий данные типа данных числовой или число с плавающей запятой. Результаты могут быть непредсказуемыми. Дополнительные сведения см. в разделе *Microsoft Jet Database Engine Programmer's Guide*.
