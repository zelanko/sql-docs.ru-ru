---
title: СЗЛПутДата (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e063d1053d8a6e5e10a1234d33893adf27fbc3ad
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302369"
---
# <a name="sqlputdata"></a>SQLPutData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Следующие ограничения применяются при использовании S'LPutData для отправки более [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 65 535 байт данных (для версии 4.21a) или 400 кБ данных (для версии sL Server 6.0 и более позднего) для SQL_LONGVARCHAR **(текст),** SQL_WLONGVARCHAR **(ntext)** или SQL_LONGVARBINARY **(изображение)** колонка:  
  
-   Ссылка параметр может быть *insert_value* в выписке INSERT.  
  
-   Ссылка параметр может быть *выражением* в предложении SET заявления UPDATE.  
  
 Отмена последовательности вызовов S'LPutData, которые предоставляют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данные в блоках на запущенном сервере, приводит к частичному обновлению значения столбца при использовании версии 6.5 или раньше. **Текст,** **ntext**или колонка **изображений,** на которую ссылались при вызове S'LCancel, устанавливается на промежуточное значение заполнителя.  
  
> [!NOTE]  
>  Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает соединение с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранней.  
  
## <a name="diagnostics"></a>Диагностика  
 Существует один [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] родной клиент конкретных S'LSTATE для S'LPutData:  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|22026|Строковые данные, несовпадение длины|Если длина данных в байтах, которые будут отправлены, была указана приложением, например, с SQL_LEN_DATA_AT_EXEC *(n),* где *n* больше, чем 0, общее количество байтов, данных приложением через S'LPutData, должно соответствовать указанной длине.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>Функция SQLPutData и параметры, возвращающие табличные значения  
 При использовании связывания переменных рядов с параметрами, оцениваемыми таблицей, приложение использует при этом связывание переменных строк. Параметр *StrLen_Or_Ind* указывает на то, что он готов для драйвера собирать данные для следующего ряда или строк и ценных данных параметров, ценных таблицей, или что больше не доступны строки:  
  
-   Значение, большее 0, указывает на доступность следующего набора значений строки.  
  
-   Значение 0 указывает, что строк для отправки больше нет.  
  
-   Значение меньше 0 является ошибочным и приводит к внесению в журнал диагностической записи со значением SQLState, равным HY090, и сообщением «Недопустимая длина строки или буфера».  
  
 Параметр *DataPtr* игнорируется, но должен быть установлен на значение, не относященное. Для получения дополнительной информации смотрите раздел о привязке строки переменной TVP в [связывании и передаче данных параметров и значений столбца.](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)  
  
 Если *StrLen_Or_Ind* имеет какое-либо значение, кроме SQL_DEFAULT_PARAM или числа между 0 и SQL_PARAMSET_SIZE (т.е. параметра *ColumnSize* S'LBindParameter), это ошибка. Эта ошибка приводит к возвращению SQL_ERROR: S'LSTATE-HY090, "Недействий строки или длины буфера".  
  
 Для получения дополнительной информации о параметрах, ценных на стол, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>Поддержка функции SQLPutData для улучшенных функций даты-времени  
 Значения параметров типов дат/времени преобразуются, как описано в [преобразованиях от C до S'L.](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)  
  
 Для получения дополнительной информации см [&#41;&#40;. ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>Поддержка функции SQLPutData для больших определяемых пользователем типов данных CLR  
 **S'LPutData** поддерживает большие типы, определяемые пользователями CLR (UDT). Для получения дополнительной информации смотрите [большие типы, определяемые пользователями CLR, &#40;&#41;ODBC. ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [Функция S'LPutData](https://go.microsoft.com/fwlink/?LinkId=59365)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
