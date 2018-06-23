---
title: Использование файлов данных и файлов формата | Документы Microsoft
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
- bulk copy [ODBC], file formats
- ODBC, functions
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [SQL Server Native Client]
- ODBC, bulk copy operations
- bulk copy [ODBC], data files
ms.assetid: c01b7155-3f0a-473d-90b7-87a97bc56ca5
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d2cbdb55f61752667cdf01045a715ee679125a65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109926"
---
# <a name="using-data-files-and-format-files"></a>Использование файлов данных и файлов форматирования
  Простейшая программа массового копирования выполняет следующие действия.  
  
1.  Вызовы [bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) для задания массового копирования (задания значения BCP_OUT) из таблицы или представления в файл данных.  
  
2.  Вызовы [bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) для выполнения операции массового копирования.  
  
 Файл данных создается в собственном режиме; следовательно, данные из всех столбцов таблицы или представления хранятся в файле данных в том же формате, что и в базе данных. Затем файл можно с помощью операции массового копирования скопировать на сервер, выполнив те же шаги и установив значение DB_IN вместо DB_OUT. Это возможно только в случае, когда структура исходной и целевой таблиц идентична. Результирующий файл данных также может быть входным для **bcp** программы с помощью **/n** (собственный режим).  
  
 Для массового копирования результирующего набора из инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], а не непосредственно из таблицы или представления.  
  
1.  Вызовите **bcp_init** для задания массового копирования out, но имя таблицы, укажите значение NULL.  
  
2.  Вызовите [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) с *eOption* значение BCPHINTS и *iValue* — указатель на строку SQLTCHAR, содержащую инструкцию Transact-SQL.  
  
3.  Вызовите **bcp_exec** для выполнения операции массового копирования.  
  
 В качестве инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] подходит любая инструкция, которая создает результирующий набор. Создается файл данных, содержащий первый результирующий набор инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Если инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] создает несколько результирующих наборов, операция массового копирования пропускает все результирующие наборы, следующие за первым.  
  
 Чтобы создать файл данных, в которых столбец данные хранятся в формате, отличном от таблицы, вызовите [bcp_columns](../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) чтобы указать, сколько столбцов будут изменены, затем вызовите [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) для каждого столбца, формат которого Вы хотите изменить. Это необходимо сделать после вызова метода **bcp_init** , но перед вызовом метода **bcp_exec**. **bcp_colfmt** указывает формат, в котором хранятся данные столбца в файле данных. Он может быть использован при входящем или исходящем массовом копировании. Можно также использовать **bcp_colfmt** для задания признаков конца строк и столбцов. Например, если данные содержат не символы табуляции, можно создать файл с разделителями-знаками табуляции, используя **bcp_colfmt** присвоить символ табуляции в качестве признака конца для каждого столбца.  
  
 При массовом копировании с использованием **bcp_colfmt**, можно легко создать файл форматирования, описывающий файл данных, созданный путем вызова [bcp_writefmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) после последнего вызова **bcp_colfmt**.  
  
 При массовом копировании из файла данных, описанного файлом форматирования, считать файл форматирования, путем вызова [bcp_readfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) после **bcp_init** перед вызовом **bcp_exec**.  
  
 **Bcp_control** функция управляет несколькими параметрами при массовом копировании в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из файла данных. **bcp_control** устанавливает значения параметров, например максимальное число ошибок до завершения операции, номер строки в файле, на которой начинается массовое копирование строк для остановки на и размер пакета.  
  
## <a name="see-also"></a>См. также  
 [Выполнение операций массового копирования &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  