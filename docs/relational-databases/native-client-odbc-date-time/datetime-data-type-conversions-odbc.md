---
title: "DateTime преобразования типа данных (ODBC) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-date-time
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC]
- bindings [ODBC]
- ODBC, bindings and conversions
ms.assetid: 66b9d282-c88d-40e5-93c2-fd5499a74458
caps.latest.revision: "19"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 065c030e38e588dbc1068ead291f0ac4f5a6a179
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="datetime-data-type-conversions-odbc"></a>Преобразования типа данных datetime (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Следующие привязки либо уже определены в ODBC, либо являются согласованными с расширением ODBC. Преобразования, поддерживаемые каждым поставщиком, определяются сообществом, обслуживаемым поставщиком; в результате — часто возникают несоответствия между поставщиками. Значения в квадратных скобках необязательны.  
  
-   Формат строк типа datetime — «гггг-мм-дд[ чч:мм:сс[.9999999][ плюс/минус чч:мм]]».  
  
-   Формат строк типа time — «чч:мм:сс[.9999999]».  
  
-   Формат строк типа date — «гггг-мм-дд».  
  
 Преобразования из строк обеспечивают гибкость в отношении пробелов и ширины полей. Дополнительные сведения см. раздел «Данных форматов: строки и литералы» [поддержка типов данных для ODBC Дата и время улучшениях](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md).  
  
 Далее приведены общие правила преобразования.  
  
-   Если время отсутствует, но получатель способен его хранить, оно устанавливается в нулевое значение.  
  
-   Если дата отсутствует, но получатель может ее хранить, используется текущая дата.  
  
-   Если в типе данных, используемых клиентом, отсутствует часовой пояс, но сервер может его хранить, дата сохраняется в часовом поясе клиента. Обратите внимание на отличие от поведения сервера.  
  
-   Если в типе сервера отсутствует часовой пояс, а в типе клиента он есть, то перед сохранением на сервере время преобразуется в формат UTC.  
  
-   Если время присутствует, но получатель не может его хранить, то компонент времени не обрабатывается.  
  
-   Если дата присутствует, но получатель не может ее хранить, то компонент даты не обрабатывается.  
  
-   Если при преобразовании из C в SQL возникает усечение секунд или долей секунд, то создается запись диагностики с кодом SQLSTATE 22008 и сообщением «Переполнение поля Datetime».  
  
-   Если при преобразовании из SQL в C возникает усечение секунд или долей секунд, то создается запись диагностики с кодом SQLSTATE 01S07 и сообщением «Частичное усечение».  
  
## <a name="in-this-section"></a>в этом разделе  
 [Преобразования из C в SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)  
 Перечисляет проблемы, которые необходимо решить при преобразовании типов C в типы даты-времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Преобразования из SQL в C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)  
 Перечисляет проблемы, которые необходимо решить при преобразовании типов даты и времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в типы C.  
  
## <a name="see-also"></a>См. также:  
 [Дата и время усовершенствования &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
