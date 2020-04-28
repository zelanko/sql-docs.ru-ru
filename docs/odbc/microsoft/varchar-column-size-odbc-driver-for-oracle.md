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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f11e1de3171521c57c80beb207d33e67d26d3e33
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304829"
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>Размер столбца VARCHAR (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 В Oracle8 максимальный размер столбца VARCHAR увеличился с 2000 до 4000 байт. Клиентское программное обеспечение Oracle 7.3. x не позволяет привязать значение параметра, превышающее 2000 байт. Поэтому при создании таблицы со столбцом VARCHAR размером более 2000 байт вы не сможете выполнять параметризованные операции вставки, обновления, удаления и запросы к данным, превышающие ограничение в 2000 байт клиентского программного обеспечения. Так как драйвер ODBC для Oracle и поставщик OLE DB для Oracle используют параметризованные операции вставки, обновления, удаления и запросы, они будут сообщать об ошибках в ORA-01026 в этом случае. Будут работать данные, находящиеся в пределах ограничений, наложенных клиентским программным обеспечением Oracle. Чтобы избежать этого до 2000 байт, необходимо обновить клиентское программное обеспечение до Oracle8 (8.0.4.1.1 c или более поздней версии).
