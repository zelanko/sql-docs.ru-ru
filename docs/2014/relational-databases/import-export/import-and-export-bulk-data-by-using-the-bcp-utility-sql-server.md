---
title: Массовый импорт и экспорт данных с использованием программы bcp (SQL Server) | Документация Майкрософт
ms.prod: sql-server-2014
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], bcp utility
- bulk importing [SQL Server], bcp utility
- bcp utility [SQL Server], about bcp utility
ms.assetid: 73e949de-67a3-4c84-9735-7da1ad4ba34a
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: ''
ms.custom: ''
ms.date: 06/14/2017
ms.openlocfilehash: 7075bf87ed64686750bc4a267af431268987ff35
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71708211"
---
# <a name="import-and-export-bulk-data-by-using-the-bcp-utility-sql-server"></a>Массовый импорт и экспорт данных с использованием программы bcp (SQL Server)

В этом разделе представлен обзор использования [программы bcp](../../tools/bcp-utility.md) для экспорта данных из любого местоположения в базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в которой может применяться инструкция SELECT, включая секционированные представления.  
  
 Программа bcp (bcp.exe) представляет собой инструмент командной строки, использующий API-интерфейс программы массового копирования (BCP). Программа bcp выполняет следующие задачи:  
  
-   массовый экспорт данных из таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в файл данных;  
  
-   массовый экспорт данных из запроса;  
  
-   массовый импорт данных из файла данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   создание файлов форматирования.  
  
 Служебная программа bcp вызывается командой **bcp** . Применение команды **bcp** для массового импорта требует понимания схемы таблицы и типов данных ее столбцов (если не используется заранее созданный файл форматирования).  
  
 Программа bcp может экспортировать данные из таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в файл данных для использования другими программами. Программа также может импортировать данные в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из другой программы, обычно другой системы управления базой данных (СУБД). Вначале выполняется экспорт данных из исходной программы в файл данных, а затем отдельной операцией данные копируются из файла данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Команда **bcp** предоставляет параметры для указания типа данных файла данных и других сведений. Если такие ключи не заданы, программа выводит приглашение для ввода этих сведений, например для типа полей данных в файле данных. Затем команда запрашивает, нужно ли создать файл форматирования, содержащий данные ответы. Чтобы обеспечить гибкость для будущих операций массового импорта и экспорта, часто используется файл форматирования. В последующих командах **bcp** вы можете указать файл форматирования для эквивалентных файлов данных. Дополнительные сведения см. в разделе [Указание форматов данных для совместимости с помощью программы bcp (SQL Server)](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).  
  
> [!NOTE]  
>  Служебная программа bcp написана при использовании массового копирования ODBC  
  
 Описание синтаксиса команды **bcp** см. в разделе [Служебная программа bcp](../../tools/bcp-utility.md).  
  
## <a name="examples"></a>Примеры

 Примеры **bcp** см. здесь:  
  
-   [Программа bcp](../../tools/bcp-utility.md)  
  
-   [Создание файла форматирования (SQL Server)](create-a-format-file-sql-server.md)  
  
-   [Примеры массового импорта и экспорта XML-документов (SQL Server)](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Сохранение значений идентификаторов при массовом импорте данных (SQL Server)](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Определение признаков конца поля и строки (SQL Server)](specify-field-and-row-terminators-sql-server.md)  
  
-   [Использование файла форматирования для массового импорта данных (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата для импорта и экспорта данных (SQL Server)](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-native-format-to-import-or-export-data-sql-server.md)  

## <a name="see-also"></a>См. также

[INSERT &#40;t-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)
[предложение &#40;SELECT, инструкция Transact&#41;-SQL](/sql/t-sql/queries/select-clause-transact-sql)
[bcp](../../tools/bcp-utility.md)   
[Подготовка к групповому импорту&#41;данных &#40;SQL Server](prepare-to-bulk-import-data-sql-server.md)
[BULK INSERT &#40;Transact&#41;-SQL](/sql/t-sql/statements/bulk-insert-transact-sql)
[массовым импортом &#40;и&#41;экспортом данных SQL Server](bulk-import-and-export-of-data-sql-server.md)1[OPENROWSET &#40; Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)5[Создание &#40;файла форматирования SQL Server&#41; ](create-a-format-file-sql-server.md)