---
title: Уровень изоляции транзакций курсора | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fef68bfdb62527f7b631b8d7433e095eba4d1c88
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63207150"
---
# <a name="cursor-transaction-isolation-level"></a>Уровень изоляции транзакций курсора
  Режим полной блокировки курсоров основывается на взаимодействии между атрибутами параллелизма и уровнем изоляции транзакций, установленным клиентом. Клиенты ODBC устанавливают уровень изоляции транзакции с помощью [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION или атрибутов SQL_COPT_SS_TXN_ISOLATION. Режим блокировки специфической среды курсора определяется комбинацией режимов блокировки параллелизма и параметров уровня изоляции транзакции.  
  
 Драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента поддерживает следующие уровни изоляции транзакций курсора:  
  
-   Зафиксированная операция чтения (SQL_TXN_READ_COMMITTED)  
  
-   Незафиксированная операция чтения (SQL_TXN_READ_COMMITTED)  
  
-   Операция чтения с возможностью повторения (SQL_TXN_REPEATABLE_READ)  
  
-   Сериализуемый (SQL_TXN_SERIALIZABLE)  
  
-   Моментальный снимок (SQL_TXN_SS_SNAPSHOT)  
  
 Обратите внимание, что API ODBC указывает дополнительные уровни изоляции транзакций, но они не поддерживаются [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвером ODBC для собственного клиента.  
  
## <a name="see-also"></a>См. также  
 [Свойства курсора](cursor-properties.md)  
  
  
