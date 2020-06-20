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
author: rothja
ms.author: jroth
ms.openlocfilehash: 45e72165eef621dc377b02ed3d2e7e1e3cf7ab8e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021867"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
  Для выполненных инструкций драйверу ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нет необходимости обращаться к серверу для сообщения о числе столбцов результирующего набора. В этом случае не `SQLNumResultCols` вызывает обмен данными с сервером. Как и в [SQLDescribeCol](sqldescribecol.md) и [SQLColAttribute](sqlcolattribute.md), вызов `SQLNumResultCols` на подготовленных, но не выполненных инструкциях создает обмен данными между серверами.  
  
 Если инструкция или пакет инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] возвращает несколько результирующих наборов строк, можно изменить число столбцов одного результирующего набора на число столбцов в другом наборе. `SQLNumResultCols`должен вызываться для каждого набора. При изменении числа столбцов приложение должно осуществить повторную привязку значений данных перед выборкой результатов строк. Дополнительные сведения об обработке запросов, возвращающих несколько результирующих наборов, см. в разделе [SQLMoreResults](sqlmoreresults.md).  
  
 Улучшения в ядре СУБД, начиная с, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] позволяют SQLNumResultCols получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значений, возвращаемых функцией SQLNumResultCols в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Обнаружение метаданных](../native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLNumResultCols](https://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
