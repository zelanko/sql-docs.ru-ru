---
title: Дата и время усовершенствования (ODBC) | Документы Microsoft
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
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 19c4e63fc9e101379af2ac7b6bc859daa783ae6f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194695"
---
# <a name="date-and-time-improvements-odbc"></a>Дата и время усовершенствования (ODBC)
  В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] добавлены новые типы данных даты и времени. В этом разделе описывается, каким образом эти новые типы доступны в виде расширений в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Общие сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддержка собственного клиента новые типы даты и времени типов данных, в разделе [даты и времени усовершенствования](../native-client/features/date-and-time-improvements.md). Пример, демонстрирующий поддержку ODBC даты и времени см. в разделе [использование данных даты и времени типы](../native-client-odbc-how-to/use-date-and-time-types.md).  
  
 Дополнительные общие сведения о типах данных даты и времени см. в разделе [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Поддержка типов данных для улучшений функций даты и времени ODBC](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 Содержит сведения о типах ODBC, которые поддерживают типы данных даты-времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Метаданные &#40;ODBC&#41;](../../database-engine/dev-guide/metadata-odbc.md)  
 Описывает сведения, возвращенные в полях дескрипторов параметра реализации (IPD) и строки реализации (IRD), а также метаданные столбца, возвращенные `SQLColumns` и `SQLProcedureColumns`. Также описывает метаданные типов данных, возвращенные `SQLGetTypeInfo`.  
  
 [Преобразование типов данных DateTime &#40;ODBC&#41;](datetime-data-type-conversions-odbc.md)  
 Описывает, как выполнять преобразование между значениями типа datetime и datetimeoffset.  
  
 [Поддержка sql_variant для типов даты и времени](sql-variant-support-for-date-and-time-types.md)  
 Описывает функцию SQL_VARIANT, поддерживающую улучшенные возможности типов данных даты-времени.  
  
 [Массовое копирование изменения для типы улучшенные даты и времени &#40;OLE DB и ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Описываются новые возможности даты-времени для поддержки операций массового копирования.  
  
 [Поведение с предыдущими версиями SQL Server типа улучшенные даты и времени &#40;ODBC&#41;](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 Описывает ожидаемое поведение при соединении клиентского приложения, использующего улучшенные возможности типов данных даты-времени со старой версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и при отправке клиентом, скомпилированным с помощью старой версии собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], команд на сервер, который поддерживает улучшенные возможности по работе с данными в формате даты-времени.  
  
 [Поддержка API-интерфейса ODBC для улучшенных функций даты и времени](odbc-api-support-for-enhanced-date-and-time-features.md)  
 Перечисляет функции ODBC, поддерживающие улучшенные возможности даты и времени.  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
