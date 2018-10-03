---
title: Обработка результатов (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], about result sets
- SQLRowCount function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- COMPUTE clause
- result sets [ODBC]
- COMPUTE BY clause
ms.assetid: 61a8db19-6571-47dd-84e8-fcc97cb60b45
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 80700d67ddf4a6976e9212370cb6edf3f72c6e6c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764502"
---
# <a name="processing-results-odbc"></a>Обработка результатов (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  После передачи приложением инструкции SQL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает все данные результата в виде одного или нескольких результирующих наборов. Результирующий набор — это набор строк и столбцов, соответствующих критерию запроса. Инструкции SELECT, функции работы с каталогами и некоторые хранимые процедуры создают результирующий набор, доступный для приложения в табличной форме. Если выполняемая инструкция SQL является хранимой процедурой, пакетом из нескольких команд либо инструкцией SELECT, содержащей ключевые слова, то необходимо выполнять обработку нескольких результирующих наборов.  
  
 Функции ODBC для работы с каталогами также могут получать данные. Например [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md) извлекает данные о столбцах в источнике данных. Эти результирующие наборы могут содержать нуль или более строк.  
  
 Некоторые инструкции SQL, например GRANT или REVOKE, не возвращают результирующие наборы. Для этих инструкций, код возврата **SQLExecute** или **SQLExecDirect** обычно является указывать только инструкция выполнена успешно.  
  
 Каждая из инструкций INSERT, UPDATE и DELETE возвращает результирующий набор, содержащий только количество строк, затронутых изменением. Это число становится доступен при вызове [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md). ODBC 3. *x* приложений должен либо вызвать метод **SQLRowCount** для получения результирующего набора или [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) отмените его. Когда приложение выполняет пакет или хранимую процедуру, содержащую несколько инструкций INSERT, UPDATE или DELETE, результирующий набор каждой инструкции изменения должны быть обработаны с помощью **SQLRowCount** или отменено с помощью **SQLMoreResults**. Эти счетчики можно сбросить, включив в пакет или хранимую процедуру инструкцию SET NOCOUNT ON.  
  
 Transact-SQL включает инструкцию SET NOCOUNT. Если параметр NOCOUNT включен, SQL Server не возвращает количество строк, затронутых инструкцией и **SQLRowCount** возвращает 0. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Версии драйвера ODBC для собственного клиента предоставляет зависящий от драйвера [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) параметр SQL_SOPT_SS_NOCOUNT_STATUS, сообщить о того, является ли параметр NOCOUNT или отключить. В любое время **SQLRowCount** возвращает 0, то приложение должно проверить SQL_SOPT_SS_NOCOUNT_STATUS. Если возвращается sql_nc_on, значение 0 от **SQLRowCount** определяет только то, что SQL Server не вернул количество строк. Если возвращается SQL_NC_OFF, это означает, что NOCOUNT отключен и значение 0 от **SQLRowCount** указывает, что инструкция не обработала все строки. Приложения не должны отображать значение **SQLRowCount** когда SQL_SOPT_SS_NOCOUNT_STATUS установлен в значение SQL_NC_OFF. Большие пакеты или хранимые процедуры могут содержать несколько инструкций SET NOCOUNT, следовательно, программисты не должны предполагать, что параметр SQL_SOPT_SS_NOCOUNT_STATUS останется неизменным. Параметр необходимо проверять каждый раз **SQLRowCount** возвращает 0.  
  
 Несколько других инструкций Transact-SQL возвращают данные в сообщениях, а не в результирующих наборах. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента получает эти сообщения, он возвращает значение SQL_SUCCESS_WITH_INFO для уведомления приложения о том, что информационные сообщения доступны. Затем приложение может вызвать **SQLGetDiagRec** для получения этих сообщений. Инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], работающие таким способом, перечислены ниже.  
  
-   DBCC  
  
-   SET SHOWPLAN (доступна в ранних версиях SQL Server)  
  
-   SET STATISTICS  
  
-   PRINT  
  
-   RAISERROR  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC для собственного клиента возвращает ошибку SQL_ERROR для инструкции RAISERROR с уровнем серьезности 11 и выше. При уровне серьезности RAISERROR от 19 и выше соединение отключается.  
  
 Чтобы обработать результирующие наборы инструкции SQL, приложение выполняет следующие действия.  
  
-   Определяет характеристики результирующего набора.  
  
-   Привязывает столбцы к переменным программы.  
  
-   Получает одно значение, целую строку значений, или несколько строк значений.  
  
-   Проверяет наличие результирующих наборов, и в случае их существования, начинает цикл снова для определения характеристик нового результирующего набора.  
  
 Процесс получения строк из источника данных и передачи их в приложение называется выборкой.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Определение характеристик результирующего набора &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
-   [Назначение хранилища](../../relational-databases/native-client-odbc-results/assigning-storage.md)  
  
-   [Выборка итоговых данных](../../relational-databases/native-client-odbc-results/fetching-result-data.md)  
  
-   [Сопоставление типов данных &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/mapping-data-types-odbc.md)  
  
-   [Использование типов данных](../../relational-databases/native-client-odbc-results/data-type-usage.md)  
  
-   [Автоматическое преобразование символьных данных](../../relational-databases/native-client-odbc-results/autotranslation-of-character-data.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [Результаты инструкции по обработке &#40;ODBC&#41;](http://msdn.microsoft.com/library/772d9064-c91d-4cac-8b60-fcc16bf76e10)  
  
  
