---
title: СЗЛБиндкол Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 69457daccbc7868e58f91c71a48b4b25f15f5318
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302735"
---
# <a name="sqlbindcol"></a>SQLBindCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Как правило, учитывайте последствия использования **S'LBindCol** для преобразования данных. Преобразования привязки являются клиентскими процессами, поэтому, например, получение значения с плавающей запятой, связанного с символьным столбцом, вынуждает драйвер выполнить локальное преобразование «плавающая запятая в символ» при выборке строки. Функция [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT может использоваться для размещения затрат преобразования данных на сервере.  
  
 Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может возвращать несколько результирующих наборов для одной инструкции. Каждый результирующий набор должен быть привязан отдельно. Для получения более подробной информации о привязке к нескольким наборам результатов, [см.](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)  
  
 Разработчик может связывать столбцы с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]конкретными типами данных C, используя значение *TargetType* **SQL_C_BINARY.** Столбцы, привязанные к типам, зависящим от служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не могут быть перенесены. Определенные типы данных ODBC языка C, зависящие от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], совпадают с определениями типов для DB-Library, и разработчики приложений переноса DB-Library могут воспользоваться этой возможностью.  
  
 Усечение данных является [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] дорогостоящим процессом для драйвера NATIVE Client ODBC. Усечения можно избежать с помощью гарантии того, что все буферы связанных данных достаточно широки для возвращения данных. Для символьных данных ширина должна включать пространство для признака конца строки при использовании поведения драйвера по умолчанию для завершения строки. Например, привязка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбца **char(5)** к массиву из пяти символов приводит к усечению для каждого извлеченного значения. Привязка одинакового столбца к массиву из шести символов позволит избежать усечения путем предоставления элемента символа для хранения признака конца NULL. [СЗЛГетДата](../../relational-databases/native-client-odbc-api/sqlgetdata.md) может быть использована для эффективного получения длинных символов и двоичных данных без усечения.  
  
 Для больших типов данных значений, если поставляемый пользователем буфер недостаточно велик, чтобы удерживать всю ценность столбца, **SQL_SUCCESS_WITH_INFO** возвращается и "строка данных; право усечение" предупреждение выдается. **Аргумент StrLen_or_IndPtr** будет содержать количество chars/байтов, хранящихся в буфере.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLBindCol улучшенных возможностей работы с данными в формате даты-времени  
 Значения столбца результатов типов даты/времени преобразуются, как описано в [преобразованиях от S'L к C.](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md) Обратите внимание, что для получения временных и дневных столбцов в качестве соответствующих структур **(SQL_SS_TIME2_STRUCT** и **SQL_SS_TIMESTAMPOFFSET_STRUCT),** *TargetType* должен быть указан как **SQL_C_DEFAULT** или **SQL_C_BINARY.**  
  
 Для получения дополнительной информации см [&#41;&#40;. ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>Поддержка функцией SQLBindCol определяемых пользователем типов больших данных CLR  
 **S'LBindCol** поддерживает большие типы, определяемые пользователями CLR (UDT). Для получения дополнительной информации смотрите [большие типы, определяемые пользователями CLR, &#40;&#41;ODBC. ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [Функция S'LBindCol](https://go.microsoft.com/fwlink/?LinkId=59327)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
