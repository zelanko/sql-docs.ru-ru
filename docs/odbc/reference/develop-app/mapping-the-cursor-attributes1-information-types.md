---
title: Сопоставление типов сведений атрибутов1 курсора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], mapping cursor attributes1 information types
- application upgrades [ODBC], mapping cursor attributes1 information types
- mapping cursor attributes1 information types [ODBC]
- backward compatibility [ODBC], mapping cursor attributes1 information types
- upgrading applications [ODBC], mapping cursor attributes1 information types
ms.assetid: 9f112449-ca86-45ac-a865-e6174d67f91b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e9549c442e301f3a6ed8d3da9c73d52177adf01
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62628903"
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Сопоставление типов сведений атрибутов1 курсора
Когда ODBC 3. *x* приложение вызывает **SQLGetInfo** в ODBC 2 *.x* драйвер с типом SQL_XXXX_CURSOR_ATTRIBUTES1 сведения (для динамической, однонаправленные, управляемые набором ключей, или статические курсоры), определяется параметр битов, возвращаемых диспетчером драйверов ODBC 2. *x* драйвер возвращает для соответствующего ODBC 2. *x* типы сведений. Биты установлены в том случае, как показано в следующей таблице.  
  
|Бит в<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|Тип курсора|ODBC 2. *x* сведения<br /><br /> type|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|All|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|Динамические, управляемые набором ключей, статические|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|Динамические, управляемые набором ключей, статические|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|All|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|Динамические, управляемые набором ключей, статические|SQL_POS_OPERATIONS|
