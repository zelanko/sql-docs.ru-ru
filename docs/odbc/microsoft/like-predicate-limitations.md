---
title: КАК предиката ограничения | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cff5bf10c05a85baeb9ad6f36b620785e8e8bab8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="like-predicate-limitations"></a>КАК предиката ограничения
Если данные в столбце длиннее 255 символов, LIKE сравнения будет основываться только на первые 255 символов.  
  
 LIKE используется в процедуре поддерживается только шаблоны констант. Драйверы системной базы данных поддерживает SQL-92 как сравнения с шаблоном.  
  
 Не поддерживается использование предложение escape в предикате LIKE.  
  
 Не следует выполнять сравнение LIKE на столбец, содержащий данные типа данных числовой или число с плавающей запятой. Результаты могут быть непредсказуемыми. Дополнительные сведения см. в разделе *Microsoft Jet базы данных подсистемы Руководство программиста*.
