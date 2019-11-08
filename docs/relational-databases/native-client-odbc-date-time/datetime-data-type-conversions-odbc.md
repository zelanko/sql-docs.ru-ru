---
title: Преобразования типов данных DateTime (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC]
- bindings [ODBC]
- ODBC, bindings and conversions
ms.assetid: 66b9d282-c88d-40e5-93c2-fd5499a74458
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8c5d601f53492b72efbcf730200fbd431f2649b1
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73783913"
---
# <a name="datetime-data-type-conversions-odbc"></a>Преобразования типа данных datetime (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Следующие привязки либо уже определены в ODBC, либо являются согласованными с расширением ODBC. Преобразования, поддерживаемые каждым поставщиком, определяются сообществом, обслуживаемым поставщиком; в результате — часто возникают несоответствия между поставщиками. Значения в квадратных скобках необязательны.  
  
-   Формат строк типа datetime — «гггг-мм-дд[ чч:мм:сс[.9999999][ плюс/минус чч:мм]]».  
  
-   Формат строк типа time — «чч:мм:сс[.9999999]».  
  
-   Формат строк типа date — «гггг-мм-дд».  
  
 Преобразования из строк обеспечивают гибкость в отношении пробелов и ширины полей. Дополнительные сведения см. в подразделе «форматы данных: строки и литералы» статьи [Поддержка типов данных для улучшений даты и времени ODBC](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md).  
  
 Далее приведены общие правила преобразования.  
  
-   Если время отсутствует, но получатель способен его хранить, оно устанавливается в нулевое значение.  
  
-   Если дата отсутствует, но получатель может ее хранить, используется текущая дата.  
  
-   Если в типе данных, используемых клиентом, отсутствует часовой пояс, но сервер может его хранить, дата сохраняется в часовом поясе клиента. Обратите внимание на отличие от поведения сервера.  
  
-   Если в типе сервера отсутствует часовой пояс, а в типе клиента он есть, то перед сохранением на сервере время преобразуется в формат UTC.  
  
-   Если время присутствует, но получатель не может его хранить, то компонент времени не обрабатывается.  
  
-   Если дата присутствует, но получатель не может ее хранить, то компонент даты не обрабатывается.  
  
-   Если при преобразовании из C в SQL возникает усечение секунд или долей секунд, то создается запись диагностики с кодом SQLSTATE 22008 и сообщением «Переполнение поля Datetime».  
  
-   Если при преобразовании из SQL в C возникает усечение секунд или долей секунд, то создается запись диагностики с кодом SQLSTATE 01S07 и сообщением «Частичное усечение».  
  
## <a name="in-this-section"></a>В этом разделе  
 [Преобразования из C в SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)  
 Перечисляет проблемы, которые необходимо решить при преобразовании типов C в типы даты-времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Преобразования из SQL в C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)  
 Перечисляет проблемы, которые необходимо решить при преобразовании типов даты и времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в типы C.  
  
## <a name="see-also"></a>См. также раздел  
 [Улучшения &#40;даты и времени ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
