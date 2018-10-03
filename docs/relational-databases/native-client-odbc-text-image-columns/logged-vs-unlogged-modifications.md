---
title: Изменения с ведением журнала Незафиксированных изменений | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 15f53b8d70f912c799cc1a6eb21b36d662d31a2d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846822"
---
# <a name="logged-vs-unlogged-modifications"></a>Изменения с ведением журнала и без ведения журнала
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Приложение может запрашивать, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не журнала **текст**, **ntext**, и **изображение** изменения. Однако этот режим следует использовать очень осторожно. Он должен использоваться только в ситуациях, где **текст**, **ntext**, или **изображения** данные не являются критическими и владельцы данных готовы добиваться возможность восстановления базы данных для более высокая производительность.  
  
 Ведение журнала **текст**, **ntext**, и **изображение** изменений осуществляется путем вызова функции [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) с  *Атрибут* параметру присвоить SQL_SOPT_SS_ TEXTPTR_LOGGING и *ValuePtr* присвоено SQL_TL_ON или SQL_TL_OFF.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами text и image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
