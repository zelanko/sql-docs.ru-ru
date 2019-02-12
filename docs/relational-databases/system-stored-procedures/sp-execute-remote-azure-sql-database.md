---
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
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: a475ba50aa8d3ba140ea551306d8b9f17fe66d22
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56035905"
---
# <a name="spexecuteremote-azure-sql-database"></a>sp_execute_remote (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Выполняет [!INCLUDE[tsql](../../includes/tsql-md.md)] оператором в единый удаленной базы данных SQL Azure или набора баз данных, выступающих в качестве сегментов в схеме горизонтального секционирования.  
  
 Хранимая процедура является частью функция эластичных запросов.  См. в разделе [Обзор запроса эластичной базы данных для базы данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/) и [запросов эластичной базы данных для сегментирования (горизонтальное секционирование)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-horizontal-partitioning/).  
  
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
 [ \@data_source_name =] *datasourcename*  
 Идентифицирует источник внешних данных, где выполняется инструкция. См. в разделе [создать внешний ИСТОЧНИК данных &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md). Внешний источник данных может быть типа «Реляционной СУБД» или «SHARD_MAP_MANAGER».  
  
 [ \@stmt =] *инструкции*  
 Строка в Юникоде, содержащий [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции или пакета. \@stmt должен быть константой или переменной в Юникоде. Более сложные выражения Юникода, например объединение двух строк с помощью оператора +, недопустимы. Символьные константы недопустимы. Если указана константа Юникода, он должен начинаться с префикса **N**. Например, константа Юникода **N 'sp_who'** является допустимым, а символьная константа **'sp_who'** не является. Размер строки ограничивается только доступной серверу баз данных памятью. На 64-разрядных серверах, размер строки ограничен 2 ГБ, максимальный размер **nvarchar(max)**.  
  
> [!NOTE]  
>  \@stmt может содержать параметры, называющиеся аналогично как имя переменной, например: `N'SELECT * FROM HumanResources.Employee WHERE EmployeeID = @IDParameter'`  
  
 Каждый параметр, включенный в \@stmt должен иметь соответствующую запись в \@список определений параметров params, а параметр списка значений.  
  
 [ \@params =] N'\@*parameter_name ** data_type* [,... *n* ] "  
 Строка, содержащая определения всех параметров, внедренных в \@stmt. Строка должна представлять собой константу в Юникоде либо переменную в этом же формате. Определение каждого параметра состоит из имени параметра и типа данных. *n* — заполнитель, указывающий Дополнительные определения параметра. Каждый параметр, указанный в \@stmtmust определяться в \@params. Если [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкция или пакет в \@stmt не содержит параметров, \@params не является обязательным. Этот аргумент по умолчанию принимает значение NULL.  
  
 [ \@param1 =] '*значение1*"  
 Значение для первого параметра, определенного в строке параметров. Это значение может быть константой или переменной в Юникоде. Должно быть значение параметра, предоставленные каждому параметру в \@stmt. Значения не являются обязательными при [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкция или пакет в \@stmt не имеет параметров.  
  
 *n*  
 Заполнитель для значений дополнительных параметров. Значения могут быть только константами и переменными. Значения не могут представлять собой сложные выражения, такие как функции или выражения, построенные с помощью операторов.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое значение (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующий набор из первой инструкции SQL.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение `ALTER ANY EXTERNAL DATA SOURCE`.  
  
## <a name="remarks"></a>Примечания  
 `sp_execute_remote` параметры должны вводиться в определенном порядке, как описано в разделе "синтаксис" выше. Если параметры вводятся не в этом порядке, будет выдано сообщение об ошибке.  
  
 `sp_execute_remote` действует так же, как [EXECUTE &#40;Transact-SQL&#41; ](../../t-sql/language-elements/execute-transact-sql.md) отношении пакетов и область имен. Инструкции Transact-SQL или пакет в sp_execute_remote  *\@stmt* не компилируются до выполнения инструкции sp_execute_remote.  
  
 `sp_execute_remote` добавляет дополнительный столбец с именем «$ShardName», содержащая имя удаленной базы данных, которая является создателем строки результирующего набора.  
  
 `sp_execute_remote` можно использовать аналогичную [sp_executesql &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
### <a name="simple-example"></a>Простой пример  
 Следующий пример создает и выполняет простой инструкции SELECT для удаленной базы данных.  
  
```sql  
EXEC sp_execute_remote  
    N'MyExtSrc',  
    N'SELECT COUNT(w_id) AS Count_id FROM warehouse'   
```  
  
### <a name="example-with-multiple-parameters"></a>Пример с несколькими параметрами  
Создайте учетные данные уровня базы данных в базу данных пользователя, указав учетные данные администратора для базы данных master. Создание внешнего источника данных указывает на базе данных master и указав учетные данные уровня базы данных. А затем выполняет следующую команду, в примере в базе данных пользователя, `sp_set_firewall_rule` процедуры в базе данных master. `sp_set_firewall_rule` Процедура требует 3 параметра, а `@name` параметр будет в Юникоде.

```
EXEC sp_execute_remote @data_source_name  = N'PointToMaster', 
@stmt = N'sp_set_firewall_rule @name, @start_ip_address, @end_ip_address', 
@params = N'@name nvarchar(128), @start_ip_address varchar(50), @end_ip_address varchar(50)',
@name = N'TempFWRule', @start_ip_address = '0.0.0.2', @end_ip_address = '0.0.0.2';
```

## <a name="see-also"></a>См. также:

[СОЗДАНИЕ ДАННЫХ ДЛЯ БАЗЫ ДАННЫХ УЧЕТНЫХ ДАННЫХ](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)  
[CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)  
    
