---
title: "Использование файла форматирования для пропуска столбца таблицы (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 08/05/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: import-export
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-bulk-import-export
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- skipping columns when importing
- format files [SQL Server], skipping columns
ms.assetid: 30e0e7b9-d131-46c7-90a4-6ccf77e3d4f3
caps.latest.revision: "50"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0603aa186c900e60cc17bc388d439738fd41a95a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="use-a-format-file-to-skip-a-table-column-sql-server"></a>Пропуск столбца таблицы с помощью файла форматирования (SQL Server)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] В этом разделе описываются файлы форматирования. Если поле не существует в файле данных, то импорт столбца таблицы можно пропустить с помощью файла форматирования. Файл данных может содержать меньше полей, чем таблица столбцов, только если пропущенные столбцы необязательно определяемы и (или) имеют значение по умолчанию.  
  
## <a name="sample-table-and-data-file"></a>Образец таблицы и файла данных  
 Для следующих примеров требуется таблица с именем `myTestSkipCol` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] схемы **dbo** . Создайте таблицу следующим образом:  
  
```sql
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestSkipCol   
   (  
   Col1 smallint,  
   Col2 nvarchar(50) NULL,  
   Col3 nvarchar(50) not NULL  
   );  
GO  
```  
  
 В примерах, приведенных ниже, используется образец файла данных `myTestSkipCol2.dat`, который содержит только два поля, в то время как в соответствующей таблице три столбца:  
  
```  
1,DataForColumn3  
1,DataForColumn3  
1,DataForColumn3  
```  
  
 Чтобы выполнить массовый импорт данных из таблицы `myTestSkipCol2.dat` в таблицу `myTestSkipCol` , файл форматирования должен сопоставлять первое поле данных с `Col1`, а второе поле данных с `Col3`, пропуская поле `Col2`.  
  
## <a name="using-a-non-xml-format-file"></a>Использование файла форматирования в формате, отличном от XML  
 Чтобы пропустить столбец таблицы, можно изменить файл форматирования в формате, отличном от XML. Обычно при этом используется служебная программа **bcp** (для создания файла форматирования по умолчанию в формате, отличном от XML) и в текстовом редакторе изменяется файл по умолчанию. Измененный файл форматирования должен сопоставлять все существующие поля соответствующим столбцам таблицы и указывать, какие столбцы или столбец таблицы пропускать. Есть два варианта изменения файлов форматирования в формате, отличном от XML по умолчанию. В одном случае поле данных не существует в файле данных, и в соответствующий столбец таблицы не будут записаны никакие данные.  
  
### <a name="creating-a-default-non-xml-format-file"></a>Создание файла форматирования в формате, отличном от XML, по умолчанию  
 В этой статье используется файл форматирования по умолчанию в формате, отличном от XML, созданный для образца таблицы `myTestSkipCol` с помощью следующей команды **bcp** :  
  
```cmd
bcp AdventureWorks2012..myTestSkipCol format nul -f myTestSkipCol_Default.fmt -c -T  
```  
  
 Предыдущая команда создает файл форматирования в формате, отличном от XML, `myTestSkipCol_Default.fmt`. Этот файл называется *файлом форматирования по умолчанию* , так как представляет собой форму, созданную командой **bcp**. Обычно файл форматирования по умолчанию описывает сопоставления один к одному между полями файла данных и столбцами таблицы.  
  
> [!IMPORTANT]  
>  Необходимо указать имя экземпляра сервера, с которым осуществляется соединение. Возможно также потребуется указать имя пользователя и пароль. Дополнительные сведения см. в разделе [bcp Utility](../../tools/bcp-utility.md).  
  
 Следующая иллюстрация показывает значения в образцах файлов форматирования по умолчанию. Иллюстрация также показывает имя каждого поля файла форматирования.  
  
 ![Файл форматирования по умолчанию для myTestSkipCol, в формате, отличном от XML](../../relational-databases/import-export/media/mytestskipcol-f-c-default-fmt.gif "Файл форматирования по умолчанию для myTestSkipCol, в формате, отличном от XML")  
  
