---
description: sp_execute_remote (база данных SQL Azure)
title: sp_execute_remote (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 02/01/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sp_execute_remote
- sp_execute_remote_TSQL
helpviewer_keywords:
- remote execution
- queries, remote execution
ms.assetid: ca89aa4c-c4c1-4c46-8515-a6754667b3e5
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 1642baedb44cc6eab4474616d03abd2f429f4276
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447169"
---
# <a name="sp_execute_remote-azure-sql-database"></a>sp_execute_remote (база данных SQL Azure)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  Выполняет [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкцию в одной удаленной базе данных SQL Azure или наборе баз данных, служащих в качестве сегментов в схеме горизонтального секционирования.  
  
 Хранимая процедура является частью функции эластичных запросов.  См. раздел [Общие сведения о запросах эластичной базы данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/) и [запросы эластичной базы данных для сегментирования (горизонтальное секционирование)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-horizontal-partitioning/).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_execute_remote [ @data_source_name = ] datasourcename  
[ , @stmt = ] statement  
[   
  { , [ @params = ] N'@parameter_name data_type [,...n ]' }   
     { , [ @param1 = ] 'value1' [ ,...n ] }  
]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ \@ data_source_name =] идентификатор *источника*  
 Определяет внешний источник данных, в котором выполняется инструкция. См. раздел [CREATE External Data SOURCE &#40;&#41;Transact-SQL ](../../t-sql/statements/create-external-data-source-transact-sql.md). Внешний источник данных может иметь тип "RDBMS" или "SHARD_MAP_MANAGER".  
  
 [ \@ stmt =], *инструкция*  
 Строка в Юникоде, содержащая [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкцию или пакет. \@значение stmt должно быть константой Юникода или переменной Юникода. Более сложные выражения Юникода, например объединение двух строк с помощью оператора +, недопустимы. Символьные константы недопустимы. Если константа Юникода указана, она должна иметь префикс **N**. Например, константа в Юникоде **N "sp_who"** допустима, но символьная константа **"sp_who"** не является. Размер строки ограничивается только доступной серверу баз данных памятью. На 64-разрядных серверах размер строки ограничен 2 ГБ, максимальный размер — **nvarchar (max)**.  
  
> [!NOTE]  
>  \@stmt может содержать параметры, имеющие ту же форму, что и имя переменной, например: `N'SELECT * FROM HumanResources.Employee WHERE EmployeeID = @IDParameter'`  
  
 Каждый параметр, входящий в \@ stmt, должен иметь соответствующую запись в \@ списке определений параметров params и в списке значений параметров.  
  
 [ \@ params =] N ' \@ *parameter_name * * data_type* [,... *n* ] "  
 — Это одна строка, содержащая определения всех параметров, внедренных в \@ stmt. Строка должна быть либо константой Юникода, либо переменной Юникода. Определение каждого параметра состоит из имени параметра и типа данных. *n* — это заполнитель, указывающий дополнительные определения параметров. Каждый параметр, указанный в \@ стмтмуст, должен быть определен в \@ параметре params. Если [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкция или пакет в \@ stmt не содержит параметров, \@ params не требуется. Этот аргумент по умолчанию принимает значение NULL.  
  
 [ \@ param1 =] '*Значение1*'  
 Значение для первого параметра, определенного в строке параметров. Это значение может быть константой или переменной в Юникоде. Для каждого параметра, входящего в stmt, должно быть указано значение параметра \@ . Значения не требуются, если [!INCLUDE[tsql](../../includes/tsql-md.md)] в инструкции или пакете в \@ stmt нет параметров.  
  
 *n*  
 Заполнитель для значений дополнительных параметров. Значения могут быть только константами и переменными. Значения не могут представлять собой сложные выражения, такие как функции или выражения, построенные с помощью операторов.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое значение (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующий набор из первой инструкции SQL.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение `ALTER ANY EXTERNAL DATA SOURCE`.  
  
## <a name="remarks"></a>Комментарии  
 `sp_execute_remote` параметры должны быть указаны в определенном порядке, как описано в разделе синтаксис выше. Если параметры вводятся не в этом порядке, будет выдано сообщение об ошибке.  
  
 `sp_execute_remote` поведение аналогично [выполнению &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md) в отношении пакетов и области имен. Инструкция или пакет Transact-SQL в параметре sp_execute_remote * \@ stmt* не компилируются до тех пор, пока не будет выполнена инструкция sp_execute_remote.  
  
 `sp_execute_remote` добавляет дополнительный столбец к результирующему набору с именем "$ShardName", который содержит имя удаленной базы данных, которая создала строку.  
  
 `sp_execute_remote` может использоваться аналогично [sp_executesql &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
### <a name="simple-example"></a>Простой пример  
 В следующем примере создается и выполняется простая инструкция SELECT для удаленной базы данных.  
  
```sql  
EXEC sp_execute_remote  
    N'MyExtSrc',  
    N'SELECT COUNT(w_id) AS Count_id FROM warehouse'   
```  
  
### <a name="example-with-multiple-parameters"></a>Пример с несколькими параметрами  
Создайте учетные данные уровня базы данных в пользовательской базе данных, указав учетные данные администратора для базы данных master. Создайте внешний источник данных, указывающий на базу данных master, и укажите учетные данные области базы данных. Затем, например, в пользовательской базе данных выполняется `sp_set_firewall_rule` процедура в базе данных master. `sp_set_firewall_rule`Процедура требует 3 параметра и требует, `@name` чтобы параметр был в Юникоде.

```
EXEC sp_execute_remote @data_source_name  = N'PointToMaster', 
@stmt = N'sp_set_firewall_rule @name, @start_ip_address, @end_ip_address', 
@params = N'@name nvarchar(128), @start_ip_address varchar(50), @end_ip_address varchar(50)',
@name = N'TempFWRule', @start_ip_address = '0.0.0.2', @end_ip_address = '0.0.0.2';
```

## <a name="see-also"></a>См. также:

[CREATE DATABASE SCOPED CREDENTIAL](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)  
[CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)  
    
