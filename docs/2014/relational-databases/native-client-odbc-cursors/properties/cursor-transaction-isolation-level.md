---
title: Уровень изоляции транзакций курсора | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 83c5195598eb28ad8bcbe219d7cda0de327973cc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101548"
---
# <a name="cursor-transaction-isolation-level"></a>Уровень изоляции транзакций курсора
  Режим полной блокировки курсоров основывается на взаимодействии между атрибутами параллелизма и уровнем изоляции транзакций, установленным клиентом. Клиенты ODBC устанавливают транзакции уровень изоляции с использованием [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) атрибутов SQL_ATTR_TXN_ISOLATION или SQL_COPT_SS_TXN_ISOLATION. Режим блокировки специфической среды курсора определяется комбинацией режимов блокировки параллелизма и параметров уровня изоляции транзакции.  
  
 Поддерживаются следующие уровни изоляции транзакций курсора [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента:  
  
-   Зафиксированная операция чтения (SQL_TXN_READ_COMMITTED)  
  
-   Незафиксированная операция чтения (SQL_TXN_READ_COMMITTED)  
  
-   Операция чтения с возможностью повторения (SQL_TXN_REPEATABLE_READ)  
  
-   Сериализуемый (SQL_TXN_SERIALIZABLE)  
  
-   Моментальный снимок (SQL_TXN_SS_SNAPSHOT)  
  
 Обратите внимание, что ODBC API определяет дополнительные уровни изоляции транзакций, но они не поддерживаются в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента.  
  
## <a name="see-also"></a>См. также  
 [Свойства курсора](cursor-properties.md)  
  
  