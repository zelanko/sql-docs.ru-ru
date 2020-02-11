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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "71708211"
---
# <a name="import-and-export-bulk-data-by-using-the-bcp-utility-sql-server"></a>Массовый импорт и экспорт данных с использованием программы bcp (SQL Server)

В этом разделе представлен обзор использования [программы bcp](../../tools/bcp-utility.md) для экспорта данных из любого местоположения в базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в которой может применяться инструкция SELECT, включая секционированные представления.  
  
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
  
-   [Создайте файл форматирования &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
-   [Примеры выполнения операций импорта и экспорта XML-документов &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Не заключайте значения идентификаторов при выполнении много&#40;ного импорта данных SQL Server&#41;](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Не заменяйте значения NULL или используйте значение по умолчанию во время &#40;ного импорта SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Укажите признаки конца поля и строки &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
-   [Использование файла форматирования для SQL Server &#40;данных при выполнении операций импорта&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Используйте символьный формат для импорта или экспорта &#40;данных SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Используйте собственный формат для импорта или экспорта &#40;данных SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Используйте символьный формат Юникода для импорта или экспорта &#40;данных SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Используйте собственный формат Юникода для импорта или экспорта &#40;данных SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  

## <a name="see-also"></a>См. также:

[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) 
 [предложение SELECT &#40;](/sql/t-sql/queries/select-clause-transact-sql) 
 [служебной программы](../../tools/bcp-utility.md) Transact-SQL&#41;bcp   
[Подготовка к групповому импорту данных &#40;SQL Server&#41;](prepare-to-bulk-import-data-sql-server.md) 
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 
 [групповой импорт и экспорт данных &#40;](bulk-import-and-export-of-data-sql-server.md) 
SQL Server&#41;[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) 
 [Создание файла форматирования &#40;](create-a-format-file-sql-server.md) SQL Server