---
description: Замечания о потокобезопасности функций API (драйвер ODBC для Oracle)
title: Замечания по безопасности потока для функций API (драйвер ODBC для Oracle) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c7da346832e2682caa02bdbdae91a1133a9cbaa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449086"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Замечания о потокобезопасности функций API (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Драйвер Microsoft ODBC для Oracle является потокобезопасным. Однако Oracle не допускает несколько параллельных операторов для одного соединения. Драйвер применяет это ограничение. Иными словами, в многопоточных приложениях, хотя любой поток может вызывать драйвер ODBC для Oracle в любое время, драйвер блокирует любой другой поток от драйвера в том же соединении, пока исходный поток не покидает драйвер.  
  
 Драйвер не блокируется, если имеется две инструкции для двух разных соединений. Однако при наличии одного соединения с двумя операторами существует вероятность блокировки.
