---
title: Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], null values
- bulk importing [SQL Server], default values
- data formats [SQL Server], null values
- bulk rowset providers [SQL Server]
- bcp utility [SQL Server], null values
- BULK INSERT statement
- default values
- OPENROWSET function, bulk importing
- data formats [SQL Server], default values
ms.assetid: 6b91d762-337b-4345-a159-88abb3e64a81
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5999a7f3a952cd0392136a96bf3bf166c8e6b155
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66011894"
---
# <a name="keep-nulls-or-use-default-values-during-bulk-import-sql-server"></a>Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)
  При импорте данных в таблицу команда **bcp** и инструкция BULK INSERT используют значения по умолчанию, которые определены для столбцов таблицы. Например, если поле в файле данных имеет значение NULL, вместо него загружается значение по умолчанию соответствующего столбца. И команда **bcp** , и инструкция BULK INSERT позволяют пользователю указать, следует ли оставлять значения NULL.  
  
 Обычная инструкция INSERT, напротив, оставляет значение NULL и не использует значения по умолчанию. Инструкция INSERT ... Инструкция SELECT * FROM OPENROWSET(BULK...) ведет себя так же, как обычная инструкция INSERT, но поддерживает табличное указание для загрузки значений по умолчанию.  
  
> [!NOTE]  
>  Пример файла форматирования, пропускающего столбец таблицы, см. в статье [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md).  
  
## <a name="sample-table-and-data-file"></a>Образец таблицы и файла данных  
 Для выполнения примеров этого подраздела необходимо создать образец таблицы и файла данных.  
  
### <a name="sample-table"></a>Образец таблицы  
 Для выполнения примеров этого раздела требуется создать таблицу **MyTestDefaultCol2** в образце базы данных **AdventureWorks** в схеме **dbo**. Чтобы создать эту таблицу, в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] редакторе запросов выполните следующую команду:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE MyTestDefaultCol2   
(Col1 smallint,  
Col2 nvarchar(50) DEFAULT 'Default value of Col2',  
Col3 nvarchar(50)   
);  
GO  
  
```  
  
 Заметьте, что во втором столбце таблицы (`Col2`) хранится значение по умолчанию.  
  
### <a name="sample-format-file"></a>Образец файла форматирования  
 Некоторые примеры массового импорта используют не XML-файл форматирования `MyTestDefaultCol2-f-c.Fmt`, в точности соответствующий таблице `MyTestDefaultCol2`. Для создания этого файла форматирования в командной строке [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows введите следующую команду.  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 format nul -c -f C:\MyTestDefaultCol2-f-c.Fmt -t, -r\n -T  
  
```  
  
 Дополнительные сведения о создании файла форматирования см. в статье [Создание файла форматирования (SQL Server)](create-a-format-file-sql-server.md).  
  
### <a name="sample-data-file"></a>Образец файла данных  
 Следующий пример использует образец файла данных `MyTestEmptyField2-c.Dat`, второе поле которого не содержит значений. Файл данных `MyTestEmptyField2-c.Dat` содержит следующие записи.  
  
```  
1,,DataField3  
2,,DataField3  
  
```  
  
## <a name="keeping-null-values-with-bcp-or-bulk-insert"></a>Сохранение значение NULL при работе с командой bcp или инструкцией BULK INSERT  
 Следующие квалификаторы указывают, что вместо пустого поля в файле данных необходимо вставить не значение по умолчанию, а значение NULL.  
  
|Get-Help|Квалификатор|Тип квалификатора|  
|-------------|---------------|--------------------|  
|**bcp**|`-k`|Параметр|  
|BULK INSERT|KEEPNULLS<sup>1</sup>|Аргумент|  
  
 <sup>1</sup> для BULK INSERT, если значения по умолчанию недоступны, столбец таблицы должен быть определен для разрешения значений NULL.  
  
