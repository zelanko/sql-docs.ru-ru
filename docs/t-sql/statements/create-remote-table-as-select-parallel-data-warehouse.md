---
title: "Создание УДАЛЕННОГО TABLE AS SELECT (Parallel Data Warehouse) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: 
ms.prod_service: pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16ef8191-7587-45a3-9ee9-7d99b7088de3
caps.latest.revision: "9"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5b1c445662f29241d8a2a1a547ef498f7491590b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="create-remote-table-as-select-parallel-data-warehouse"></a>Создание УДАЛЕННОГО TABLE AS SELECT (параллельное хранилище данных)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Выбирает данные из [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] базы данных и копирует их в новую таблицу в SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных на удаленном сервере. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]использует устройство, со всеми преимуществами MPP обработки запросов, чтобы выбрать данные для удаленной копии. Использовать в сценариях, требующих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функциональные возможности.  
  
 Настройка удаленного сервера, в разделе «Удаленный копирование таблицы» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE REMOTE TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name     AT ('<connection_string>')  
    [ WITH ( BATCH_SIZE = batch_size ) ]  
    AS <select_statement>  
[;]  
  
<connection_string> ::=   
    Data Source = { IP_address | hostname } [, port ]; User ID = user_name ;Password = password;  
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT <select_criteria>  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Для создания удаленной таблицы в базы данных. *database_name* — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных. По умолчанию — база данных по умолчанию для имени входа пользователя на сервере назначения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.  
  
 *schema_name*  
 Схема для новой таблицы. По умолчанию используется схема по умолчанию для имени входа пользователя на сервере назначения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.  
  
 *имя_таблицы*  
 Имя новой таблицы. Сведения о разрешенных имена таблиц, см. в разделе «Правила именования объектов» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Удаленная таблица создается как кучи. Он не имеет ограничений проверки или триггеров. Параметры сортировки удаленных столбцов таблицы совпадает с параметрами сортировки столбцы исходной таблицы. Это относится к столбцам типа **char**, **nchar**, **varchar**, и **nvarchar**.  
  
 *строка_соединения*  
 Строка символов, указывающая `Data Source`, `User ID`, и `Password` параметры для подключения к удаленному серверу и базе данных.  
  
 Строка подключения является разделенный точками с запятой список пар "ключ-значение". Ключевые слова не учитывают регистр. Пробелы между парами «ключ-значение» учитываются. Однако значения могут быть с учетом регистра, в зависимости от источника данных.  
  
 *Источник данных*  
 Параметр, который указывает имя или IP-адреса и TCP-номер порта для удаленного SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *Имя узла* или *IP-адрес*  
 Имя удаленного сервера или IPv4-адрес удаленного сервера. Адреса IPv6 не поддерживаются. Можно указать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] именованного экземпляра в формате **Computer_Name\Instance_Name** или **IP_address\Instance_Name**. Сервер должен быть удаленной и таким образом, не могут быть указаны как (local).  
  
 TCP *порт* номер  
 Номер порта TCP для подключения. Для экземпляра SQL Server, который не прослушивает порт по умолчанию 1433, можно указать номер порта TCP от 0 до 65535. Например: **ServerA 1450** или **10.192.14.27,1435**  
  
> [!NOTE]  
>  Корпорация Майкрософт рекомендует подключение к удаленному серверу с использованием IP-адрес. В зависимости от конфигурации сети подключение по имени компьютера могут потребовать дополнительных шагов для использования не является специализированным DNS-сервера для разрешения имени к правильному серверу. Этот шаг необязателен, при соединении с IP-адрес. Дополнительные сведения см. в разделе «Использовать DNS-сервер пересылки для DNS-устройство без разрешения имен (Analytics Platform System)» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 *имя_пользователя*  
 Является допустимым [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа для проверки подлинности. Максимальное количество символов — 128.  
  
 *пароль*  
 Пароль имени входа. Максимальное количество символов — 128.  
  
 *batch_size*  
 Максимальное число строк в пакете. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]отправляет строки в виде пакетов на сервере назначения. *Batch_size* является положительным целым числом > = 0. По умолчанию — 0.  
  
 С *обобщенное_табличное_выражение*  
 Задается временно именованный результирующий набор, называемый обобщенным табличным выражением (ОТВ). Дополнительные сведения см. в разделе [с общее_табличное_выражение &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 ВЫБЕРИТЕ \<select_criteria > запрос предикат, который указывает, какие данные будут заполнять новые удаленной таблицы. Сведения об инструкции SELECT см. в разделе [ВЫБЕРИТЕ &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Требуется:  
  
-   Разрешение SELECT для каждого объекта в предложении SELECT.  
  
-   Требуется разрешение CREATE TABLE в целевой базе данных SMP.  
  
-   Требуется ALTER, INSERT и разрешение SELECT на схему конечного SMP.  
  
## <a name="error-handling"></a>Обработка ошибок  
 Если происходит сбой копирования данных в удаленную базу данных, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] прервать операцию, регистрации ошибки и попытаться удалить удаленную таблицу. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]не гарантирует успешной очистки новой таблицы.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 **Сервер удаленного места назначения**:  
  
