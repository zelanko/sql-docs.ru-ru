---
title: Результаты обработки (ODBC) Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 39dafbb865ef951356bb01c4fd8f646bf943346b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304608"
---
# <a name="processing-results-odbc"></a>Обработка результатов (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  После передачи приложением инструкции SQL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает все данные результата в виде одного или нескольких результирующих наборов. Результирующий набор — это набор строк и столбцов, соответствующих критерию запроса. Инструкции SELECT, функции работы с каталогами и некоторые хранимые процедуры создают результирующий набор, доступный для приложения в табличной форме. Если выполняемая инструкция SQL является хранимой процедурой, пакетом из нескольких команд либо инструкцией SELECT, содержащей ключевые слова, то необходимо выполнять обработку нескольких результирующих наборов.  
  
 Функции ODBC для работы с каталогами также могут получать данные. Например, [S'LColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md) получает данные о столбцах в источнике данных. Эти результирующие наборы могут содержать нуль или более строк.  
  
 Некоторые инструкции SQL, например GRANT или REVOKE, не возвращают результирующие наборы. Для этих утверждений код возврата от **S'LExecute** или **S'LExecDirect,** как правило, является единственным признаком успеха оператора.  
  
 Каждая из инструкций INSERT, UPDATE и DELETE возвращает результирующий набор, содержащий только количество строк, затронутых изменением. Этот подсчет становится доступным, когда приложение вызывает [S'LRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md). ODBC 3. *приложения x* должны либо позвонить в **S'LRowCount,** чтобы получить набор результатов, [либо](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) отменить его. При выполнении приложения пакетная или сохраненная процедура, содержащая несколько инструкций INSERT, UPDATE или DELETE, результат, установленный из каждой выписки о модификации, должен быть обработан с помощью **S'LRowCount** или отменен с помощью **S'LMoreResults.** Эти счетчики можно сбросить, включив в пакет или хранимую процедуру инструкцию SET NOCOUNT ON.  
  
 Transact-SQL включает инструкцию SET NOCOUNT. При установке опции NOCOUNT сервер S'L Server не возвращает количество строк, затронутых выпиской, и **S'LRowCount** возвращает 0. Версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвера Native Client ODBC вводит опцию для водителей, специфичную для [s'LGetStmtAttr,](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) SQL_SOPT_SS_NOCOUNT_STATUS, чтобы сообщить о том, включается или выключается опция NOCOUNT. В любое **время,** когда приложение возвращает 0, приложение должно протестировать SQL_SOPT_SS_NOCOUNT_STATUS. При возврате SQL_NC_ON значение 0 от **S'LRowCount** указывает только на то, что сервер S'L'L не вернул количество строк. Если SQL_NC_OFF возвращается, это означает, что NOCOUNT выключен, а значение 0 от **S'LRowCount** указывает на то, что выписка не повлияла на строки. Приложения не должны отображать значение **S'LRowCount,** когда SQL_SOPT_SS_NOCOUNT_STATUS SQL_NC_OFF. Большие пакеты или хранимые процедуры могут содержать несколько инструкций SET NOCOUNT, следовательно, программисты не должны предполагать, что параметр SQL_SOPT_SS_NOCOUNT_STATUS останется неизменным. Опция должна тестироваться каждый раз, когда **S'LRowCount** возвращает 0.  
  
 Несколько других инструкций Transact-SQL возвращают данные в сообщениях, а не в результирующих наборах. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] водитель Native Client ODBC получает эти сообщения, он возвращает SQL_SUCCESS_WITH_INFO, чтобы сообщить приложению о доступных информационных сообщениях. Для получения этих сообщений приложение может позвонить в **S'LGetDiagRec.** Инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], работающие таким способом, перечислены ниже.  
  
-   DBCC  
  
-   SET SHOWPLAN (доступна в ранних версиях SQL Server)  
  
-   SET STATISTICS  
  
-   PRINT  
  
-   RAISERROR  
  
 Водитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC возвращает SQL_ERROR на RAISERROR с тяжестью 11 или выше. При уровне серьезности RAISERROR от 19 и выше соединение отключается.  
  
 Чтобы обработать результирующие наборы инструкции SQL, приложение выполняет следующие действия.  
  
-   Определяет характеристики результирующего набора.  
  
-   Привязывает столбцы к переменным программы.  
  
-   Получает одно значение, целую строку значений, или несколько строк значений.  
  
-   Проверяет наличие результирующих наборов, и в случае их существования, начинает цикл снова для определения характеристик нового результирующего набора.  
  
 Процесс получения строк из источника данных и передачи их в приложение называется выборкой.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Определение характеристик набора результатов &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
-   [Назначение хранилища](../../relational-databases/native-client-odbc-results/assigning-storage.md)  
  
-   [Выборка итоговых данных](../../relational-databases/native-client-odbc-results/fetching-result-data.md)  
  
-   [Картирование типов данных &#40;&#41;ODBC](../../relational-databases/native-client-odbc-results/mapping-data-types-odbc.md)  
  
-   [Использование типов данных](../../relational-databases/native-client-odbc-results/data-type-usage.md)  
  
-   [Автоматическое преобразование символьных данных](../../relational-databases/native-client-odbc-results/autotranslation-of-character-data.md)  
  
## <a name="see-also"></a>См. также:  
 [Родной клиент сервера &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [Обработка результатов Как-к темам &#40;odBC&#41;](https://msdn.microsoft.com/library/772d9064-c91d-4cac-8b60-fcc16bf76e10)  
  
  
