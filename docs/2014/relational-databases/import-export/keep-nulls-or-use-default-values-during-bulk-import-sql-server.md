---
title: Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server) | Документация Майкрософт
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
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7840877066f5f941050d96c3274ab7bf6698326c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192888"
---
# <a name="keep-nulls-or-use-default-values-during-bulk-import-sql-server"></a>Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)
  При импорте данных в таблицу команда **bcp** и инструкция BULK INSERT используют значения по умолчанию, которые определены для столбцов таблицы. Например, если поле в файле данных имеет значение NULL, вместо него загружается значение по умолчанию соответствующего столбца. И команда **bcp**, и инструкция BULK INSERT позволяют пользователю указать, следует ли оставлять значения NULL.  
  
 Обычная инструкция INSERT, напротив, оставляет значение NULL и не использует значения по умолчанию. Инструкция INSERT ... Инструкция SELECT * FROM OPENROWSET(BULK...) ведет себя так же, как обычная инструкция INSERT, но поддерживает табличное указание для загрузки значений по умолчанию.  
  
> [!NOTE]  
>  Пример файла форматирования, пропускающего столбец таблицы, см. в статье [Пропуск столбца таблицы с помощью файла форматирования (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md).  
  
## <a name="sample-table-and-data-file"></a>Образец таблицы и файла данных  
 Для выполнения примеров этого подраздела необходимо создать образец таблицы и файла данных.  
  
### <a name="sample-table"></a>Образец таблицы  
 Для выполнения примеров этого раздела требуется создать таблицу **MyTestDefaultCol2** в образце базы данных **AdventureWorks** в схеме **dbo**. Для создания этой таблицы в редакторе запросов среды [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните следующий код:  
  
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
  
|Command|Квалификатор|Тип квалификатора|  
|-------------|---------------|--------------------|  
|**bcp**|`-k`|Параметр|  
|BULK INSERT|KEEPNULLS<sup>1</sup>|Аргумент|  
  
 <sup>1</sup> для инструкции BULK INSERT, если значения по умолчанию недоступны, столбец таблицы должен быть определен допустимы значения null.  
  
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
  
 Для вставки»`NULL`«вместо «»`Default value of Col2`«, необходимо использовать `-k` или параметр KEEPNULL, как показано в следующем **bcp** и примеры инструкции BULK INSERT.  
  
#### <a name="using-bcp-and-keeping-null-values"></a>Сохранение значений NULL при работе с командой bcp  
 Следующий пример демонстрирует, как сохранить значения NULL при использовании команды **bcp**. Команда **bcp** поддерживает следующие параметры.  
  
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
  
## <a name="keeping-default-values-with-insert--select--from-openrowsetbulk"></a>Использование инструкции INSERT ... для сохранения значений по умолчанию SELECT * FROM OPENROWSET(BULK...).  
 По умолчанию инструкция INSERT ... SELECT * FROM OPENROWSET(BULK...) присваивает значение NULL любым столбцам, не участвующим в операции массового импорта. SELECT * FROM OPENROWSET(BULK...). Тем не менее можно указать, что вместо пустых значений необходимо вставить значения по умолчанию соответствующих столбцов (если оно задано). Чтобы вставить значения по умолчанию, укажите следующее табличное указание.  
  
|Command|Квалификатор|Тип квалификатора|  
|-------------|---------------|--------------------|  
|Инструкции INSERT ... SELECT * FROM OPENROWSET(BULK...).|WITH(KEEPDEFAULTS)|Табличное указание|  
  
> [!NOTE]  
>  Дополнительные сведения см. в статьях [INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql), [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql), [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) и [Табличные указания (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-table).  
  
### <a name="examples"></a>Примеры  
 В следующем примере инструкция INSERT ... SELECT * FROM OPENROWSET(BULK...) производит массовый импорт данных и вставляет значения по умолчанию.  
  
 Чтобы выполнить эти примеры, необходимо создать образец таблицы **MyTestDefaultCol2**, файл данных `MyTestEmptyField2-c.Dat` и использовать файл форматирования `MyTestDefaultCol2-f-c.Fmt`. Дополнительные сведения о создании этих образцов см. в подразделе «Образец таблицы и файла данных» ранее в этом разделе.  
  
 Для второго столбца таблицы (**Col2**) задано значение по умолчанию. Соответствующее поле файла данных содержит пустые строки. При использовании инструкции INSERT ... SELECT \* FROM OPENROWSET(BULK...) для импорта полей из этого файла данных в таблицу **MyTestDefaultCol2**, по умолчанию в столбец **Col2** вместо значений по умолчанию будут вставлены значения NULL. В этом случае результат будет выглядеть следующим образом.  
  
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
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Сохранение значений идентификаторов при массовом импорте данных (SQL Server)](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Подготовка данных к массовому экспорту или импорту (SQL Server)](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 **Использование файла форматирования**  
  
-   [Создание файла форматирования (SQL Server)](create-a-format-file-sql-server.md)  
  
-   [Использование файла форматирования для массового импорта данных (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Использование файла форматирования для сопоставления столбцов таблицы полям файла данных (SQL Server)](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [Использование файла форматирования для пропуска поля данных (SQL Server)](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Использование файла форматирования для пропуска столбца таблицы (SQL Server)](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
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
  
## <a name="see-also"></a>См. также  
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [Программа bcp](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Табличные указания (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
