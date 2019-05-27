---
title: Сохранение значений идентификаторов при массовом импорте данных (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- identity values [SQL Server], bulk imports
- data formats [SQL Server], identity values
- bulk importing [SQL Server], identity values
ms.assetid: 45894a3f-2d8a-4edd-9568-afa7d0d3061f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5bb2fbd3129475c5d712cd4d1fce8bbe29ea096f
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66011904"
---
# <a name="keep-identity-values-when-bulk-importing-data-sql-server"></a>Сохранение значений идентификаторов при массовом импорте данных (SQL Server)
  Для файлов данных, содержащих значения идентификаторов, можно выполнить массовый импорт в экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию значения столбца идентификаторов в импортируемом файле данных не учитываются, и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически присваивает им уникальные значения на основе начального значения и значения приращения, указанных при создании таблицы.  
  
 Если файл данных не содержит значений для столбцов идентификаторов в таблице, то для указания того, что при импорте столбец идентификаторов в таблице нужно пропустить, применяется файл форматирования. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически присваивает столбцу уникальные значения.  
  
 Чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не присваивал значения идентификаторов при массовом импорте строк в таблицу, используется соответствующий квалификатор команды для сохранения значений идентификаторов. При указании квалификатора сохранения значений идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользуется значениями идентификаторов, имеющимися в файле данных. Ниже приведены эти квалификаторы.  
  
|Command|Квалификатор сохранения значений идентификаторов|Тип квалификатора|  
|-------------|------------------------------|--------------------|  
|`bcp`|**-E**|Параметр|  
|BULK INSERT|KEEPIDENTITY|Аргумент|  
|Инструкции INSERT ... SELECT * FROM OPENROWSET(BULK...).|KEEPIDENTITY|Табличное указание|  
  
 Дополнительные сведения см. в статьях [Программа bcp](../../tools/bcp-utility.md), [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql), [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql), [INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql), [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) и [Табличные указания (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-table).  
  
> [!NOTE]  
>  Сведения о том, как создать автоматически увеличивающееся числовое значение, которое может использоваться в нескольких таблицах или вызываться из приложений без ссылки на какие-либо таблицы, см. в разделе [Порядковые номера](../sequence-numbers/sequence-numbers.md).  
  
## <a name="examples"></a>Примеры  
 Примеры в этом подразделе выполняют массовый импорт данных при помощи инструкции INSERT ... SELECT * FROM OPENROWSET(BULK...) с сохранением значений по умолчанию.  
  
### <a name="sample-table"></a>Образец таблицы  
 Примеры массового импорта требуют, чтобы в образце базы данных **AdventureWorks** в схеме **dbo** была создана таблица с именем **myTestKeepNulls**. Для создания такой таблицы: В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks;  
GO  
SELECT * INTO HumanResources.myDepartment   
   FROM HumanResources.Department  
      WHERE 1=0;  
GO  
SELECT * FROM HumanResources.myDepartment;  
```  
  
 В таблице **Department**, на которой основана таблица `myDepartment`, IDENTITY_INSERT имеет значение OFF. Поэтому для импорта данных в столбец идентификаторов необходимо указать KEEPIDENTITY или **-E**.  
  
### <a name="sample-data-file"></a>Образец файла данных  
 Файл данных, который используется в примерах массового импорта, содержит данные, экспортированные из таблицы `HumanResources.Department` в собственном формате. Для создания файла данных введите в командной строке [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows:  
  
```  
bcp AdventureWorks.HumanResources.Department out myDepartment-n.Dat -n -T  
```  
  
### <a name="sample-format-file"></a>Образец файла форматирования  
 В этих примерах массового импорта применяется XML-файл форматирования `myDepartment-f-x-n.Xml`, использующий собственные форматы данных. В этом примере `bcp` используется для создания данного файла форматирования из таблицы `HumanResources.Department` базы данных `AdventureWorks`. В командной строке Windows введите:  
  
```  
bcp AdventureWorks.HumanResources.Department format nul -n -x -f myDepartment-f-n-x.Xml -T  
```  
  
 Дополнительные сведения о создании файла форматирования см. в разделе [Создание файла форматирования (SQL Server)](create-a-format-file-sql-server.md).  
  
### <a name="a-using-bcp-and-keeping-identity-values"></a>A. Использование команды bcp с сохранением значений идентификаторов  
 В следующем примере показан способ сохранения значений идентификаторов при использовании команды `bcp` для массового импорта данных. Команда `bcp` использует файл форматирования `myDepartment-f-n-x.Xml` и содержит следующие параметры:  
  
|Квалификаторы|Описание|  
|----------------|-----------------|  
|**-E**|Указывает, что в столбец идентификаторов загружаются значения идентификаторов, находящиеся в файле данных.|  
|**-T**|Указывает, что `bcp` программа устанавливает соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используя доверительное соединение.|  
  
 В командной строке Windows введите:  
  
```  
bcp AdventureWorks.HumanResources.myDepartment in C:\myDepartment-n.Dat -f C:\myDepartment-f-n-x.Xml -E -T  
  
```  
  
### <a name="b-using-bulk-insert-and-keeping-identity-values"></a>Б. Использование BULK INSERT с сохранением значений идентификаторов  
 В следующем примере BULK INSERT используется для массового импорта данных из файла `myDepartment-c.Dat` в таблицу `AdventureWorks.HumanResources.myDepartment` . Инструкция использует файл форматирования `myDepartment-f-n-x.Xml` и включает параметр KEEPIDENTITY для сохранения значений идентификаторов, находящихся в файле данных.  
  
 В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
BULK INSERT HumanResources.myDepartment  
   FROM 'C:\myDepartment-n.Dat'  
   WITH (  
      KEEPIDENTITY,  
      FORMATFILE='C:\myDepartment-f-n-x.Xml'  
   );  
GO  
SELECT * FROM HumanResources.myDepartment;  
  
```  
  
### <a name="c-using-openrowset-and-keeping-identity-values"></a>В. Использование OPENROWSET с сохранением значений идентификаторов  
 В следующем примере поставщик наборов строк OPENROWSET используется для массового импорта данных из файла `myDepartment-c.Dat` в таблицу `AdventureWorks.HumanResources.myDepartment` . Инструкция использует файл форматирования `myDepartment-f-n-x.Xml` и включает указание KEEPIDENTITY для сохранения всех значений идентификаторов, содержащихся в файле данных.  
  
 В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] выполните:  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
  
INSERT INTO HumanResources.myDepartment  
   with (KEEPIDENTITY)  
   (DepartmentID, Name, GroupName, ModifiedDate)  
   SELECT *  
      FROM  OPENROWSET(BULK 'C:\myDepartment-n.Dat',  
      FORMATFILE='C:\myDepartment-f-n-x.Xml') as t1;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
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
  
1.  [Определение признаков конца поля и строки (SQL Server)](specify-field-and-row-terminators-sql-server.md)  
  
2.  [Определение длины префикса в файлах данных с помощью программы bcp (SQL Server)](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [Указание типа файлового хранилища с помощью программы bcp (SQL Server)](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a>См. также  
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [Табличные указания (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
