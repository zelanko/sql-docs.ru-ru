---
title: Сочетания типа курсора и параллелизма | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6397b5d675546bf41102f037b68c0022bec74df
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280774"
---
# <a name="cursor-type-and-concurrency-combinations"></a>Сочетания типов курсора и параллелизма
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Типы курсоров управляют функциональными возможностями курсора, предоставленного пользователю. Параметры параллелизма управляют поведением обновления и блокировки результирующего набора.  
  
|Тип курсора|Параллелизм (допустимые значения)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1]</sup> см. [ограничения при использовании курсоров, управляемых набором ключей](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md).  
  
 <sup>[2]</sup> SQL_CONCUR_LOCK поддерживается, только если для параметра подключения SQL_AUTOCOMMIT установлено значение SQL_AUTOCOMMIT_OFF.  
  
## <a name="see-also"></a>См. также:  
 [Параметры подключения](../../odbc/microsoft/connect-options.md)
