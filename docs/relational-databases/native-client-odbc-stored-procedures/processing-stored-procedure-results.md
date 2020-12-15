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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e1e01b61f3eb19b06b9f61653fe839818e52702d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97437545"
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
  
## <a name="see-also"></a>См. также:  
 [Выполнение хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
