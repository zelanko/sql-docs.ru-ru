---
title: Освобождение дескрипторов | Документы Microsoft
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
- SQLFreeHandle function [ODBC]
- descriptors [ODBC], allocating and freeing
- freeing descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 317213f4-0ebb-4bf8-a37a-4d6b1313823f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0977ba814841ab2fa445a1009262e4a2bfd3a5b3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="freeing-descriptors"></a>Освобождение дескрипторов
Может быть явно выделенный дескрипторы явно, либо освободить путем вызова **SQLFreeHandle** с *HandleType* SQL_HANDLE_DESC или неявно, когда дескриптор соединения освобождается. Когда освобождается явно выделенный дескриптор, все дескрипторы инструкций, к которым освобожденные дескриптора, применяются автоматически восстановить дескрипторы неявно выделенную для них.  
  
 Можно освободить неявно выделенном дескрипторы только путем вызова **SQLDisconnect**, который удаляет все инструкции или дескрипторы открытия соединения или путем вызова **SQLFreeHandle** с  *HandleType* значение sql_handle_stmt для освобождения дескриптора инструкции и неявно выделенном дескрипторы, связанные с инструкцией. Дескриптор неявно выделенном не могут быть освобождены вызовом **SQLFreeHandle** с *HandleType* из SQL_HANDLE_DESC.  
  
 Даже в том случае, если освобожден, неявно выделенный дескриптор действителен, и **SQLGetDescField** может быть вызван для ее полей.
