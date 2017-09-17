---
title: "OPENDATASOURCE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd106322dfc78186aefaadac42622852d87d40f2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="opendatasource-transact-sql"></a>OPENDATASOURCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Передает сведения о нерегламентированном соединении в виде одной из четырех частей имени объекта, без имени связанного сервера.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OPENDATASOURCE ( provider_name, init_string )  
```  
  
## <a name="arguments"></a>Аргументы  
 *provider_name*  
 Имя, зарегистрированное как PROGID имя поставщика OLE DB, используемое для доступа к источнику данных. *provider_name* — **char** тип данных, и не имеет значения по умолчанию.  
  
 *init_string*  
 Строка соединения, передаваемая IDataInitialize интерфейса поставщика назначения. Синтаксис строки поставщика основан на пары значение ключевого слова, разделенных точкой с запятой, например: **"***ключевое_слово1*=*значение***;** *ключевое_слово2*=*значение***"**.  
  
 Описание конкретных пар «ключевое_слово-значение», поддерживаемых поставщиком, см. в пакете [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access SDK. Данная документация определяет основной синтаксис. В следующей таблице перечислены наиболее часто используемые ключевые слова в *init_string* аргумент.  
  
|Ключевое слово|Свойство OLE DB|Допустимые значения и описание|  
|-------------|---------------------|----------------------------------|  
|Источник данных|DBPROP_INIT_DATASOURCE|Имя источника данных для подключения. Различные поставщики интерпретируют его по-разному. Для поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это означает имя сервера. Для поставщика Jet OLE DB таким образом определяется полный путь к MDB-файлу или XLS-файлу.|  
|Местоположение|DBPROP_INIT_LOCATION|Расположение базы данных для подключения.|  
|Расширенные свойства|DBPROP_INIT_PROVIDERSTRING|Строка подключения этого поставщика.|  
|Время ожидания подключения|DBPROP_INIT_TIMEOUT|Время, по истечении которого попытка соединения признается неудачной.|  
|Идентификатор пользователя|DBPROP_AUTH_USERID|Идентификатор пользователя для соединения.|  
|Пароль|DBPROP_AUTH_PASSWORD|Пароль для соединения.|  
|Каталог|DBPROP_INIT_CATALOG|Имя первоначального каталога или каталога по умолчанию при подключении к источнику данных.|  
|Встроенные функции безопасности|DBPROP_AUTH_INTEGRATED|SSPI для указания проверки подлинности Windows|  
  
## <a name="remarks"></a>Замечания  
 Функцию OPENDATASOURCE можно использовать для доступа к удаленным данным из источников OLE DB только в том случае, если параметр реестра DisallowAdhocAccess явно содержит 0 для указанного поставщика, а также если используется расширенный параметр Ad Hoc Distributed Queries. Если эти параметры не установлены, поведение по умолчанию запрещает нерегламентированный доступ.  
  
 Функция OPENDATASOURCE может применяться в тех же местах в коде [!INCLUDE[tsql](../../includes/tsql-md.md)], где и имя связанного сервера. Следовательно, функцию OPENDATASOURCE можно использовать в качестве первой из четырех частей имени, которое ссылается на таблицу или представление в инструкциях SELECT, INSERT, UPDATE, DELETE или в удаленной хранимой процедуре в инструкции EXECUTE. При запуске удаленных хранимых процедур функция OPENDATASOURCE должна ссылаться на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Функция OPENDATASOURCE не может принимать переменные в качестве аргументов.  
  
 Функции OPENROWSET и OPENDATASOURCE должны использоваться только для ссылки на источники данных OLE DB, обращения к которым происходят нечасто. Задайте связанный сервер для любых источников данных, доступ к которым производится достаточно часто. Ни функция OPENDATASOURCE, ни функция OPENROWSET не обеспечивают полную поддержку для определения связанных серверов. Например, отсутствует управление безопасностью и возможность запросить данные каталога. Вся информация о соединении, включая пароли, должна предоставляться каждый раз при вызове OPENDATASOURCE.  
  
> [!IMPORTANT]  
>  Проверка подлинности Windows намного надежнее, чем проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Везде, где возможно, следует применять проверку подлинности Windows. Не рекомендуется использовать функцию OPENDATASOURCE с паролями, явно присутствующими в строке соединения.  
  
 Требования к соединениям для каждого поставщика похожи на требования к этим параметрам при создании связанных серверов. В разделе представлены сведения по многим обычным поставщикам [sp_addlinkedserver &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).  
  
 Любой вызов функции OPENDATASOURCE, OPENQUERY или OPENROWSET в предложении FROM вычисляется отдельно и независимо от любого вызова этих функций, используемого как назначение при обновлении, даже если в двух таких вызовах будут заданы идентичные аргументы. В частности, условия фильтра или соединения, применяемые к результатам одного из таких вызовов, никак не влияют на результаты другого.  
  
## <a name="permissions"></a>Permissions  
 Любой пользователь может выполнить OPENDATASOURCE. Разрешения, применяемые для подключения к удаленному серверу, определяются из строки подключения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается нерегламентированное соединение с экземпляром `Payroll` СУБД [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на сервере `London`, а затем формируется запрос к таблице `AdventureWorks2012.HumanResources.Employee`. (При использовании SQLNCLI [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет использовать последнюю версию поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)  
  
```  
SELECT *  
FROM OPENDATASOURCE('SQLNCLI',  
    'Data Source=London\Payroll;Integrated Security=SSPI')  
    .AdventureWorks2012.HumanResources.Employee  
```  
  
 В следующем примере создается нерегламентированное соединение с электронной таблицей Excel в формате 1997 — 2003.  
  
```  
SELECT * FROM OPENDATASOURCE('Microsoft.Jet.OLEDB.4.0',  
'Data Source=C:\DataFolder\Documents\TestExcel.xls;Extended Properties=EXCEL 5.0')...[Sheet1$] ;  
```  
  
## <a name="see-also"></a>См. также:  
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)  
  
  
