---
title: Изменение функции секционирования | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: ae5bfc09-f27a-4ea9-9518-485278b11674
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7cc06db0cf02a5d2e85b4e49a778f5484446b9be
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51640761"
---
# <a name="modify-a-partition-function"></a>Изменение функции секционирования
  Вы можете изменить способ секционирования таблицы или индекса в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] путем увеличения или уменьшения указанного числа секций с шагом 1 в функции секционирования секционированной таблицы или индекса при помощи [!INCLUDE[tsql](../../includes/tsql-md.md)]. Добавление секции осуществляется путем разбиения существующей секции на две и переопределением границ новых секций. Удаление секции происходит путем слияния двух секций в одну на границе. Это действие повторно заполняет одну секцию и оставляет другую незаполненной.  
  
> [!CAUTION]  
>  Несколько таблиц или индексов могут использовать одинаковую функцию секционирования. При изменении функции секционирования затрагиваются все таблицы и индексы в одной транзакции. Проверьте зависимости функции секционирования перед внесением изменений.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Изменение функции секционирования при помощи:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Инструкция ALTER PARTITION FUNCTION может использоваться только для разделения одной секции на две или для слияния двух секций в одну. Чтобы изменить способ секционирование таблиц или индексов (например, с 10 секций до 5), вы можете использовать один из следующих вариантов.  
  
    -   Создайте новую секционированную таблицу с необходимой функцией секционирования, затем вставьте данные из старой таблицы в новую при помощи инструкции INSERT INTO... SELECT FROM [!INCLUDE[tsql](../../includes/tsql-md.md)] или воспользуйтесь **Мастером управления секциями** в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
    -   Создайте секционированный кластеризованный индекс по всей куче.  
  
        > [!NOTE]  
        >  Удаление результатов секционированного кластеризованного индекса в секционированной куче.  
  
    -   Удалите и заново создайте существующий секционированный индекс с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX с предложением DROP EXISTING = ON.  
  
    -   Выполните последовательность инструкций ALTER PARTITION FUNCTION.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает репликацию для изменения функций секционирования. Если нужно внести изменения в функцию секционирования в базе данных публикации, необходимо сделать это вручную и в базе данных подписки.  
  
-   Все файловые группы, на которые влияет инструкция ALTER PARTITION FUNCTION необходимо подключиться к Интернету.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для выполнения инструкции ALTER PARTITION FUNCTION может использоваться одно из перечисленных ниже разрешений.  
  
-   Разрешение ALTER ANY DATASPACE. Это разрешение назначено по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенных ролей базы данных **db_owner** и **db_ddladmin**.  
  
-   Разрешение CONTROL или ALTER в базе данных, в которой была создана функция секционирования.  
  
-   Разрешение CONTROL SERVER или ALTER ANY DATABASE на сервере базы данных, в которой была создана функция секционирования.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Изменение функции секционирования**  
  
 Это действие не может быть выполнено при помощи [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Чтобы изменить функцию секционирования, необходимо сначала удалить функцию, после чего создать новую с нужными свойствами при помощи мастера создания секций. Дополнительные сведения см. в разделе  
  
#### <a name="to-delete-a-partition-function"></a>Удаление функции секционирования  
  
1.  Разверните базу данных, на которой требуется удалить функцию секционирования, а затем разверните папку **Хранение** .  
  
2.  Разверните папку **Функции секционирования** .  
  
3.  Щелкните правой кнопкой мыши функцию секционирования, которую нужно удалить, и выберите пункт **Удалить**.  
  
4.  В диалоговом окне **Удаление объекта** убедитесь, что выбрана верная функция секционирования, и нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-split-a-single-partition-into-two-partitions"></a>Разбиение одной секции на две  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Look for a previous version of the partition function “myRangePF1” and deletes it if it is found.  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
        DROP PARTITION FUNCTION myRangePF1;  
    GO  
    -- Create a new partition function called “myRangePF1” that partitions a table into four partitions.  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    --Split the partition between boundary_values 100 and 1000  
    --to create two partitions between boundary_values 100 and 500  
    --and between boundary_values 500 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    SPLIT RANGE (500);  
    ```  
  
#### <a name="to-merge-two-partitions-into-one-partition"></a>Слияние двух секций в одну  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Look for a previous version of the partition function “myRangePF1” and deletes it if it is found.  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
        DROP PARTITION FUNCTION myRangePF1;  
    GO  
    -- Create a new partition function called “myRangePF1” that partitions a table into four partitions.  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    --Merge the partitions between boundary_values 1 and 100  
    --and between boundary_values 100 and 1000 to create one partition  
    --between boundary_values 1 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    MERGE RANGE (100);  
    ```  
  
 Дополнительные сведения см. в статье [ALTER PARTITION FUNCTION (Transact-SQL)](/sql/t-sql/statements/alter-partition-function-transact-sql).  
  
  
