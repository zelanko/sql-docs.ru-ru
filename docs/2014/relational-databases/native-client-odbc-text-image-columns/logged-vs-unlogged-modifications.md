---
title: Изменения с ведением журнала Незафиксированных изменений | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c722d5360ad01e7e95508c2219ceb674de381286
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63195143"
---
# <a name="logged-vs-unlogged-modifications"></a>Изменения с ведением журнала и без ведения журнала
  Приложение может запрашивать, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не журнала **текст**, **ntext**, и **изображение** изменения. Однако этот режим следует использовать очень осторожно. Он должен использоваться только в ситуациях, где **текст**, **ntext**, или **изображения** данные не являются критическими и владельцы данных готовы добиваться возможность восстановления базы данных для более высокая производительность.  
  
 Ведение журнала **текст**, **ntext**, и **изображение** изменений осуществляется путем вызова функции [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) с  *Атрибут* параметру присвоить SQL_SOPT_SS_ TEXTPTR_LOGGING и *ValuePtr* присвоено SQL_TL_ON или SQL_TL_OFF.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами text и image](managing-text-and-image-columns.md)  
  
  
