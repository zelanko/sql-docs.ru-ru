---
title: Процедуры | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 260e9a6ab31e2376132c107c19bb30b8aeee8b1c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191951"
---
# <a name="procedures"></a>Процедуры
  Хранимая процедура представляет собой заранее скомпилированный исполняемый объект, содержащий одну или несколько инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Хранимые процедуры могут иметь входные и выходные параметры, а также возвращать целочисленный код возврата. Приложение может перечислять существующие хранимые процедуры с помощью функций для работы с каталогами.  
  
 Приложения ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должны вызывать хранимые процедуры только методом прямого выполнения. При подключении к более ранним версиям [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] реализует драйвер ODBC для собственного клиента [SQLPrepare, функция](http://go.microsoft.com/fwlink/?LinkId=59360) путем создания временной хранимой процедуры, которая затем вызывается на **SQLExecute** . Он добавляет нагрузку по **SQLPrepare** создания временной хранимой процедуры, который только вызывает целевую хранимую процедуру или непосредственно исполнением целевой хранимой процедуры. Даже если соединение с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] уже существует, подготовка вызова требует лишнего цикла приема-передачи данных по сети и построения плана выполнения, который только вызывает план выполнения хранимой процедуры.  
  
 При выполнении хранимой процедуры приложения ODBC должны использовать конструкцию ODBC CALL. Драйвер оптимизирован так, что при обработке конструкции ODBC CALL использует механизм удаленного вызова процедур (RPC). Это эффективнее, чем механизм, используемый для посылки инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE на сервер.  
  
 Дополнительные сведения см. в разделе [выполнение хранимых процедур](../../native-client-odbc-stored-procedures/running-stored-procedures.md).  
  
## <a name="see-also"></a>См. также  
 [Выполнение инструкций &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  