> [!NOTE]  
>  Эти квалификаторы отключают проверку определений DEFAULT для таблицы командами массового импорта. Однако для одновременно выполняемых инструкций INSERT определения DEFAULT требуются.  
  
 Дополнительные сведения см. в статьях [Программа bcp](../../tools/bcp-utility.md) и [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
### <a name="examples"></a>Примеры  
 Примеры в этом разделе показывают, как выполнить массовый импорт данных с помощью команды **bcp** или инструкции BULK INSERT и сохранить значения NULL.  
  
 Для второго столбца таблицы (**Col2**) задано значение по умолчанию. Соответствующее поле файла данных содержит пустые строки. По умолчанию при импорте данных из этого файла в таблицу **MyTestDefaultCol2** с помощью команды **bcp** или инструкции BULK INSERT вставляется значение по умолчанию столбца **Col2**, что приводит к получению следующих результатов.  
  
||||  
|-|-|-|  
|`1`|`Default value of Col2`|`DataField3`|  
|`2`|`Default value of Col2`|`DataField3`|  
  
 Чтобы вставить "`NULL`" вместо "`Default value of Col2`", необходимо использовать параметр `-k` Switch или keepnull (см, как показано в следующих примерах **bcp** и BULK INSERT.  
  
#### <a name="using-bcp-and-keeping-null-values"></a>Сохранение значений NULL при работе с командой bcp  
 Следующий пример демонстрирует, как сохранить значения NULL при использовании команды **bcp**. Команда **bcp** содержит следующие параметры:  
  
|Параметр|Описание|  
|------------|-----------------|  
|`-f`|Позволяет указать файл форматирования.|  
|`-k`|Указывает, что пустые столбцы во время данной операции должны сохранить значение NULL вместо любых вставляемых значений столбцов по умолчанию.|  
|`-T`|Указывает, что программа bcp подключается к серверу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используя доверительное соединение.|  
  
 В командной строке Windows введите:  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 in C:\MyTestEmptyField2-c.Dat -f C:\MyTestDefaultCol2-f-c.Fmt -k -T  
  
```  
  
#### <a name="using-bulk-insert-and-keeping-null-values"></a>Сохранение значений NULL при работе с инструкцией BULK INSERT  
 Следующий пример демонстрирует применение параметра KEEPNULLS в операторе BULK INSERT. В средстве выполнения запросов, например в редакторе запросов [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], выполните:  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT MyTestDefaultCol2  
   FROM 'C:\MyTestEmptyField2-c.Dat'  
   WITH (  
      DATAFILETYPE = 'char',  
      FIELDTERMINATOR = ',',  
      KEEPNULLS  
   );  
GO  
  
```  
  
## <a name="keeping-default-values-with-insert--select--from-openrowsetbulk"></a>Хранение значений по умолчанию с помощью инструкции INSERT... SELECT * FROM OPENROWSET (BULK...)  
 По умолчанию все столбцы, не указанные в операции групповой загрузки, устанавливаются в значение NULL путем вставки... SELECT * FROM OPENROWSET (BULK...). Однако можно указать, что для пустого поля в файле данных соответствующий столбец таблицы использует значение по умолчанию (если таковое имеется). Чтобы вставить значения по умолчанию, укажите следующее табличное указание.  
  
|Get-Help|Квалификатор|Тип квалификатора|  
|-------------|---------------|--------------------|  
|Инструкции INSERT ... SELECT * FROM OPENROWSET(BULK...).|WITH(KEEPDEFAULTS)|Табличное указание|  
  
> [!NOTE]  
>  Дополнительные сведения см. в статьях [вставка &#40;Transact-sql&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT &#40;transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)и [табличные указания &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)  
  
### <a name="examples"></a>Примеры  
 Следующая инструкция INSERT... SELECT * FROM OPENROWSET (BULK...) пример выполняет операции по импорту данных и сохраняет значения по умолчанию.  
  
 Чтобы выполнить эти примеры, необходимо создать образец таблицы **MyTestDefaultCol2**, файл данных `MyTestEmptyField2-c.Dat` и использовать файл форматирования `MyTestDefaultCol2-f-c.Fmt`. Дополнительные сведения о создании этих образцов см. в подразделе «Образец таблицы и файла данных» ранее в этом разделе.  
  
 Для второго столбца таблицы (**Col2**) задано значение по умолчанию. Соответствующее поле файла данных содержит пустые строки. При ВСТАВКе... Выбор \* из OPENROWSET (BULK...). Импорт полей этого файла данных в таблицу **MyTestDefaultCol2** по умолчанию значение NULL вставляется в **Col2** вместо значения по умолчанию. В этом случае результат будет выглядеть следующим образом.  
  
||||  
|-|-|-|  
|`1`|`NULL`|`DataField3`|  
|`2`|`NULL`|`DataField3`|  
  
 Чтобы вставить значение по умолчанию `Default value of Col2` вместо значения `NULL`, необходимо использовать табличное указание KEEPDEFAULTS (см. следующий пример). В средстве выполнения запросов, например в редакторе запросов [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], выполните:  
  
```  
USE AdventureWorks;  
GO  
INSERT INTO MyTestDefaultCol2  
    WITH (KEEPDEFAULTS)  
    SELECT *  
      FROM OPENROWSET(BULK  'C:\MyTestEmptyField2-c.Dat',  
      FORMATFILE='C:\MyTestDefaultCol2-f-c.Fmt'       
      ) as t1 ;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
  
-   [Сохранение значений идентификаторов при массовом импорте данных (SQL Server)](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Подготовка данных к массовому экспорту или импорту (SQL Server)](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 **Использование файла форматирования**  
  
-   [Создание файла форматирования (SQL Server)](create-a-format-file-sql-server.md)  
  
-   [Использование файла форматирования для массового импорта данных (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Использование файла форматирования для сопоставления столбцов таблицы с полями файла данных (SQL Server)](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [Использование файла форматирования для пропуска поля данных (SQL Server)](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 **Использование форматов данных для массового импорта или экспорта**  
  
-   [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата для импорта и экспорта данных (SQL Server)](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 **Задание форматов данных для совместимости с помощью программы bcp**  
  
-   [Определение признаков конца поля и строки (SQL Server)](specify-field-and-row-terminators-sql-server.md)  
  
-   [Определение длины префикса в файлах данных с помощью программы bcp (SQL Server)](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [Указание типа файлового хранилища с помощью программы bcp (SQL Server)](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Табличные указания (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
