---
title: Использование собственного формата Юникода для импорта или экспорта данных (SQL Server) | Документация Майкрософт
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
- Unicode [SQL Server], bulk importing and exporting
- data formats [SQL Server], Unicode native
ms.assetid: a6213308-f3d5-406e-9029-19d8bb3367f3
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 310234920939cfea19d6d17370bc3c427ff3fbcc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095450"
---
# <a name="use-unicode-native-format-to-import-or-export-data-sql-server"></a>Использование собственного формата Юникода для импорта или экспорта данных (SQL Server)
  Собственный формат Юникода может быть полезен при копировании данных с одной установки [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на другую. Использование собственного формата для несимвольных данных позволяет сэкономить время благодаря исключению ненужных преобразований типов данных в символьный формат и обратно. Использование символьного формата Юникода для всех символьных данных предотвращает потерю дополнительных символов в ходе массовой передачи данных между серверами, использующими различные кодовые страницы. Файл данных в собственном формате Юникода может быть считан с помощью любого метода массового импорта.  
  
 Собственный формат Юникода рекомендуется использовать для массовой передачи данных между несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью файла данных, который содержит дополнительный набор символов или символы в кодировке DBCS. В отношении несимвольных данных собственный формат Юникода использует собственные (для базы данных) типы данных. Для символьных данных таких как `char`, `nchar`, `varchar`, `nvarchar`, `text`, `varchar(max)`, `nvarchar(max)`, и `ntext`, собственный формат Юникода использует формат символьных данных Юникода.  
  
 Данные типа `sql_variant`, которые хранятся в виде инструкции SQLVARIANT в файле собственного формата Юникода, функционируют точно так, как в файле данных собственного формата, за исключением того, что значения типа `char` и `varchar` преобразуются в `nchar` и `nvarchar`, что требует вдвое больше места для хранения столбцов, подлежащих преобразованию. Исходные метаданные сохраняются, а значения преобразуются обратно в исходные `char` и `varchar` типа данных в процессе массового импорта в столбец таблицы.  
  
## <a name="command-options-for-unicode-native-format"></a>Командные параметры для собственного формата Юникода  
 Импортировать в таблицу данные в собственном формате Юникод можно с помощью программы **bcp** или с помощью инструкции BULK INSERT или INSERT... ВЫБЕРИТЕ \* FROM OPENROWSET(BULK...). Для команды **bcp** или инструкции BULK INSERT формат данных можно указать в командной строке. Для инструкции INSERT ... SELECT * FROM OPENROWSET(BULK...) нужно указать формат данных в файле форматирования.  
  
 Собственный формат Юникода поддерживается следующими параметрами.  
  
|Command|Параметр|Описание|  
|-------------|------------|-----------------|  
|**bcp**|**-N**|Вызывает **bcp** типы программы, чтобы использовать собственный формат Юникода, который использует собственные (базы данных) данных для всех несимвольных данных и формат символьных данных Юникода для всех символьных (`char`, `nchar`, `varchar`, `nvarchar`, `text`, и `ntext`) данных.|  
|BULK INSERT|DATAFILETYPE **='** widenative **'**|Собственный формат Юникода используется при массовом импорте данных.|  
  
 Дополнительные сведения см. в статьях [Программа bcp](../../tools/bcp-utility.md), [BULK INSERT (SQL Server)](/sql/t-sql/statements/bulk-insert-transact-sql) и [OPENROWSET (SQL Server)](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Также в файле форматирования можно указать форматирование для каждого поля. Дополнительные сведения см. в статье [Файлы форматирования для импорта или экспорта данных (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показан массовый экспорт данных в собственном формате с помощью программы **bcp** , а также массовый импорт тех же данных с помощью инструкции BULK INSERT.  
  
### <a name="sample-table"></a>Образец таблицы  
 Для использования в примерах необходимо создать таблицу **myTestUniNativeData** в образце базы данных **AdventureWorks** под схемой **dbo** . Перед выполнением примеров следует создать эту таблицу. В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestUniNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Чтобы заполнить эту таблицу и просмотреть результирующее содержимое, выполните следующие инструкции:  
  
```  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a>Массовый экспорт собственных данных с помощью программы bcp  
 Чтобы экспортировать данные из таблицы в файл данных, используйте команду **bcp** с параметром **out** и следующими квалификаторами:  
  
|Квалификаторы|Описание|  
|----------------|-----------------|  
|**-N**|Указывает собственные типы данных.|  
|**-T**|Указывает, что программа **bcp** устанавливает доверительное соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием встроенной безопасности. Если параметр **-T** не указан, для входа необходимо указать **-U** и **-P** .|  
  
 В следующем примере показан массовый экспорт данных в собственном формате из таблицы `myTestUniNativeData` в новый файл данных с именем `myTestUniNativeData-N.Dat`. В командной строке [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows введите:  
  
```  
bcp AdventureWorks..myTestUniNativeData out C:\myTestUniNativeData-N.Dat -N -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a>Массовый импорт собственных данных с помощью инструкции BULK INSERT  
 В следующем примере с помощью инструкции BULK INSERT выполняется импорт данных из файла данных `myTestUniNativeData-N.Dat` в таблицу `myTestUniNativeData` . В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestUniNativeData   
    FROM 'C:\myTestUniNativeData-N.Dat'   
   WITH (DATAFILETYPE='widenative');   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Использование форматов данных для массового импорта или экспорта**  
  
-   [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата для импорта и экспорта данных (SQL Server)](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>См. также  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
