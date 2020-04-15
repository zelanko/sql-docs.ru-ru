---
title: Примечания к безопасности потока на функциях API (драйвер ODBC для Oracle) Документы Майкрософт
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
ms.openlocfilehash: 489f0e99ea53d419ff94dddfeb22e37573abb874
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303075"
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Замечания о потокобезопасности функций API (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 Драйвер Microsoft ODBC для Oracle является безопасным для потоков; однако Oracle не допускает несколько одновременных инструкций в одном подключении. Водитель применяет это ограничение. Другими словами, в многопоточных приложениях, хотя любой поток может зайти в драйвер ODBC для Oracle в любое время, драйвер блокирует любой другой поток от драйвера на том же соединении до тех пор, пока исходный поток не покинет драйвер.  
  
 Драйвер не блокирует, если есть два заявления на двух разных соединениях. Однако, если есть единая связь с двумя операторами, есть потенциал для блокировки.
