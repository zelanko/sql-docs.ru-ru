---
title: Использование собственного формата Юникода для импорта или экспорта данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- Unicode [SQL Server], bulk importing and exporting
- data formats [SQL Server], Unicode native
ms.assetid: a6213308-f3d5-406e-9029-19d8bb3367f3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b1d115dacc53cb074080931c2ebad88dcaf1c68d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66011567"
---
# <a name="use-unicode-native-format-to-import-or-export-data-sql-server"></a>Использование собственного формата Юникода для импорта или экспорта данных (SQL Server)
  Собственный формат Юникода полезен, если необходимо скопировать данные из одной [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установки в другую. Использование собственного формата для несимвольных данных позволяет сэкономить время благодаря исключению ненужных преобразований типов данных в символьный формат и обратно. Использование символьного формата Юникода для всех символьных данных предотвращает потерю дополнительных символов в ходе массовой передачи данных между серверами, использующими различные кодовые страницы. Файл данных в собственном формате Юникода может быть считан с помощью любого метода массового импорта.  
  
 Собственный формат Юникода рекомендуется использовать для массовой передачи данных между несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью файла данных, который содержит дополнительный набор символов или символы в кодировке DBCS. В отношении несимвольных данных собственный формат Юникода использует собственные (для базы данных) типы данных. В отношении символьных данных, таких как `char`, `nchar`, `varchar`, `nvarchar`, `text`, `varchar(max)`, `nvarchar(max)` и `ntext`, собственный формат Юникода использует формат данных Юникода.  
  
 Данные типа `sql_variant`, которые хранятся в виде инструкции SQLVARIANT в файле собственного формата Юникода, функционируют точно так, как в файле данных собственного формата, за исключением того, что значения типа `char` и `varchar` преобразуются в `nchar` и `nvarchar`, что требует вдвое больше места для хранения столбцов, подлежащих преобразованию. В процессе массового импорта в столбец таблицы исходные метаданные сохраняются, а значения преобразуются обратно в исходные типы данных `char` и `varchar`.  
  
## <a name="command-options-for-unicode-native-format"></a>Командные параметры для собственного формата Юникода  
 Вы можете импортировать данные в собственном формате Юникода в таблицу с помощью программы **bcp**, BULK INSERT или INSERT... Выбор \* из OPENROWSET (BULK...). Для команды **bcp** или инструкции BULK INSERT можно указать формат данных в командной строке. Для инструкции INSERT ... SELECT * FROM OPENROWSET(BULK...) нужно указать формат данных в файле форматирования.  
  
 Собственный формат Юникода поддерживается следующими параметрами.  
  
|Get-Help|Параметр|Description|  
|-------------|------------|-----------------|  
|**bcp**|**-N**|Заставляет служебную программу **bcp** использовать собственный формат Юникода, в котором используются собственные типы данных (базы данных) для всех несимвольных данных и формат символьных данных Юникода для`char`всех символьных `nvarchar`данных `text`(, `ntext` `nchar` `varchar`,,, и).|  
|BULK INSERT|DATAFILETYPE **='** widenative **'**|Собственный формат Юникода используется при массовом импорте данных.|  
  
 Дополнительные сведения см. в статьях [Программа bcp](../../tools/bcp-utility.md), [BULK INSERT (SQL Server)](/sql/t-sql/statements/bulk-insert-transact-sql) и [OPENROWSET (SQL Server)](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Также в файле форматирования можно указать форматирование для каждого поля. Дополнительные сведения см в разделе [Файлы форматирования для импорта или экспорта данных (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md).  
  
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
  
|Квалификаторы|Description|  
|----------------|-----------------|  
|**-N**|Указывает собственные типы данных.|  
|**-T**|Указывает, что программа **bcp** устанавливает доверительное соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием встроенной безопасности. Если параметр **-T** не указан, для входа необходимо указать **-U** и **-P** .|  
  
 В следующем примере показан массовый экспорт данных в собственном формате из таблицы `myTestUniNativeData` в новый файл данных с именем `myTestUniNativeData-N.Dat` . В командной строке [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows введите:  
  
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
  
-   [Используйте символьный формат для импорта или экспорта &#40;данных SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Используйте собственный формат для импорта или экспорта &#40;данных SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Используйте символьный формат Юникода для импорта или экспорта &#40;данных SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Типы данных &#40;&#41;Transact-SQL](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
