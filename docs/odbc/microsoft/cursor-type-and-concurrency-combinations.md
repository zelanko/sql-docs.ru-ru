---
title: "Тип курсора и параллелизма сочетания | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
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
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a20223e272ce2790a8959df3d9f7ed318e700aef
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
  
## <a name="see-also"></a>См. также:  
 [Параметры подключения](../../odbc/microsoft/connect-options.md)
