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
ms.openlocfilehash: fe489222c026c1499135b716f0485bb04f51bad9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069773"
---
# <a name="freeing-descriptors"></a>Освобождение дескрипторов
Явно выделенные дескрипторы можно освободить явно, вызвав **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_DESC или неявно, при освобождении дескриптора соединения. При освобождении явно выделенного дескриптора все дескрипторы инструкций, к которым применяется освобожденный дескриптор, автоматически возвращаются к дескрипторам, неявно выделенным для них.  
  
 Неявно выделенные дескрипторы можно освободить только путем вызова **SQLDisconnect**, который удаляет любые операторы или дескрипторы, открытые в соединении, либо вызывая **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_STMT, чтобы освободить дескриптор инструкции и все неявно выделенные дескрипторы, связанные с инструкцией. Неявно выделенный дескриптор не может быть освобожден путем вызова **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_DESC.  
  
 Даже при освобождении неявно выделенный дескриптор остается допустимым, и **SQLGetDescField** может быть вызван для своих полей.
