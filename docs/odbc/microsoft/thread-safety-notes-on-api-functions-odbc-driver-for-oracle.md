---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 926b2285bcce9a28579fffc4004c5454b2837392
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912437"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Замечания о потокобезопасности функций API (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Драйвер Microsoft ODBC для Oracle является потокобезопасным. Однако Oracle не допускает несколько параллельных операторов для одного соединения. Драйвер применяет это ограничение. Иными словами, в многопоточных приложениях, хотя любой поток может вызывать драйвер ODBC для Oracle в любое время, драйвер блокирует любой другой поток от драйвера в том же соединении, пока исходный поток не покидает драйвер.  
  
 Драйвер не блокируется, если имеется две инструкции для двух разных соединений. Однако при наличии одного соединения с двумя операторами существует вероятность блокировки.
