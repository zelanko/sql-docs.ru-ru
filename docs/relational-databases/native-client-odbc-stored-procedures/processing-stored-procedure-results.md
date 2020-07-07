---
title: Обработка результатов хранимой процедуры | Документация Майкрософт
description: Сведения о механизмах, SQL Server хранимые процедуры для возврата данных в приложения. Приложения должны иметь возможность обрабатывать все эти типы.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e5073665d959c35261cc0384b5a09a2e3cfd9ca5
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86004633"
---
# <a name="processing-stored-procedure-results"></a>Обработка результатов хранимой процедуры
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Хранимые процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используют для возвращения данных следующие четыре механизма.  
  
-   Каждая инструкция SELECT в хранимой процедуре формирует результирующий набор.  
  
-   Процедура может возвращать данные через выходные параметры.  
  
-   Выходной параметр курсора может передать обратно серверный курсор [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Процедура может иметь целочисленный код возврата.  
  
 Приложения должны обрабатывать все эти выходы хранимых процедур. Инструкции CALL или EXECUTE должны включать маркеры параметров для кода возврата и выходных параметров. Используйте [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) , чтобы привязать их все как выходные параметры, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента передает выходные значения в привязанные переменные. Выходные параметры и коды возврата — это последние элементы, возвращаемые клиенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . они не возвращаются в приложение, пока [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) не возвратит SQL_NO_DATA.  
  
 ODBC не поддерживает привязку параметров курсора [!INCLUDE[tsql](../../includes/tsql-md.md)]. Поскольку все выходные параметры должны быть связаны до выполнения процедуры, приложение ODBC не может вызывать хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)], содержащие выходной параметр курсора.  
  
## <a name="see-also"></a>См. также  
 [Выполнение хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
