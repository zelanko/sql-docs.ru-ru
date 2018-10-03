---
title: Освобождение дескрипторов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
- descriptors [ODBC], allocating and freeing
- freeing descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 317213f4-0ebb-4bf8-a37a-4d6b1313823f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d643ccad0110796127524a10e82aef7c3339b163
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694633"
---
# <a name="freeing-descriptors"></a>Освобождение дескрипторов
Явно выделенные дескрипторы могут быть освобождены либо явно, путем вызова **SQLFreeHandle** с *HandleType* SQL_HANDLE_DESC или неявно, когда дескриптор соединения освобождается. Когда освобождается явно выделенные дескриптор, все дескрипторы инструкций, к которым дескриптор освобожденные применяется автоматически вернуться к дескрипторам неявно выделенную для них.  
  
 Неявно выделенные дескрипторы может быть освобожден только путем вызова **SQLDisconnect**, отбрасывает все инструкции или откройте дескрипторы для соединения или путем вызова **SQLFreeHandle** с  *HandleType* значение sql_handle_stmt дескриптора инструкции и неявно выделенные дескрипторы, связанные с инструкцией. Неявно выделенные дескриптор не могут быть освобождены, вызвав **SQLFreeHandle** с *HandleType* из SQL_HANDLE_DESC.  
  
 Даже в том случае, если освобождения дескриптора неявно выделенные остается допустимым, и **SQLGetDescField** могут быть вызваны для его поля.
