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
ms.openlocfilehash: da7d6541f7bf31920519cc7462bdfd24a5f6dc0d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63067695"
---
# <a name="sqlclosecursor"></a>SQLCloseCursor
  **SQLCloseCursor** заменяет [SQLFreeStmt](sqlfreestmt.md) значением *параметра* SQL_CLOSE. По получении функции **SQLCloseCursor**драйвер собственного клиента ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отбрасывает строки ожидающих результирующих наборов. Обратите внимание, что содержащиеся в инструкции привязки параметров и столбцов (если они существуют) **SQLCloseCursor**оставляет без изменений.  
  
## <a name="see-also"></a>См. также  
 [SQLCloseCursor](https://go.microsoft.com/fwlink/?LinkId=59331)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
