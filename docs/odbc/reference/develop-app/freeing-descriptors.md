---
description: Освобождение дескрипторов
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 95c87b7ac70369509a72ff539c63ac888e5f3262
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465806"
---
# <a name="freeing-descriptors"></a>Освобождение дескрипторов
Явно выделенные дескрипторы можно освободить явно, вызвав **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_DESC или неявно, при освобождении дескриптора соединения. При освобождении явно выделенного дескриптора все дескрипторы инструкций, к которым применяется освобожденный дескриптор, автоматически возвращаются к дескрипторам, неявно выделенным для них.  
  
 Неявно выделенные дескрипторы можно освободить только путем вызова **SQLDisconnect**, который удаляет любые операторы или дескрипторы, открытые в соединении, либо вызывая **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_STMT, чтобы освободить дескриптор инструкции и все неявно выделенные дескрипторы, связанные с инструкцией. Неявно выделенный дескриптор не может быть освобожден путем вызова **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_DESC.  
  
 Даже при освобождении неявно выделенный дескриптор остается допустимым, и **SQLGetDescField** может быть вызван для своих полей.
