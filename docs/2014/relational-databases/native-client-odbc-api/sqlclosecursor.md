---
title: SQLCloseCursor | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLCloseCursor function
ms.assetid: e7134d65-5c1c-4ae2-b119-d9b4b9a42483
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26b00c4781624bf653ad9a8200a219951dc793c7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097164"
---
# <a name="sqlclosecursor"></a>SQLCloseCursor
  **SQLCloseCursor** заменяет [SQLFreeStmt](sqlfreestmt.md) с *параметр* значение SQL_CLOSE. При получении **SQLCloseCursor**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента отбрасывает строки ожидающих результирующих наборов. Обратите внимание, что содержащиеся в инструкции привязки параметров и столбцов (если они существуют) **SQLCloseCursor**оставляет без изменений.  
  
## <a name="see-also"></a>См. также  
 [SQLCloseCursor](http://go.microsoft.com/fwlink/?LinkId=59331)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
