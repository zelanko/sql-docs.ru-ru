---
title: С ведением журнала. Незафиксированных изменений | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34064aaa2e96a7d610f8709c1f5750bddd62b766
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420305"
---
# <a name="logged-vs-unlogged-modifications"></a>С ведением журнала. Без ведения журнала
  Приложение может запрашивать, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не журнала **текст**, **ntext**, и **изображение** изменения. Однако этот режим следует использовать очень осторожно. Он должен использоваться только в ситуациях, где **текст**, **ntext**, или **изображения** данные не являются критическими и владельцы данных готовы добиваться возможность восстановления базы данных для более высокая производительность.  
  
 Ведение журнала **текст**, **ntext**, и **изображение** изменений осуществляется путем вызова функции [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) с  *Атрибут* параметру присвоить SQL_SOPT_SS_ TEXTPTR_LOGGING и *ValuePtr* присвоено SQL_TL_ON или SQL_TL_OFF.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами text и image](managing-text-and-image-columns.md)  
  
  
