---
title: "КАК предиката ограничения | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5668f03e785c0d27133965f16af40ce69c2a2567
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="like-predicate-limitations"></a>КАК предиката ограничения
Если данные в столбце длиннее 255 символов, LIKE сравнения будет основываться только на первые 255 символов.  
  
 LIKE используется в процедуре поддерживается только шаблоны констант. Драйверы системной базы данных поддерживает SQL-92 как сравнения с шаблоном.  
  
 Не поддерживается использование предложение escape в предикате LIKE.  
  
 Не следует выполнять сравнение LIKE на столбец, содержащий данные типа данных числовой или число с плавающей запятой. Результаты могут быть непредсказуемыми. Дополнительные сведения см. в разделе *Microsoft Jet базы данных подсистемы Руководство программиста*.

