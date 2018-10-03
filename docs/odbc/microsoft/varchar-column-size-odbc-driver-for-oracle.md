---
title: Размер столбца VARCHAR (драйвер ODBC для Oracle) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- varchar column size [ODBC]
- ODBC driver for Oracle [ODBC], data types
ms.assetid: eb4cb410-3d00-4251-8c5e-a06f36c4dac7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db2871324f92ef6d84a8bf8313db105489100a96
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47847572"
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>Размер столбца VARCHAR (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 В Oracle8 максимальный размер столбца VARCHAR увеличен с 2000 до 4000 байтов. Клиентское программное обеспечение Oracle 7.3.x никак не может связать значение размером более 2000 байтов. Таким образом Если создать таблицу со столбцом VARCHAR размером более 2000 байтов, невозможно выполнять параметризованные операции вставки, обновления, удаления и запросы к ним с данными, превышает ограничение в 2000-байтовое клиентского программного обеспечения. Так как драйвер ODBC для Oracle и поставщик OLE DB для Oracle использовать параметризованные операции вставки, обновления, удаления и запросы, они будут сообщать об ошибках ORA-01026 в данном случае. Данные, которые лежат в пределах, обеспечиваемая клиентское программное обеспечение Oracle будет работать. Чтобы избежать это 2000-байтовое ограничение, необходимо обновить клиентского программного обеспечения до Oracle8 (8.0.4.1.1c или более поздней версии).
