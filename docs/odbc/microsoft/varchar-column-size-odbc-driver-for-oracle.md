---
title: "Размер столбца VARCHAR (драйвер ODBC для Oracle) | Документы Microsoft"
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
- data types [ODBC], ODBC driver for Oracle
- varchar column size [ODBC]
- ODBC driver for Oracle [ODBC], data types
ms.assetid: eb4cb410-3d00-4251-8c5e-a06f36c4dac7
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fdd09067b2a938a285264955ad0ff05c6455c00a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>Размер столбца VARCHAR (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 В Oracle8 максимальный размер столбца VARCHAR увеличиваться от 2000 до 4 000 байт. Клиентское программное обеспечение Oracle 7.3.x никак не может связать значение больше 2000 байт. Таким образом Если создать таблицу со столбцом VARCHAR размером более 2000 байт, будут недоступны для выполнения параметризованные операции вставки, обновления, удаления и запросов к ней с данными, превышает 2000-байтовое ограничение клиентского программного обеспечения. Поскольку драйвер ODBC для Oracle и поставщик OLE DB для Oracle использовать параметризованные операции вставки, обновления, удаления и запросы, они будут сообщать об ошибках ORA-01026 в этом случае. Данные, которые предельным регламентированный клиентское программное обеспечение Oracle будет работать. Чтобы избежать это 2000-байтовое ограничение, необходимо обновить клиентское по до Oracle8 (8.0.4.1.1c или более поздней версии).
