---
title: Форматы данных для массового экспорта или импорта (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data formats [SQL Server], choosing
- bulk importing [SQL Server], data formats
ms.assetid: 73fe6741-9437-4b26-b030-28b863e74399
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e7ae0c46d3d602715e62f92396430e1f424067fc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192666"
---
# <a name="data-formats-for-bulk-import-or-bulk-export-sql-server"></a>Форматы данных для массового экспорта или импорта (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может принимать данные в символьном или исходном двоичном формате. Символьный формат применяется при перемещении данных между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и другим приложением (например [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel) или другим сервером базы данных (например Oracle или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Собственный формат может применяться только при переносе данных между экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **В этом разделе.**  
  
-   [Форматы данных для массового импорта или экспорта](#ComponentsAndConcepts)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="ComponentsAndConcepts"></a> Форматы данных для массового импорта или экспорта  
 В следующей таблице приведены общие правила выбора формата данных в зависимости от того, как представлены данные, а также от источника или назначения операции.  
  
|Операция|Собственный|собственный формат Юникода|Символ|символьный формат Юникода|  
|---------------|------------|--------------------|---------------|-----------------------|  
|Массовый перенос данных между несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи файла данных, не содержащего символы расширенной или двухбайтовой кодировки (DBCS). Если не используется файл форматирования, эти таблицы должны быть определены одинаково.|Да<sup>1</sup>|—|—|—|  
|Для столбцов типа `sql_variant` наилучшим образом подходит собственный формат данных, так как в отличие от символьного и формата Юникода, собственный формат сохраняет метаданные для каждого значения типа `sql_variant`.|Да|—|—|—|  
|Массовая передача данных между несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи файла данных, содержащего символы расширенной или двухбайтовой кодировки (DBCS).|—|Да|—|—|  
|Массовый импорт данных из текстового файла, формируемого другой программой.|—|—|Да|—|  
|Массовый экспорт данных в текстовый файл, который должен использоваться другой программой.|—|—|Да|—|  
|Массовая передача данных между несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи файла данных, содержащего данные Юникода и не содержащего символы расширенной или двухбайтовой кодировки (DBCS).|—|—|—|Да|  
  
 <sup>1</sup> самый быстрый метод массового экспорта данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при использовании **bcp**.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Использование собственного формата для импорта и экспорта данных (SQL Server)](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
## <a name="see-also"></a>См. также  
 [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)   
 [Указание форматов данных для совместимости с помощью программы bcp (SQL Server)](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)  
  
  