> [!NOTE]  
>  Дополнительные сведения о файлах форматирования в формате, отличном от XML, см. в разделе [Файлы формата, отличные от XML (SQL Server)](../../relational-databases/import-export/non-xml-format-files-sql-server.md).  
  
### <a name="methods-for-modifying-a-non-xml-format-file"></a>Методы изменения файла форматирования в формате, отличном от XML  
 Чтобы пропустить столбец таблицы, отредактируйте файл форматирования в формате, отличном от XML, и измените файл с помощью одного из следующих вариантов.  
  
-   Рекомендуемый метод состоит из трех основных шагов. Сначала удалите все строки файла форматирования, описывающие пропущенные в файле данных поля. Затем уменьшите значение «порядкового номера поля в файле данных» каждой строки файла форматирования, которая следует за удаленной строкой. Целью являются последовательные значения "порядкового номера поля в файле данных", от 1 до *n*, которые отражают действительную позицию каждого поля данных в файле данных. Наконец, уменьшите значение в поле «Число столбцов» до действительного числа полей в файле данных.  
  
     Следующий пример основан на файле форматирования по умолчанию для таблицы `myTestSkipCol` , создаваемой в подразделе «Создание файла форматирования в формате, отличном от XML» ранее в этом разделе. Этот измененный файл форматирования сопоставляет первое поле данных полю `Col1`, пропускает поле `Col2`и сопоставляет второе поле данных `Col3`. Строка для поля `Col2` была удалена.  
  
    ```  
    9.0  
    2  
    1       SQLCHAR       0       7       "\t"     1     Col1         ""  
    2       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS  
    ```  
  
-   В качестве альтернативы, чтобы пропустить столбец таблицы, можно изменить определение строки файла форматирования, которая соответствует этому столбцу таблицы. В этой строке файла форматирования значения «длина префикса», «длина данных файла узла» и «порядковый номер столбца на сервере» должны быть равны 0. Также должны быть установлены в значение « » (NULL) поля «признак конца» и «параметры сортировки столбца».  
  
     Для значения поля «порядковый номер столбца на сервере» необходима непустая строка, хотя действительное имя столбца не требуется. Для оставшихся полей форматирования требуются значения по умолчанию.  
  
     Следующий пример основан на файле форматирования по умолчанию для таблицы `myTestSkipCol` .  
  
    ```  
    9.0  
    3  
    1       SQLCHAR       0       7       "\t"     1     Col1         ""  
    2       SQLCHAR       0       0       ""       0     Col2         ""  
    3       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS  
    ```  
  
### <a name="examples"></a>Примеры  
 Следующие примеры также базируются на образце таблицы `myTestSkipCol` и образце файла данных `myTestSkipCol2.dat` , созданных в подразделе «Образец таблицы и файла данных» ранее в этом разделе.  
  
#### <a name="using-bulk-insert"></a>Использование предложения BULK INSERT  
 Следующий пример работает с использованием любого из файлов форматирования, отличных от XML и создаваемых в подразделе «Методы изменения не XML-файла форматирования» ранее в этом разделе. В этом примере измененный файл форматирования называется `C:\myTestSkipCol2.fmt`. Чтобы использовать `BULK INSERT` для массового импорта файла данных `myTestSkipCol2.dat` , в редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните следующий код:  
  
```sql  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestSkipCol   
   FROM 'C:\myTestSkipCol2.dat'   
   WITH (FORMATFILE = 'C:\myTestSkipCol2.fmt');  
GO  
SELECT * FROM myTestSkipCol;  
GO  
```  
  
## <a name="using-an-xml-format-file"></a>Использование XML-файла форматирования  
 Если для импорта непосредственно в таблицу используется XML-файл форматирования, с помощью команды **bcp** или инструкции BULK INSERT столбец пропустить нельзя. Однако можно выполнить импорт всех столбцов таблицы, кроме последнего. Если нужно пропустить все столбцы, кроме последнего, необходимо создать представление целевой таблицы, содержащее только столбцы из файла данных. После этого можно выполнить массовый импорт данных из этого файла в представление.  
  
 Чтобы пропустить столбец таблицы с помощью XML-файла форматирования с помощью инструкции OPENROWSET(BULK...), необходимо следующим образом подставить явный список столбцов в список выбора и в целевую таблицу:  
  
 INSERT ...<список_столбцов> SELECT <список_столбцов> FROM OPENROWSET(BULK...)  
  
