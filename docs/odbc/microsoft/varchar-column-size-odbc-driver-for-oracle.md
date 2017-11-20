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
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- varchar column size [ODBC]
- ODBC driver for Oracle [ODBC], data types
ms.assetid: eb4cb410-3d00-4251-8c5e-a06f36c4dac7
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 57dcc53769c9b5ba80f5c949436f0b3eb2ce08b1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>Размер столбца VARCHAR (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 В Oracle8 максимальный размер столбца VARCHAR увеличиваться от 2000 до 4 000 байт. Клиентское программное обеспечение Oracle 7.3.x никак не может связать значение больше 2000 байт. Таким образом Если создать таблицу со столбцом VARCHAR размером более 2000 байт, будут недоступны для выполнения параметризованные операции вставки, обновления, удаления и запросов к ней с данными, превышает 2000-байтовое ограничение клиентского программного обеспечения. Поскольку драйвер ODBC для Oracle и поставщик OLE DB для Oracle использовать параметризованные операции вставки, обновления, удаления и запросы, они будут сообщать об ошибках ORA-01026 в этом случае. Данные, которые предельным регламентированный клиентское программное обеспечение Oracle будет работать. Чтобы избежать это 2000-байтовое ограничение, необходимо обновить клиентское по до Oracle8 (8.0.4.1.1c или более поздней версии).

