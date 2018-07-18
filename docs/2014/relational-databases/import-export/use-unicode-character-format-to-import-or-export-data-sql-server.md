---
title: Использование символьного формата Юникода для импорта или экспорта данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: data-movement
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], Unicode character
- Unicode [SQL Server], bulk importing and exporting
ms.assetid: 74342a11-c1c0-4746-b482-7f3537744a70
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9124d6807bc4fea19e98fb0f099cd31ba15172bd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37235344"
---
# <a name="use-unicode-character-format-to-import-or-export-data-sql-server"></a>Использование символьного формата Юникода для импорта и экспорта данных (SQL Server)
  Символьный формат Юникода рекомендуется для массового переноса данных между несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через файл данных, содержащий символы расширенной или двухбайтовой кодировки (DBCS). Формат символьных данных Юникода позволяет экспортировать данные из сервера в кодовой странице, отличающейся от кодовой страницы, используемой выполняющим операцию клиентом. В этих случаях использование символьного формата Юникода имеет следующие преимущества.  
  
-   Если данные источника и назначения имеют тип данных Юникода, при использовании символьного формата Юникода все символьные данные сохраняются.  
  
-   Если данные источника и назначения имеют тип данных, отличный от Юникода, использование символьного формата Юникода позволяет уменьшить потери дополнительных символов данных источника, которые не могут быть представимы в назначении.  
  
 Файлы данных символьного формата Юникода следуют соглашениям для файлов Юникода. Первые два байта файла являются шестнадцатеричными числами 0xFFFE. Эти байты служат в качестве меток порядка байтов, определяющих, хранится старший байт в файле первым или последним.  
  
> [!IMPORTANT]  
>  Чтобы файл форматирования мог работать с файлом данных в Юникоде, все поля входных данных должны быть представлены в виде текстовых строк в Юникоде (то есть в Юникоде в виде строк фиксированной длины или заканчивающимися символом конца строки).  
  
 `sql_variant` Данные, хранящиеся в файле данных символьного формата Юникода работает таким же образом, как он работает в файле данных символьного формата, за исключением того, что данные хранятся в виде `nchar` вместо `char` данных. Дополнительные сведения о формате символов см. в разделе [Поддержка параметров сортировки и Юникода](../collations/collation-and-unicode-support.md).  
  
 Сведения об использовании признака конца поля или строки, отличного от признака по умолчанию, предоставляемого в символьном формате Юникод, см. в разделе [Определение признаков конца поля и строки (SQL Server)](specify-field-and-row-terminators-sql-server.md).  
  
## <a name="command-options-for-unicode-character-format"></a>Параметры команд для символьного формата Юникода  
 Импортировать в таблицу данные в символьном формате Юникод можно при помощи команды **bcp**, инструкций BULK INSERT или INSERT… ВЫБЕРИТЕ \* FROM OPENROWSET(BULK...). Для команды **bcp** или инструкции BULK INSERT формат данных можно указать в командной строке. Для инструкции INSERT ... SELECT * FROM OPENROWSET(BULK...) нужно указать формат данных в файле форматирования.  
  
 Символьный формат Юникода поддерживается следующими параметрами командной строки.  
  
|Command|Параметр|Описание|  
|-------------|------------|-----------------|  
|**bcp**|**-w**|Использует символьный формат Юникода.|  
|BULK INSERT|DATAFILETYPE **='** widechar **'**|Использует символьный формат Юникода при массовом импорте данных.|  
  
 Дополнительные сведения см. в статьях [Программа bcp](../../tools/bcp-utility.md), [BULK INSERT (SQL Server)](/sql/t-sql/statements/bulk-insert-transact-sql) и [OPENROWSET (SQL Server)](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Также в файле форматирования можно указать форматирование для каждого поля. Дополнительные сведения см. в статье [Файлы форматирования для импорта или экспорта данных (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="examples"></a>Примеры  
 В следующих примерах демонстрируется массовый экспорт символьных данных в Юникоде при помощи команды **bcp** и массовый импорт тех же данных при помощи инструкции BULK INSERT.  
  
### <a name="sample-table"></a>Образец таблицы  
 Для работы примеров необходимо, чтобы в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] в схеме `myTestUniCharData` была создана таблица `dbo`. Перед выполнением примеров следует создать эту таблицу. Для создания этой таблицы в редакторе запросов среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] выполните следующий код:  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestUniCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Чтобы заполнить эту таблицу и просмотреть результирующее содержимое, выполните следующие инструкции:  
  
```  
INSERT INTO myTestUniCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3')   
        ,(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
  
```  
  
### <a name="using-bcp-to-bulk-export-unicode-character-data"></a>Использование программы bcp для массового экспорта символьных данных формата Юникода  
 Чтобы экспортировать данные из таблицы в файл данных, используйте команду **bcp** с параметром **out** и следующими квалификаторами:  
  
|Квалификаторы|Описание|  
|----------------|-----------------|  
|**-w**|Задает символьный формат Юникода.|  
|**-t** `,`|Задает запятую (`,`) в качестве признака конца поля.<br /><br /> Примечание: По умолчанию признак конца поля является символ табуляции Юникода (\t). Дополнительные сведения см. в разделе [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).|  
|**-T**|Указывает, что программа **bcp** устанавливает доверительное соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием встроенной безопасности. Если параметр **-T** не указан, необходимо указать параметры **-U** и **-P**, чтобы успешно выполнить вход.|  
  
 Далее приводится пример массового экспорта символьных данных в Юникоде из таблицы `myTestUniCharData` в новый файл данных `myTestUniCharData-w.Dat`, в котором признаком конца поля служит запятая (`,`). В командной строке [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows введите:  
  
```  
bcp AdventureWorks2012..myTestUniCharData out C:\myTestUniCharData-w.Dat -w -t, -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-unicode-character-data"></a>Использование инструкции BULK INSERT для массового импорта символьных данных формата Юникода  
 В следующем примере инструкция `BULK INSERT` используется для импорта данных из файла `myTestUniCharData-w.Dat` в таблицу `myTestUniCharData`. В инструкции должен быть объявлен признак конца поля (`,`), отличающийся от установленного по умолчанию. В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestUniCharData   
   FROM 'C:\myTestUniCharData-w.Dat'   
   WITH (  
      DATAFILETYPE='widechar',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Использование форматов данных для массового импорта или экспорта**  
  
-   [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата для импорта и экспорта данных (SQL Server)](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>См. также  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)   
 [Поддержка параметров сортировки и Юникода](../collations/collation-and-unicode-support.md)  
  
  
