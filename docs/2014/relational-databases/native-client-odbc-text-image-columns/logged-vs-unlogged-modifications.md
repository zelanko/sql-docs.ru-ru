---
title: Журнал vs. Незафиксированных изменений | Документы Microsoft
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
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d5c73288c57a834008f4d09ad098ad1b41183e76
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195155"
---
# <a name="logged-vs-unlogged-modifications"></a>Журнал vs. Незафиксированных изменений
  Приложение может запрашивать, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не журнала **текст**, **ntext**, и **изображения** изменения. Однако этот режим следует использовать очень осторожно. Он должен использоваться только для тех случаев, где **текст**, **ntext**, или **изображения** данные не являются критическими и владельцы данных готовы пожертвовать возможностью для восстановления данных на более высокая производительность.  
  
 Ведение журнала **текст**, **ntext**, и **изображения** изменений осуществляется путем вызова функции [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) с  *Атрибут* равным SQL_SOPT_SS_ TEXTPTR_LOGGING и *ValuePtr* SQL_TL_ON или SQL_TL_OFF.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами text и image](managing-text-and-image-columns.md)  
  
  