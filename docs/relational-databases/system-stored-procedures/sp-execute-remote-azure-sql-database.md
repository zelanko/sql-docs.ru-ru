---
title: sp_execute_remote (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 02/01/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sp_execute_remote
- sp_execute_remote_TSQL
helpviewer_keywords:
- remote execution
- queries, remote execution
ms.assetid: ca89aa4c-c4c1-4c46-8515-a6754667b3e5
caps.latest.revision: 17
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 4e80528b6a8ce0e6f470a0fc5fbc0152ee8f8007
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spexecuteremote-azure-sql-database"></a>sp_execute_remote (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Выполняет [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции на одном удаленной базы данных SQL Azure или набор баз данных, которые выступают в качестве сегментов в горизонтальной схемы секционирования.  
  
 Хранимая процедура является частью возможность гибко запроса.  В разделе [Общие сведения о базе данных SQL Azure эластичной базы данных запроса](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/) и [эластичной базы данных запросов для сегментирования (горизонтальное секционирование)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-horizontal-partitioning/).  
  
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
 [ @data_source_name =] *источнику данных*  
 Определяет источник внешних данных, где выполнена инструкция. В разделе [СОЗДАНИЯ ВНЕШНЕГО источника данных &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md). Внешний источник данных может иметь тип «СУРБД» или «SHARD_MAP_MANAGER».  
  
 [ @stmt=] *инструкции*  
 Строка в Юникоде, содержащий [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции или пакета. @stmt должен быть константой или переменной в Юникоде. Более сложные выражения Юникода, например объединение двух строк с помощью оператора +, недопустимы. Символьные константы недопустимы. Если константа в Юникоде указывается, она должна начинаться с префикса **N**. Например, константа Юникода **N 'sp_who'** является допустимым, а символьная константа **'sp_who'** не является. Размер строки ограничивается только доступной серверу баз данных памятью. На 64-разрядных серверах размер строки ограничен 2 ГБ, максимальный размер **nvarchar(max)**.  
  
> [!NOTE]  
>  @stmt может содержать параметры, называющиеся аналогично именам переменных, например: `N'SELECT * FROM HumanResources.Employee WHERE EmployeeID = @IDParameter'`  
  
 Каждый параметр, включенный в аргумент @stmt, должен иметь соответствующую запись в списке определений параметров @params и в списке значений параметров.  
  
 [ @params=] N'@*parameter_name ** data_type* [,... *n* ] "  
 Строка, содержащая определения всех параметров, внедренных в @stmt. Строка должна представлять собой константу в Юникоде либо переменную в этом же формате. Определение каждого параметра состоит из имени параметра и типа данных. *n* — заполнитель, означающий определения дополнительных параметров. Каждый параметр, указанный в @stmtmust определяться в @params. Если инструкция или пакет инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)] в аргументе @stmt не содержат параметров, @params может отсутствовать. Этот аргумент по умолчанию принимает значение NULL.  
  
 [ @param1=] '*значение1*"  
 Значение для первого параметра, определенного в строке параметров. Это значение может быть константой или переменной в Юникоде. Каждому параметру, указанному в @stmt, должно соответствовать значение. Если инструкция или пакет инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] в @stmt не содержат параметров, список значений может отсутствовать.  
  
 *n*  
 Заполнитель для значений дополнительных параметров. Значения могут быть только константами и переменными. Значения не могут представлять собой сложные выражения, такие как функции или выражения, построенные с помощью операторов.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое значение (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующий набор из первой инструкции SQL.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение `ALTER ANY EXTERNAL DATA SOURCE`.  
  
## <a name="remarks"></a>Замечания  
 `sp_execute_remote` параметры должны вводиться в определенном порядке, как описано в разделе "синтаксис" выше. Если параметры вводятся не в этом порядке, будет выдано сообщение об ошибке.  
  
 `sp_execute_remote` ведет себя как [EXECUTE &#40;Transact-SQL&#41; ](../../t-sql/language-elements/execute-transact-sql.md) отношении пакетов и область имен. Выполнение инструкции Transact-SQL или пакета в sp_execute_remote *@stmt* не компилируются до выполнения инструкции sp_execute_remote.  
  
 `sp_execute_remote` добавляет дополнительный столбец с именем «$ShardName», содержащее имя удаленной базы данных, созданных строки результирующего набора.  
  
 `sp_execute_remote` можно использовать аналогично [sp_executesql &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
### <a name="simple-example"></a>Простой пример  
 В следующем примере создается и выполняется простая инструкция SELECT для удаленной базы данных.  
  
```sql  
EXEC sp_execute_remote  
    N'MyExtSrc',  
    N'SELECT COUNT(w_id) AS Count_id FROM warehouse'   
```  
  
### <a name="example-with-multiple-parameters"></a>Пример с несколькими параметрами  
Создайте учетные данные уровня базы данных в базе данных пользователя, указав учетные данные администратора для базы данных master. Создайте источник внешних данных, указывающий на базу данных master и указав учетные данные уровня базы данных. Затем выполняется следующий пример в базе данных пользователей `sp_set_firewall_rule` процедуры в базе данных master. `sp_set_firewall_rule` Процедура требует 3 параметра, а также `@name` параметр как Юникод.

```
EXEC sp_execute_remote @data_source_name  = N'PointToMaster', 
@stmt = N'sp_set_firewall_rule @name, @start_ip_address, @end_ip_address', 
@params = N'@name nvarchar(128), @start_ip_address varchar(50), @end_ip_address varchar(50)',
@name = N'TempFWRule', @start_ip_address = '0.0.0.2', @end_ip_address = '0.0.0.2';
```

## <a name="see-also"></a>См. также:

[СОЗДАНИЕ УРОВНЯ БАЗЫ ДАННЫХ УЧЕТНЫХ ДАННЫХ](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)  
[СОЗДАЙТЕ внешний ИСТОЧНИК данных (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)  
    