### <a name="creating-a-default-xml-format-file"></a>Создание XML-файла форматирования по умолчанию  
 Следующие примеры измененных файлов форматирования базируются на образце таблицы `myTestSkipCol` и файла данных, созданных в подразделе «Образец таблицы и файла данных» ранее в этом разделе. Следующая команда **bcp`myTestSkipCol` создает XML-файл форматирования по умолчанию для таблицы** .  
  
```cmd
bcp AdventureWorks2012..myTestSkipCol format nul -f myTestSkipCol_Default.xml -c -x -T  
```  
  
 Результирующий файл форматирования в формате, отличном от XML, описывает сопоставления один к одному между полями файла данных и столбцами таблицы следующим образом:  
  
```xml
\<?xml version="1.0"?>  
\<BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  \<FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="7"/>  
  \<FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  \<FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  \<COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  \<COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  \<COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  Сведения о структуре файлов форматирования XML см. в разделе [Файлы формата XML (SQL Server)](../../relational-databases/import-export/xml-format-files-sql-server.md).  
  
### <a name="examples"></a>Примеры  
 В примерах этого раздела используется образец таблицы `myTestSkipCol` и образец файла данных `myTestSkipCol2.dat` , создаваемых в подразделе «Образец таблицы и файла данных» ранее в этом разделе. Для импортирования данных из файла `myTestSkipCol2.dat` в таблицу `myTestSkipCol` в примерах используется следующий измененный XML-файл форматирования `myTestSkipCol2-x.xml`. Следующий пример основан на файле форматирования, создаваемом в подразделе «Создание не XML-файла форматирования по умолчанию» ранее в этом разделе.  
  
```xml
\<?xml version="1.0"?>  
\<BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  \<FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  \<FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  \<COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  \<COLUMN SOURCE="2" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
#### <a name="using-openrowsetbulk"></a>Применение инструкции OPENROWSET(BULK...)  
 В следующем примере используется поставщик массового набора строк `OPENROWSET` и файл форматирования `myTestSkipCol2.xml` . В примере выполняется массовый импорт файла данных `myTestSkipCol2.dat` в таблицу `myTestSkipCol` . Инструкция, в соответствии с требованиями, содержит явный список столбцов в списке выбора, а также в целевой таблице.  
  
 В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните:  
  
```sql  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipCol  
  (Col1,Col3)  
    SELECT Col1,Col3  
      FROM  OPENROWSET(BULK  'C:\myTestSkipCol2.Dat',  
      FORMATFILE='C:\myTestSkipCol2.Xml'    
       ) as t1 ;  
GO  
```  
  
#### <a name="using-bulk-import-on-a-view"></a>Использование инструкции BULK IMPORT на представлениях  
 В следующем примере создается представление `v_myTestSkipCol` для таблицы `myTestSkipCol` . В этом представлении пропущен второй столбец таблицы `Col2`. Затем применяется инструкция `BULK INSERT` для импорта файла данных `myTestSkipCol2.dat` в это представление.  
  
 В редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выполните:  
  
```sql  
CREATE VIEW v_myTestSkipCol AS  
    SELECT Col1,Col3  
    FROM myTestSkipCol;  
GO  
  
USE AdventureWorks2012;  
GO  
BULK INSERT v_myTestSkipCol  
FROM 'C:\myTestSkipCol2.dat'  
WITH (FORMATFILE='C:\myTestSkipCol2.xml');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [Использование файла форматирования для пропуска поля данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-skip-a-data-field-sql-server.md)   
 [Использование файла форматирования для сопоставления столбцов таблицы полям файла данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)   
 [Использование файла форматирования для массового импорта данных (SQL Server)](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
  
