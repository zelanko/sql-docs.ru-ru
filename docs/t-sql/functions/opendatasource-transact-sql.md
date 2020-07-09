---
title: OPENDATASOURCE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/26/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- OPENDATASOURCE
- OPENDATASOURCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data sources [SQL Server]
- OPENDATASOURCE function
- remote data access [SQL Server], OPENDATASOURCE
- ad hoc distributed queries
- OLE DB data sources [SQL Server]
- ad hoc connection information
ms.assetid: 5510b846-9cde-4687-8798-be9a273aad31
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: a7b4aa391f3b8f8822b65142417031ad21af9669
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85882460"
---
# <a name="opendatasource-transact-sql"></a>OPENDATASOURCE (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Передает сведения о нерегламентированном соединении в виде одной из четырех частей имени объекта, без имени связанного сервера.  

 ![Значок ссылки](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
OPENDATASOURCE ( 'provider_name', 'init_string' )  
```  
  
## <a name="arguments"></a>Аргументы  
 '*provider_name*'  
 Имя, зарегистрированное как PROGID имя поставщика OLE DB, используемое для доступа к источнику данных. Аргумент *provider_name* имеет тип данных **char** и не имеет значения по умолчанию.  

 > [!IMPORTANT]
 > Предыдущие поставщики Microsoft OLE DB для SQL Server (SQLOLEDB) и собственный клиент OLE DB для SQL Server (SQLNCLI) объявляются нерекомендуемыми для новых разработок. Вместо этого используйте новый драйвер [Microsoft OLE DB для SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), который будет обновлен с самыми последними серверными компонентами.
 
 '*init_string*'  
 Строка подключения, передаваемая в интерфейс IDataInitialize поставщика назначения. Синтаксис строки поставщика основан на парах "ключевое слово — значение", разделенных точкой с запятой, например: **"** _ключевое_слово1_=_значение_ **;** _ключевое_слово2_=_значение_ **"** .  
  
 Описание конкретных пар «ключевое_слово-значение», поддерживаемых поставщиком, см. в пакете [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access SDK. Данная документация определяет основной синтаксис. В приведенной ниже таблице представлены наиболее часто используемые ключевые слова в аргументе *init_string*.  
  
|Ключевое слово|Свойство OLE DB|Допустимые значения и описание|  
|-------------|---------------------|----------------------------------|  
|Источник данных|DBPROP_INIT_DATASOURCE|Имя источника данных для подключения. Различные поставщики интерпретируют его по-разному. Для поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это означает имя сервера. Для поставщика Jet OLE DB таким образом определяется полный путь к MDB-файлу или XLS-файлу.|  
|Location|DBPROP_INIT_LOCATION|Расположение базы данных для подключения.|  
|Расширенные свойства|DBPROP_INIT_PROVIDERSTRING|Строка подключения этого поставщика.|  
|Время ожидания подключения|DBPROP_INIT_TIMEOUT|Время, по истечении которого попытка соединения признается неудачной.|  
|Идентификатор пользователя.|DBPROP_AUTH_USERID|Идентификатор пользователя для соединения.|  
|Пароль|DBPROP_AUTH_PASSWORD|Пароль для соединения.|  
|Каталог|DBPROP_INIT_CATALOG|Имя первоначального каталога или каталога по умолчанию при подключении к источнику данных.|  
|Встроенные функции безопасности|DBPROP_AUTH_INTEGRATED|SSPI для указания проверки подлинности Windows|  
  
## <a name="remarks"></a>Remarks  
`OPENROWSET` всегда наследует параметры сортировки экземпляра независимо от параметров сортировки, заданных для столбцов.

Функцию `OPENDATASOURCE` можно использовать для доступа к удаленным данным из источников OLE DB только в том случае, если параметр реестра DisallowAdhocAccess явно содержит значение 0 для указанного поставщика, а также если включен расширенный параметр конфигурации Ad Hoc Distributed Queries. Если эти параметры не установлены, поведение по умолчанию запрещает нерегламентированный доступ.  
  
Функция `OPENDATASOURCE` может применяться в тех же местах в коде [!INCLUDE[tsql](../../includes/tsql-md.md)], где и имя связанного сервера. Следовательно, функцию `OPENDATASOURCE` можно использовать в качестве первой из четырех частей имени, которое ссылается на таблицу или представление в инструкциях SELECT, INSERT, UPDATE, DELETE или в удаленной хранимой процедуре в инструкции EXECUTE. При запуске удаленных хранимых процедур функция `OPENDATASOURCE` должна ссылаться на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Функция OPENDATASOURCE не может принимать переменные в качестве аргументов.  
  
Функции `OPENROWSET` и `OPENDATASOURCE` должны использоваться только для ссылки на источники данных OLE DB, обращения к которым происходят нечасто. Задайте связанный сервер для любых источников данных, доступ к которым производится достаточно часто. Функции OPENDATASOURCE и OPENROWSET не обеспечивают полную поддержку для определения связанных серверов. Например, отсутствует функция управления безопасностью и возможность запросить данные каталога. Вся информация о соединении, включая пароли, должна предоставляться каждый раз при вызове OPENDATASOURCE.  
  
> [!IMPORTANT]  
> Проверка подлинности Windows намного надежнее, чем проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Везде, где возможно, следует применять проверку подлинности Windows. Не рекомендуется использовать функцию `OPENDATASOURCE` с паролями, явно присутствующими в строке соединения.  
  
Требования к соединениям для каждого поставщика похожи на требования к этим параметрам при создании связанных серверов. Подробные сведения для многих распространенных поставщиков приведены в статье [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).  
  
Любой вызов функции `OPENDATASOURCE`, `OPENQUERY` или `OPENROWSET` в предложении `FROM` вычисляется отдельно и независимо от любого вызова этих функций, используемого как назначение при обновлении, даже если в двух таких вызовах будут заданы идентичные аргументы. В частности, условия фильтра или соединения, применяемые к результатам одного из таких вызовов, никак не влияют на результаты другого.  
  
## <a name="permissions"></a>Разрешения  
 Любой пользователь может выполнить OPENDATASOURCE. Разрешения, применяемые для подключения к удаленному серверу, определяются из строки подключения.  
  
## <a name="examples"></a>Примеры  

### <a name="a-using-opendatasource-with-select-and-the-sql-server-ole-db-driver"></a>A. Использование функции OPENDATASOURCE с инструкцией SELECT и драйвером OLE DB для SQL Server  
 В следующем примере используется [драйвер Microsoft OLE DB для SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) для доступа к таблице `HumanResources.Department` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на удаленном сервере `Seattle1`. Инструкция `SELECT` используется для определения возвращаемого набора строк. Строка поставщика содержит ключевые слова `Server` и `Trusted_Connection`. Эти ключевые слова распознаются драйвером OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```sql  
SELECT GroupName, Name, DepartmentID  
FROM OPENDATASOURCE('MSOLEDBSQL', 'Server=Seattle1;Database=AdventureWorks2016;TrustServerCertificate=Yes;Trusted_Connection=Yes;').HumanResources.Department  
ORDER BY GroupName, Name;  
``` 

### <a name="b-using-opendatasource-with-select-and-the-sql-server-ole-db-provider"></a>Б. Использование функции OPENDATASOURCE с инструкцией SELECT и поставщиком OLE DB для SQL Server  
В следующем примере создается нерегламентированное соединение с экземпляром `Payroll` СУБД [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на сервере `London`, а затем формируется запрос к таблице `AdventureWorks2012.HumanResources.Employee`. 

> [!NOTE] 
> При использовании SQLNCLI [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет использовать последнюю версию поставщика OLE DB для собственного клиента SQL Server. Предполагается, что поставщик OLE DB будет зарегистрирован в реестре с указанным идентификатором PROGID. 

> [!IMPORTANT]  
> Собственный клиент OLE DB для SQL Server (SQLNCLI) объявляется нерекомендуемым для новых разработок. Вместо этого используйте новый драйвер [Microsoft OLE DB для SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), который будет обновлен с самыми последними серверными компонентами.
  
```sql  
SELECT *  
FROM OPENDATASOURCE('SQLNCLI',  
    'Data Source=London\Payroll;Integrated Security=SSPI')  
    .AdventureWorks2012.HumanResources.Employee;  
```  

### <a name="c-using-the-microsoft-ole-db-provider-for-jet"></a>В. Использование поставщика Microsoft OLE DB для Jet   
 В следующем примере создается нерегламентированное соединение с электронной таблицей Excel в формате 1997 — 2003.  
  
```sql  
SELECT * FROM OPENDATASOURCE('Microsoft.Jet.OLEDB.4.0',  
    'Data Source=C:\DataFolder\Documents\TestExcel.xls;Extended Properties=EXCEL 5.0')...[Sheet1$] ;  
```  
  
## <a name="see-also"></a>См. также:  
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)  
  
