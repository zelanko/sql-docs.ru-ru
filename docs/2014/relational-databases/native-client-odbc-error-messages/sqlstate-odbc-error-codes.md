---
title: SQLSTATE (коды ошибок ODBC) | Документы Microsoft
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
- SQL Server Native Client ODBC driver, errors
- ODBC error handling, cause information
- messages [ODBC], cause information
- SQLSTATEs
- errors [ODBC], cause information
ms.assetid: 84cce528-edb0-473f-a85f-3eb87fbe2cf3
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 16eb32feae2495fcd325fb09d53be2861ee84a4d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101051"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (коды ошибок ODBC)
  Код SQLSTATE предоставляет подробные сведения о причине предупреждения или ошибки. Для ошибок, возникающих в данных источника выявляются и возвращаются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента сопоставляет возвращенный собственный номер ошибки с соответствующим кодом SQLSTATE. Если номер собственной ошибки отсутствует код ошибки ODBC для сопоставления, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента возвращает сообщение SQLSTATE 42000 («синтаксическая ошибка или нарушение доступа»). Для ошибки, обнаруженные с помощью драйвера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента создает соответствующий код SQLSTATE.  
  
 Дополнительные сведения о кодах ошибок состояния см. в следующих разделах.  
  
-   [Приложение А. Коды ошибок ODBC](http://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [Сопоставления SQLSTATE](http://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>См. также  
 [Обработка ошибок и сообщений](handling-errors-and-messages.md)  
  
  