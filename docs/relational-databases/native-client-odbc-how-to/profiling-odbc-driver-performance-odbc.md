---
description: Создание профилей производительности драйвера (ODBC)
title: Создание профилей производительности драйвера ODBC
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0e6d7aed-28d2-419e-be6a-f60d3729bfd0
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 09c5dff41c7865f02c508acbbf718b81cafa932a
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97469535"
---
# <a name="profiling-odbc-driver-performance-odbc"></a>Создание профилей производительности драйвера (ODBC)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Драйвер ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет два параметра для измерения производительности драйвера.  
  
 Драйвер ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может записывать статистические показатели производительности в файл. Журнал статистики — это файл с разделителями-знаками табуляции, который можно проанализировать в приложении электронных таблиц, поддерживающем файлы с разделителями-знаками табуляции, например в Microsoft Excel.  
  
 Драйвер также может регистрировать долго выполняемые запросы (запросы, на которые сервер не возвращает ответа в течение заданного времени). Эти запросы могут позднее анализироваться программистами и администраторами баз данных.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Данные производительности драйвера профиля &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data.md)  
  
-   [Запросы Long-Running журналов &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data-log-long-running-queries.md)  
  
## <a name="see-also"></a>См. также:  
 [ODBC How-to Topics](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)  
  
  
