---
title: Выполнение операций массового копирования (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC]
- ODBC, bulk copy operations
- minimally logged operations [SQL Server Native Client]
- bulk copy [ODBC], about bulk copy
ms.assetid: 5c793405-487c-4f52-88b8-0091d529afb3
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 445085c69f0fd98eff70be60575de5d2dcb002b3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100422"
---
# <a name="performing-bulk-copy-operations-odbc"></a>Выполнение операций массового копирования (ODBC)
  Стандарт ODBC напрямую не поддерживает операции массового копирования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0 или более поздней, драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает функции библиотеки DB-Library, выполняющие операции массового копирования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот собственный модуль драйвера обеспечивает легкий путь обновления для существующих приложений DB-Library, использующих функции массового копирования. Специализированная поддержка массового копирования реализована в следующих файлах.  
  
-   sqlncli.h  
  
     Включает прототипы функций и определения констант для функций массового копирования. Файл sqlncli.h должен входить в состав приложения ODBC, выполняющего операции массового копирования, и при компиляции приложения должен находиться в пути поиска включаемых файлов.  
  
-   sqlncli11.lib  
  
     Должна находиться в пути к библиотекам компоновщика и определена как файл для связывания. Файл sqlncli11.lib поставляется вместе с драйвером ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
-   sqlncli11.dll  
  
     Необходима во время выполнения. Файл sqlncli11.dll поставляется вместе с драйвером ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
> [!NOTE]  
>  ODBC **SQLBulkOperations** функция не имеет отношения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функциями массового копирования. Для выполнения операций массового копирования приложения должны использовать собственные функции массового копирования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="minimally-logging-bulk-copies"></a>Массовое копирование с минимальным ведением журнала  
 В модели полного восстановления все операции вставки строк, выполняемые при массовой загрузке, полностью регистрируются в журнале транзакций. При загрузке большого количества данных это может привести к быстрому заполнению журнала транзакций. При определенных условиях возможно минимальное протоколирование. Минимальное ведение журнала снижает вероятность заполнения журнала в результате массовой загрузки и является также более эффективным, чем полное ведение журнала.  
  
 Сведения об использовании минимальное ведение журнала см. в разделе [необходимые условия для минимального протоколирования массового импорта](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
## <a name="remarks"></a>Примечания  
 При использовании программы bcp.exe в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздних версий могут возникать ошибки в ситуациях, в которых в версиях, предшествующих [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ошибок не возникало. Это происходит по той причине, что в более поздних версиях программа bcp.exe больше не выполняет явное преобразование типов данных. До версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] программа bcp.exe преобразовывала числовые данные в тип money, если целевая таблица имела тип данных money. Однако в этой ситуации программа bcp.exe просто усекала лишние поля. Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], если типы данных в файле и целевой таблице не совпадают, программа bcp.exe выдает ошибку, если присутствуют данные, которые придется усечь, чтобы поместить в целевую таблицу. Для устранения этой ошибки преобразуйте данные в целевой тип данных. При необходимости используйте программу bcp.exe версии, предшествующей [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Использование файлов данных и файлов форматирования](using-data-files-and-format-files.md)  
  
-   [Массовое копирование из переменных приложения](bulk-copying-from-program-variables.md)  
  
-   [Управление размером пакета массового копирования](managing-bulk-copy-batch-sizes.md)  
  
-   [Массовое копирование данных text и image](bulk-copying-text-and-image-data.md)  
  
-   [Перевод массового копирования с DB-Library на ODBC](converting-from-db-library-to-odbc-bulk-copy.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [Массовый импорт и экспорт данных (SQL Server)](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  