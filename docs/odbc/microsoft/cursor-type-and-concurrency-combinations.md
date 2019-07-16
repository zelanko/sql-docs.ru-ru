---
title: Тип курсора и параллелизма сочетания | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], concurrency options
- cursors [ODBC], ODBC driver for Oracle
- concurrency options [ODBC]
- ODBC driver for Oracle [ODBC], cursor options
ms.assetid: db63d610-f86f-4029-9d66-fed616c8a818
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2a29fc2d02cb46dda44fa22b2344cbab475443f2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096535"
---
# <a name="cursor-type-and-concurrency-combinations"></a>Сочетания типов курсора и параллелизма
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Типы курсоров управления функциональность курсора, предоставленному пользователю. Параметры параллелизма контролировать возможность обновления и режим блокировки результирующего набора.  
  
|Тип курсора|Параллелизм (допустимые значения)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1] </sup> См. в разделе [ограничения на использование курсоры](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md).  
  
 <sup>[2] </sup> SQL_CONCUR_LOCK поддерживается только в том случае, если параметр подключения SQL_AUTOCOMMIT имеет значение к SQL_AUTOCOMMIT_OFF.  
  
## <a name="see-also"></a>См. также  
 [Параметры подключения](../../odbc/microsoft/connect-options.md)
