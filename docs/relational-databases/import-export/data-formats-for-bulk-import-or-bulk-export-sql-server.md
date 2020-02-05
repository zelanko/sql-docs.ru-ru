---
title: Форматы данных для массового импорта и экспорта
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], choosing
- bulk importing [SQL Server], data formats
ms.assetid: 73fe6741-9437-4b26-b030-28b863e74399
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.custom: seo-lt-2019
ms.openlocfilehash: 1f6bb69e4d1a18cf2f3e596a4bbbd179e8c4f373
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "74056021"
---
# <a name="data-formats-for-bulk-import-or-bulk-export-sql-server"></a>Форматы данных для массового импорта и экспорта (SQL Server)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может принимать данные в символьном или исходном двоичном формате. Символьный формат применяется при перемещении данных между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и другим приложением (например [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel) или другим сервером базы данных (например Oracle или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Собственный формат может применяться только при переносе данных между экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **В этом разделе.**  
  
-   [Форматы данных для массового импорта или экспорта](#ComponentsAndConcepts)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="ComponentsAndConcepts"></a> Форматы данных для массового импорта или экспорта  
 В следующей таблице приведены общие правила выбора формата данных в зависимости от того, как представлены данные, а также от источника или назначения операции.  
  
|Операция|Собственный|собственный формат Юникода|Символ|символьный формат Юникода|  
|---------------|------------|--------------------|---------------|-----------------------|  
|Массовый перенос данных между несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи файла данных, не содержащего символы расширенной или двухбайтовой кодировки (DBCS). Если не используется файл форматирования, эти таблицы должны быть определены одинаково.|Да*|-|-|-|  
|Для столбцов **sql_variant** наилучшим образом подходит собственный формат данных, так как в отличие от символьного и формата Юникод собственный формат сохраняет метаданные для каждого значения **sql_variant** .|Да|-|-|-|  
|Массовая передача данных между несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи файла данных, содержащего символы расширенной или двухбайтовой кодировки (DBCS).|-|Да|-|-|  
|Массовый импорт данных из текстового файла, формируемого другой программой.|-|-|Да|-|  
|Массовый экспорт данных в текстовый файл, который должен использоваться другой программой.|-|-|Да|-|  
|Массовая передача данных между несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи файла данных, содержащего данные Юникода и не содержащего символы расширенной или двухбайтовой кодировки (DBCS).|-|-|-|Да|  
  
 \* Самый быстрый метод массового экспорта данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предполагает использование программы **bcp**.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Использование собственного формата для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата Юникод для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](../../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Указание форматов данных для совместимости с помощью программы bcp (SQL Server)](../../relational-databases/import-export/specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)  
  
  