-   Значение по умолчанию — TCP и поддерживается только протокол для подключения к удаленному серверу.  
  
-   На целевой сервер должен быть сервером не является специализированным. CREATE REMOTE TABLE не может использоваться для копирования данных из одного устройства.  
  
-   Инструкцию CREATE REMOTE TABLE только для создания новых таблиц. Таким образом новая таблица не может уже существовать. Удаленную базу данных и схемы должен уже существовать.  
  
-   Удаленный сервер должен иметь места для хранения данных, передаваемых из устройства [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удаленной базы данных.  
  
 **Инструкция SELECT**:  
  
-   Предложения TOP и ORDER BY не поддерживаются в выберите критерии.  
  
-   CREATE REMOTE TABLE не может выполняться внутри активной транзакции или активен параметр автоматической ФИКСАЦИИ OFF для сеанса.  
  
 [SET ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/statements/set-rowcount-transact-sql.md) не влияет на этой инструкции. Чтобы достичь такое же поведение, используйте [в начало &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
## <a name="locking-behavior"></a>Режим блокировки  
 После создания удаленной таблицы, целевая таблица не блокируется, пока начинается копирование. Таким образом возможно, что другой процесс удалить удаленную таблицу после ее создания и перед началом копирования. В этом случае [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] выдаст ошибку и копирование завершится сбоем.  
  
## <a name="metadata"></a>Метаданные  
 Используйте [sys.dm_pdw_dms_workers &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md) просмотреть ход выполнения копирования выбранных данных на удаленный сервер SMP. Строки с типом PARALLEL_COPY_READER содержат эти сведения.  
  
## <a name="security"></a>безопасность  
 CREATE REMOTE TABLE использует [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности для подключения к удаленному [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра; не использует проверку подлинности Windows.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] Внешняя сеть с выходом необходимо включить брандмауэр с исключением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] портов, административных портов и порты для управления.  
  
 Чтобы предотвратить случайную потерю данных или повреждения, учетной записи пользователя, используемый для копирования из устройства в целевой базе данных должны иметь минимальные требуемые разрешения в целевой базе данных.  
  
 Параметры подключения позволяют подключаться к SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра с помощью протокола SSL, защищая данные имя и пароль пользователя, но фактических данных, отправляемых в виде открытого текста в незашифрованном виде. В этом случае злоумышленник может перехватить текст инструкции CREATE REMOTE TABLE, который содержит [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя пользователя и пароль для входа в систему Состояния [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра. Чтобы избежать этого, использовать шифрование данных для подключения к SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.  
  
##  <a name="Examples"></a> Примеры  
  
### <a name="a-creating-a-remote-table"></a>A. Создание удаленной таблицы  
 В этом примере создается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SMP удаленной таблице с именем `MyOrdersTable` в базе данных `OrderReporting` и схемы `Orders`. `OrderReporting` База данных находится на сервере с именем `SQLA` , прослушивает порт по умолчанию 1433. Подключение к серверу использует учетные данные пользователя `David`, пароль которого является `e4n8@3`.  
  
```  
CREATE REMOTE TABLE OrderReporting.Orders.MyOrdersTable  
AT ( 'Data Source = SQLA, 1433; User ID = David; Password = e4n8@3;' )  
AS SELECT <select_criteria>;  
```  
  
### <a name="b-querying-the-sysdmpdwdmsworkers-dmv-for-remote-table-copy-status"></a>Б. Запрос sys.dm_pdw_dms_workers динамического административного Представления для копирования состояние удаленной таблицы  
 Этот запрос показывает, как просмотреть состояние копирования для копирования удаленной таблицы.  
  
```  
SELECT * FROM sys.dm_pdw_dms_workers   
WHERE type = 'PARALLEL_COPY_READER';  
```  
  
### <a name="c-using-a-query-join-hint-with-create-remote-table"></a>В. Использование указаний запросов соединения с CREATE REMOTE TABLE  
 Этот запрос показан основной синтаксис для использования подсказки в запросе соединения с CREATE REMOTE TABLE. После отправки запроса к узлу управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на вычислительных узлах, будут применяться стратегии хэш соединения, при создании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] плана запроса. Дополнительные сведения о указания соединения и как использовать предложение OPTION. в разделе [предложение OPTION &#40; Transact-SQL &#41; ](../../t-sql/queries/option-clause-transact-sql.md).  
  
```  
USE ssawPDW;  
CREATE REMOTE TABLE OrderReporting.Orders.MyOrdersTable  
AT ( 'Data Source = SQLA, 1433; User ID = David; Password = e4n8@3;' )  
    AS SELECT T1.* FROM OrderReporting.Orders.MyOrdersTable T1   
    JOIN OrderReporting.Order.Customer T2  
    ON T1.CustomerID=T2.CustomerID OPTION (HASH JOIN);  
```  
  
  

