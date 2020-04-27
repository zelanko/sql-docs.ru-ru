---
title: Использование символьного формата для импорта или экспорта данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], character
- character formats [SQL Server]
ms.assetid: d925e66a-1a73-43cd-bc06-1cbdf8174a4d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ab658be26dc8ccbdd4e760d0b1bc835ace3b2c38
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66011669"
---
# <a name="use-character-format-to-import-or-export-data-sql-server"></a>Использование символьного формата для импорта и экспорта данных (SQL Server)
  Символьный формат рекомендуется применять при выполнении массового экспорта данных в текстовый файл, который предназначен для использования в других программах, а также при выполнении массового импорта данных из текстового файла, созданного другими программами.  
  
> [!NOTE]  
>  При массовом переносе данных между экземплярами [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , если файл данных содержит символьные данные в Юникоде, но не содержит расширенные символы и символы в двухбайтовой кодировке (DBCS), используйте символы в формате Юникод. Дополнительные сведения см. в разделе [Использование символьного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-character-format-to-import-or-export-data-sql-server.md).  
  
 В символьном формате все столбцы представлены в формате символьных данных. Хранение данных в символьном формате удобно в том случае, когда данные используются в других программах (например электронных таблицах) или когда на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо перенести данные из базы данных другого поставщика (например Oracle).  
  
## <a name="considerations-for-using-character-format"></a>Замечания по использованию символьного формата  
 При использовании символьного формата имейте в виду следующее.  
  
-   По умолчанию программа **bcp** разделяет поля символьных данных с помощью символа табуляции и завершает записи символом новой строки. Сведения о том, как указать другой признак конца поля, см. в статье [Определение признаков конца поля и строки (SQL Server)](specify-field-and-row-terminators-sql-server.md).  
  
-   По умолчанию перед выполнением массового импорта или экспорта символьных данных выполняются следующие преобразования.  
  
    |Направление массовой операции|Преобразование|  
    |---------------------------------|----------------|  
    |Экспорт|Преобразует данные в символьное представление. Если это явно запрошено, данные в символьных столбцах преобразуются в требуемую кодовую страницу. Если кодовая страница не указана, символьные данные преобразуются в кодовую страницу изготовителя оборудования (OEM) клиентского компьютера.|  
    |Импорт|Если необходимо, преобразует символьные данные в собственное представление, а также преобразует данные из кодовой страницы клиента в кодовую страницу целевого столбца.|  
  
-   Чтобы предотвратить потерю дополнительных символов при преобразовании, применяйте символьный формат Юникода либо укажите кодовую страницу.  
  
-   Значения типа `sql_variant` сохраняются в файле в символьном формате без метаданных. Каждое значение типа данных преобразуется в формат типа `char` в соответствии с правилами неявного преобразования данных. В столбец типа `sql_variant` данные импортируются как тип `char`. При импорте в столбец типа данных, отличного от типа `sql_variant`, данные преобразуются из типа `char` в соответствии с правилами неявного преобразования. Дополнительные сведения о преобразовании данных см. в статье [Преобразование типов данных (ядро СУБД)](/sql/t-sql/data-types/data-type-conversion-database-engine).  
  
-   Программа **bcp** экспортирует `money` значения в виде файлов данных символьного формата с четырьмя цифрами после десятичной запятой и без символов группирования цифр, таких как разделители-запятые. Например: для столбца типа `money`, содержащего значение 1 234 567,123456, будет выполнен массовый экспорт в файл данных в виде символьной строки «1234567,1235».  
  
## <a name="command-options-for-character-format"></a>Параметры команд для символьного формата  
 Данные символьного формата можно импортировать в таблицу с помощью программы **bcp**, BULK INSERT или INSERT... Выбор \* из OPENROWSET (BULK...). Для команды **bcp** или инструкции BULK INSERT можно указать формат данных в командной строке. Для инструкции INSERT ... SELECT * FROM OPENROWSET(BULK...) нужно указать формат данных в файле форматирования.  
  
 Символьный формат поддерживается следующими параметрами командной строки.  
  
|Get-Help|Параметр|Описание|  
|-------------|------------|-----------------|  
|**bcp**|**-c**|Заставляет служебную программу **bcp** использовать символьные данные. <sup>1</sup>|  
|BULK INSERT|DATAFILETYPE **='char'**|Использует символьный формат при массовом импорте данных.|  
  
 <sup>1</sup> чтобы загрузить символьные данные (**-c**) в формат, совместимый с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] клиентов, используйте параметр **-V** . Дополнительные сведения см. в разделе [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).  
  
 Дополнительные сведения см. в статьях [Программа bcp](../../tools/bcp-utility.md), [BULK INSERT (SQL Server)](/sql/t-sql/statements/bulk-insert-transact-sql) и [OPENROWSET (SQL Server)](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Также в файле форматирования можно указать форматирование для каждого поля. Дополнительные сведения см в разделе [Файлы форматирования для импорта или экспорта данных (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показано, как массово экспортировать символьные данные с помощью **bcp** и массово импортировать эти же данные с помощью BULK INSERT.  
  
### <a name="sample-table"></a>Образец таблицы  
 Для выполнения примеров необходима таблица **myTestCharData** в образце базы данных **AdventureWorks** в схеме **dbo**. Перед выполнением примеров следует создать эту таблицу. Для этого в редакторе запросов SQL среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Чтобы заполнить эту таблицу и просмотреть результирующее содержимое, выполните следующие инструкции:  
  
```  
INSERT INTO myTestCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestCharData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestCharData  
  
```  
  
### <a name="using-bcp-to-bulk-export-character-data"></a>Использование программы bcp для массового экспорта символьных данных  
 Чтобы экспортировать данные из таблицы в файл данных, используйте команду **bcp** с параметром **out** и следующими квалификаторами:  
  
|Квалификаторы|Описание|  
|----------------|-----------------|  
|**-c**|Указывает символьный формат данных.|  
|**-t** `,`|Задает запятую (`,`) в качестве признака конца поля.<br /><br /> Примечание. По умолчанию признаком конца поля является символ табуляции (\t). Дополнительные сведения см. в разделе [Определение признаков конца поля и строки (SQL Server)](specify-field-and-row-terminators-sql-server.md).|  
|**-T**|Указывает, что программа **bcp** устанавливает доверительное соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием встроенной безопасности. Если параметр **-T** не указан, для входа необходимо указать **-U** и **-P** .|  
  
 Следующий пример выполняет массовый экспорт данных из таблицы `myTestCharData` в новый файл данных `myTestCharData-c.Dat` в символьном формате. В качестве признака конца поля используется запятая (,). В командной строке [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows введите:  
  
```  
bcp AdventureWorks..myTestCharData out C:\myTestCharData-c.Dat -c -t, -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-character-data"></a>Применение инструкции BULK INSERT для массового импорта символьных данных  
 В следующем примере с помощью инструкции BULK INSERT выполняется импорт данных из файла данных `myTestCharData-c.Dat` в таблицу `myTestCharData` . В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestCharData   
   FROM 'C:\myTestCharData-c.Dat'   
   WITH (  
      DATAFILETYPE='char',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestCharData;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
 **Использование форматов данных для массового импорта или экспорта**  
  
-   [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Использование собственного формата для импорта и экспорта данных (SQL Server)](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)   
 [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
  
