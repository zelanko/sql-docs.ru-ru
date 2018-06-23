---
title: Обработка результатов хранимой процедуры | Документы Microsoft
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
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cfc9756a6c55e4ff894b56ec483e921a1acb6b68
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096151"
---
# <a name="processing-stored-procedure-results"></a>Обработка результатов хранимой процедуры
  Хранимые процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используют для возвращения данных следующие четыре механизма.  
  
-   Каждая инструкция SELECT в хранимой процедуре формирует результирующий набор.  
  
-   Процедура может возвращать данные через выходные параметры.  
  
-   Выходной параметр курсора может передать обратно серверный курсор [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Процедура может иметь целочисленный код возврата.  
  
 Приложения должны обрабатывать все эти выходы хранимых процедур. Инструкции CALL или EXECUTE должны включать маркеры параметров для кода возврата и выходных параметров. Используйте [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) для их привязки в качестве выходных параметров и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента будет передавать выходные значения привязанным переменным. Выходные параметры и коды возврата являются последними элементами, возвращаемыми клиенту по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; они не возвращаются приложению, пока [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) не вернет значение SQL_NO_DATA.  
  
 ODBC не поддерживает привязку параметров курсора [!INCLUDE[tsql](../../includes/tsql-md.md)]. Поскольку все выходные параметры должны быть связаны до выполнения процедуры, приложение ODBC не может вызывать хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)], содержащие выходной параметр курсора.  
  
## <a name="see-also"></a>См. также  
 [Выполнение хранимых процедур](running-stored-procedures.md)  
  
  