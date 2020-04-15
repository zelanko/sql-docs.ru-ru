---
title: Зарегистрированные против незарегистрированных модификаций (ru) Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dc7fb913bef4083b045a0c1c010bdedbc43135c5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297702"
---
# <a name="logged-vs-unlogged-modifications"></a>Изменения с ведением журнала и без ведения журнала
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Приложение может запросить, чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] водитель Native Client ODBC не регистрировать **текст,** **ntext**и изменения **изображения.** Однако этот режим следует использовать очень осторожно. Он должен использоваться только в тех ситуациях, когда **текст,** **ntext**или данные **изображения** не являются критическими и владельцы данных готовы торговать возможностью восстановления данных для более высокой производительности.  
  
 Регистрация **текста,** **ntext**и изменения **изображения** контролируется путем вызова [S'LSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) с параметром *атрибута,* установленным для SQL_SOPT_SS_ TEXTPTR_LOGGING и *ValuePtr,* установленных либо SQL_TL_ON, либо SQL_TL_OFF.  
  
## <a name="see-also"></a>См. также:  
 [Управление столбцами text и image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
