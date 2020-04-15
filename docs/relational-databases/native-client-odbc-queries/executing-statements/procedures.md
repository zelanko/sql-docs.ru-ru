---
title: Процедуры Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 59d971f4d835470924874b0a08a648d36d98c0f9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297919"
---
# <a name="procedures"></a>Процедуры
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Хранимая процедура представляет собой заранее скомпилированный исполняемый объект, содержащий одну или несколько инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Хранимые процедуры могут иметь входные и выходные параметры, а также возвращать целочисленный код возврата. Приложение может перечислять существующие хранимые процедуры с помощью функций для работы с каталогами.  
  
 Приложения ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должны вызывать хранимые процедуры только методом прямого выполнения. При подключении [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более ранним версиям драйвера Native Client ODBC реализует [функцию S'LPrepare,](https://go.microsoft.com/fwlink/?LinkId=59360) создавая временную процедуру хранения, которая затем вызывается на **S'LExecute.** Он добавляет накладные расходы, чтобы **спомощьей создать** временную процедуру хранения, которая вызывает только целевую процедуру хранения по сравнению с непосредственной выполнением целевой процедуры хранения. Даже если соединение с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] уже существует, подготовка вызова требует лишнего цикла приема-передачи данных по сети и построения плана выполнения, который только вызывает план выполнения хранимой процедуры.  
  
 При выполнении хранимой процедуры приложения ODBC должны использовать конструкцию ODBC CALL. Драйвер оптимизирован так, что при обработке конструкции ODBC CALL использует механизм удаленного вызова процедур (RPC). Это эффективнее, чем механизм, используемый для посылки инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE на сервер.  
  
 Для получения дополнительной информации [см.](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
## <a name="see-also"></a>См. также:  
 [Выполнение заявлений &#40;&#41;ODBC](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
