---
title: SQLNumResultCols | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 679888376c7ea02570e877ed5eac0e9638af48e3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220364"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
  Для выполненных инструкций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента нет необходимости обращаться к серверу для сообщения число столбцов в результирующем наборе. В этом случае `SQLNumResultCols` не вызывает обращения к серверу. Как и [SQLDescribeCol](sqldescribecol.md) и [SQLColAttribute](sqlcolattribute.md), вызов `SQLNumResultCols` для подготовленных, но не выполненных инструкций приводит к обращению к серверу.  
  
 Если инструкция или пакет инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] возвращает несколько результирующих наборов строк, можно изменить число столбцов одного результирующего набора на число столбцов в другом наборе. `SQLNumResultCols` должен вызываться для каждого набора. При изменении числа столбцов приложение должно осуществить повторную привязку значений данных перед выборкой результатов строк. Дополнительные сведения об обработке несколько результирующих наборов возвращает, см. в разделе [SQLMoreResults](sqlmoreresults.md).  
  
 Улучшения в ядро базы данных, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] разрешить SQLNumResultCols получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значения, возвращаемые методом SQLNumResultCols в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Обнаружение метаданных](../native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>См. также  
 [SQLNumResultCols, функция](http://go.microsoft.com/fwlink/?LinkId=59359)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
