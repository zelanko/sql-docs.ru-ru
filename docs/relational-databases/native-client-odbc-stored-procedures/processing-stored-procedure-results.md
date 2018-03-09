---
title: "Обработка результатов хранимой процедуры | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e55e6884737d20dd02a496f37d8e8cf71cf1597b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="processing-stored-procedure-results"></a>Обработка результатов хранимой процедуры
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Хранимые процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используют для возвращения данных следующие четыре механизма.  
  
-   Каждая инструкция SELECT в хранимой процедуре формирует результирующий набор.  
  
-   Процедура может возвращать данные через выходные параметры.  
  
-   Выходной параметр курсора может передать обратно серверный курсор [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Процедура может иметь целочисленный код возврата.  
  
 Приложения должны обрабатывать все эти выходы хранимых процедур. Инструкции CALL или EXECUTE должны включать маркеры параметров для кода возврата и выходных параметров. Используйте [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) для их привязки в качестве выходных параметров и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента будет передавать выходные значения привязанным переменным. Выходные параметры и коды возврата являются последними элементами, возвращаемыми клиенту по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; они не возвращаются приложению, пока [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) не вернет значение SQL_NO_DATA.  
  
 ODBC не поддерживает привязку параметров курсора [!INCLUDE[tsql](../../includes/tsql-md.md)]. Поскольку все выходные параметры должны быть связаны до выполнения процедуры, приложение ODBC не может вызывать хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)], содержащие выходной параметр курсора.  
  
## <a name="see-also"></a>См. также  
 [Выполнение хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
