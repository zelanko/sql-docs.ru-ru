---
title: Закладки с фиксированной длиной Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f90c5888a68506c056b2a56fce516080148528e7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306985"
---
# <a name="fixed-length-bookmarks"></a>Закладки фиксированной длины
Если водитель ODBC *3.x* должен работать с приложением ODBC *2.x,* используюв закладки с фиксированной длиной, водитель должен поддерживать следующее:  
  
-   SQL_UB_ON как значение для опции SQL_USE_BOOKMARKS оператора. (SQL_UB_ON амортизирован в ODBC *3.x*.)  
  
-   Вариант SQL_GET_BOOKMARK оператора.
