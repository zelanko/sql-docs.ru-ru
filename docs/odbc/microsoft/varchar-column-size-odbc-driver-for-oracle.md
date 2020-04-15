---
title: Размер колонки VARCHAR (драйвер ODBC для Oracle) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304829"
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>Размер столбца VARCHAR (драйвер ODBC для Oracle)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 В Oracle8 максимальный размер колонны VARCHAR увеличился с 2000 до 4000 байтов. Клиентское программное обеспечение Oracle 7.3.x не может связать значение параметра, превышающее 2000 байтов. Таким образом, если вы создадите таблицу с столбцом VARCHAR размером более 2000 байтов, вы не сможете выполнять параметризированные вставки, обновления, удаления и запросы против нее с данными, превышающеми 2000-байт лимит программного обеспечения клиента. Поскольку как ODBC Driver для Oracle, так и поставщик OLE DB для Oracle используют параметризированные вставки, обновления, удаления и запросы, в этом случае они сообщат об ошибках ORA-01026. Данные, накоторыемые клиентским программным обеспечением Oracle, будут работать. Чтобы избежать этого лимита в 2000 байт, необходимо обновить клиентское программное обеспечение до Oracle8 (8.0.4.1.1c или выше).
