---
title: Тип курсора и параллелизма сочетания | Документы Microsoft
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
- ODBC driver for Oracle [ODBC], concurrency options
- cursors [ODBC], ODBC driver for Oracle
- concurrency options [ODBC]
- ODBC driver for Oracle [ODBC], cursor options
ms.assetid: db63d610-f86f-4029-9d66-fed616c8a818
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d9b963135f30169bdf6e145e4719115b2d805fa2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="cursor-type-and-concurrency-combinations"></a>Тип курсора и параллелизма сочетания
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Типы курсоров управлять функциональность курсора, направляемое пользователю. Параметры параллелизма контролировать возможность обновления и режим блокировки результирующего набора.  
  
|Тип курсора|Параллелизм (допустимые значения)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1] </sup> Разделе [ограничения использования управляемые набором ключей курсоры](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md).  
  
 <sup>[2] </sup> SQL_CONCUR_LOCK поддерживается только в том случае, если параметр SQL_AUTOCOMMIT соединений задано равным SQL_AUTOCOMMIT_OFF.  
  
## <a name="see-also"></a>См. также  
 [Параметры подключения](../../odbc/microsoft/connect-options.md)
