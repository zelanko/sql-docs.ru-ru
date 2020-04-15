---
title: Освобождение дескрипторов Документы Майкрософт
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
ms.openlocfilehash: af30ceb29e032764b89aa2069086aa898a7d35db
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305605"
---
# <a name="freeing-descriptors"></a>Освобождение дескрипторов
Явно выделенные дескрипторы могут быть освобождены либо явно, позвонив в **S'LFreeHandle** с *помощью HandleType* SQL_HANDLE_DESC, либо косвенно, когда ручка соединения освобождается. При освобождении явно выделенного дескриптора все ручки оператора, к которым применяется освободившийся дескриптор, автоматически возвращаются к неявно выделенным для них дескрипторам.  
  
 Неявно выделенные дескрипторы могут быть освобождены только по телефону **S'LDisconnect,** который отбрасывает любые операторы или дескрипторы, открытые на подключении, или вызывая **S'LFreeHandle** с *помощью handleType* SQL_HANDLE_STMT освободить ручку оператора и все неявно выделенные дескрипторы, связанные с оператором. Неявно выделенный дескриптор не может быть освобожден, позвонив по **s'LFreeHandle** с *помощью HandleType* of SQL_HANDLE_DESC.  
  
 Даже при освобождении неявно выделенный дескриптор остается в силе, и на его полях можно вызывать **S'LGetDescField.**
