---
title: "Заметки о безопасности потока на API-функции (драйвер ODBC для Oracle) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6037a11f71d5fc6af4d9f173974fc91c80833fc0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Заметки о безопасности потока на API-функции (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Драйвер ODBC для Oracle является потокобезопасным; Oracle допускает несколько одновременно выполняемых инструкций, в одном соединении. Это ограничение соблюдается драйвер. Иными словами в многопоточных приложениях, несмотря на то, что драйвер ODBC для Oracle в любое время можно вызывать любой поток драйвер блоков любого другого потока с помощью драйвера, в том же соединении пока исходный поток покидает драйвер.  
  
 Драйвер не блокируется, если имеются две инструкции на двух разных подключений. Тем не менее есть одно соединение с двумя инструкциями, существует ли потенциальные блокировки.
