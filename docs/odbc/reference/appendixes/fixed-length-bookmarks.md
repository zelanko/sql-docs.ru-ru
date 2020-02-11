---
title: Закладки с фиксированной длиной | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5877a6cb7a99803f854338321e333c87037c2e90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67913587"
---
# <a name="fixed-length-bookmarks"></a>Закладки фиксированной длины
Если драйвер ODBC *3. x* должен работать с приложением ODBC *2. x* , использующим закладки фиксированной длины, драйвер должен поддерживать следующее:  
  
-   SQL_UB_ON в качестве значения параметра инструкции SQL_USE_BOOKMARKS. (SQL_UB_ON не рекомендуется использовать в ODBC *3. x*.)  
  
-   Параметр инструкции SQL_GET_BOOKMARK.
