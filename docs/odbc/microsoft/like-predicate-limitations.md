---
title: LIKE Предикатные ограничения Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6d596d688956d7bdbf3d9125184d81c16249781c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298964"
---
# <a name="like-predicate-limitations"></a>Ограничения предиката LIKE
Если данные в столбце длиннее 255 символов, сравнение LIKE будет основываться только на первых 255 символах.  
  
 LIKE, используемый в процедуре, поддерживается только постоянными шаблонами. Драйверы настольных баз данных поддерживают сопоставление шаблонов S'L-92 LIKE.  
  
 Использование оговорки о побеге в предикате LIKE не поддерживается.  
  
 Сравнение LIKE не должно выполняться на столбце, содержащем данные типа численных или плавающих данных. Результаты могут быть непредсказуемыми. Для получения дополнительной информации, *см.*
