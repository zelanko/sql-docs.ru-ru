---
title: Заметки о безопасности потока на API-функции (драйвер ODBC для Oracle) | Документы Microsoft
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
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 31ac813b6419b75f63ee9c7152f888dd1396238e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Заметки о безопасности потока на API-функции (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Драйвер ODBC для Oracle является потокобезопасным; Oracle допускает несколько одновременно выполняемых инструкций, в одном соединении. Это ограничение соблюдается драйвер. Иными словами в многопоточных приложениях, несмотря на то, что драйвер ODBC для Oracle в любое время можно вызывать любой поток драйвер блоков любого другого потока с помощью драйвера, в том же соединении пока исходный поток покидает драйвер.  
  
 Драйвер не блокируется, если имеются две инструкции на двух разных подключений. Тем не менее есть одно соединение с двумя инструкциями, существует ли потенциальные блокировки.
