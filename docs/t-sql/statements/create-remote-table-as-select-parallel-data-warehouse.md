---
title: CREATE REMOTE TABLE AS SELECT (Parallel Data Warehouse) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: ''
ms.prod_service: pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.suite: sql
ms.component: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 16ef8191-7587-45a3-9ee9-7d99b7088de3
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b3a35be7145db9bb2ada6bd0af5805740568c216
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37990242"
---
# <a name="create-remote-table-as-select-parallel-data-warehouse"></a>CREATE REMOTE TABLE AS SELECT (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Выбирает данные из базы данных [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] и копирует их в новую таблицу в базе данных SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на удаленном сервере. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] использует устройство со всеми преимуществами обработки запросов MPP, чтобы выбрать данные для удаленной копии. Используйте в сценариях, требующих функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Сведения о настройке удаленного сервера см. в разделе "Копирование удаленной таблицы" в статье [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 База данных, в которой будет создана удаленная таблица. *database_name* — это база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию — база данных по умолчанию для имени входа пользователя в месте назначения экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *schema_name*  
 Схема новой таблицы. По умолчанию — схема по умолчанию для имени входа пользователя в месте назначения экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *table_name*  
 Имя новой таблицы. Сведения о разрешенных именах таблиц см. в разделе "Правила именования объектов" в статье [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Удаленная таблица создается как куча. Она не имеет проверочных ограничений или триггеров. Параметры сортировки столбцов удаленной таблицы совпадают с параметрами сортировки столбцов исходной таблицы. Эти параметры применяются к столбцам типа **char**, **varchar**, **nchar** и **nvarchar**.  
  
 *connection_string*  
 Строка символов, указывающая параметры `Data Source`, `User ID` и `Password` для подключения к удаленному серверу и базе данных.  
  
 Строка подключения является списком пар "ключ-значение", разделенных точкой с запятой. Ключевые слова не учитывают регистр. Пробелы между парами "ключ-значение" игнорируются. Однако значения могут быть чувствительны к регистру в зависимости от источника данных.  
  
 *Источник данных*  
 Параметр, который указывает имя или IP-адрес и номер TCP-порта для удаленного SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *hostname* или *IP_address*  
 Имя удаленного сервера или IPv4-адрес удаленного сервера. IPv6-адреса не поддерживаются. Можно указать именованный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в формате **Computer_Name\Instance_Name** или **IP_address\Instance_Name**. Сервер должен быть удаленным и не может быть указан как (локальный).  
  
 Номер TCP-*порта*  
 Номер TCP-порта, используемого для соединения. Для экземпляра SQL Server, который не ожидает передачи данных через порт по умолчанию 1433, можно указать номер TCP-порта от 0 до 65535. Например: **ServerA,1450** или **10.192.14.27,1435**  
  
> [!NOTE]  
>  Рекомендуем подключаться к удаленному серверу через IP-адрес. В зависимости от конфигурации сети подключение по имени компьютера может потребовать дополнительных шагов, чтобы использовать не являющийся устройством DNS-сервер для разрешения имени для правильного сервера. Этот шаг необязателен при соединении через IP-адрес. Дополнительные сведения см. в разделе "Использование DNS-сервера пересылки для разрешения имен DNS, не являющегося устройством (Analytics Platform System)" в статье [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 *user_name*  
 Действительное имя входа для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Максимальное количество символов равно 128.  
  
 *password*  
 Пароль имени входа. Максимальное количество символов равно 128.  
  
 *batch_size*  
 Максимальное количество строк на пакет. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] отправляет строки в виде пакетов на сервер назначения. *Batch_size* является целым положительным числом >= 0. Значение по умолчанию — 0.  
  
 WITH *common_table_expression*  
 Задается временно именованный результирующий набор, называемый обобщенным табличным выражением (ОТВ). Дополнительные сведения см. в разделе [WITH common_table_expression (Transact-SQL)](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 SELECT \<select_criteria> Предикат запроса, который указывает, какие данные будут заполнять новую удаленную таблицу. Сведения об инструкции SELECT см. в разделе [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требования:  
  
-   Разрешение SELECT для каждого объекта в предложении SELECT.  
  
-   Требуется разрешение CREATE TABLE в целевой базе данных SMP.  
  
-   Требуются разрешения ALTER, INSERT и SELECT на целевую схему SMP.  
  
## <a name="error-handling"></a>Обработка ошибок  
 Если происходит сбой копирования данных в удаленную базу данных, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] прерывает операцию, регистрирует ошибку и пытается удалить удаленную таблицу. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] не гарантирует успешную очистку новой таблицы.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 **Удаленный целевой сервер**:  
  
-   TCP является значением по умолчанию и единственным поддерживаемым протоколом для подключения к удаленному серверу.  
  
-   Целевой сервер не должен быть устройством. Инструкция CREATE REMOTE TABLE не может использоваться для копирования данных с одного устройства на другое.  
  
-   Инструкция CREATE REMOTE TABLE только создает новые таблицы. Поэтому новая таблица уже не может существовать. Удаленная база данных и схема уже должны существовать.  
  
-   Удаленный сервер должен иметь достаточно места для хранения данных, передаваемых с устройства в удаленную базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Инструкция SELECT**:  
  
-   Предложения TOP и ORDER BY не поддерживаются в критериях выбора.  
  
-   Инструкция CREATE REMOTE TABLE не может выполняться внутри активной транзакции или если для сеанса установлен параметр AUTOCOMMIT OFF.  
  
 [SET ROWCOUNT (Transact-SQL)](../../t-sql/statements/set-rowcount-transact-sql.md) не влияет на эту инструкцию. Чтобы обеспечить аналогичное поведение, воспользуйтесь инструкцией [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md).  
  
## <a name="locking-behavior"></a>Режим блокировки  
 После создания удаленной таблицы целевая таблица не блокируется, пока не начнется копирование. Поэтому другой процесс может удалить удаленную таблицу после ее создания и до начала копирования. В этом случае [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] выдает ошибку, и копирование не выполняется.  
  
## <a name="metadata"></a>Метаданные  
 Используйте [sys.dm_pdw_dms_workers (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md), чтобы просмотреть ход выполнения копирования выбранных данных на удаленный сервер SMP. Эти сведения содержатся в строках типа PARALLEL_COPY_READER.  
  
## <a name="security"></a>безопасность  
 Инструкция CREATE REMOTE TABLE использует проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для подключения к удаленному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не использует проверку подлинности Windows.  
  
 Для сети с внешним доступом [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] необходимо включить брандмауэр с исключением портов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], административных портов и портов управления.  
  
 Чтобы предотвратить случайную потерю или повреждение данных, учетная запись пользователя, используемая для копирования данных с устройства в целевую базу данных, должна иметь только минимальные требуемые разрешения в целевой базе данных.  
  
 Параметры подключения позволяют подключаться к экземпляру SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью протокола SSL, который защищает имя пользователя и пароль, но сами данные отправляются в виде открытого текста без шифрования. В этом случае злоумышленник может перехватить текст инструкции CREATE REMOTE TABLE, который содержит имя пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пароль для входа в экземпляр SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы избежать этого, используйте шифрование данных для подключения к экземпляру SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##  <a name="Examples"></a> Примеры  
  
### <a name="a-creating-a-remote-table"></a>A. Создание удаленной таблицы  
 В этом примере создается удаленная таблица SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем `MyOrdersTable` в базе данных `OrderReporting` и схеме `Orders`. База данных `OrderReporting` находится на сервере с именем `SQLA`, который ожидает передачи данных через порт по умолчанию 1433. Подключение к серверу использует учетные данные пользователя `David` с паролем `e4n8@3`.  
  
```  
CREATE REMOTE TABLE OrderReporting.Orders.MyOrdersTable  
AT ( 'Data Source = SQLA, 1433; User ID = David; Password = e4n8@3;' )  
AS SELECT <select_criteria>;  
```  
  
### <a name="b-querying-the-sysdmpdwdmsworkers-dmv-for-remote-table-copy-status"></a>Б. Запрос в динамическое административное представление sys.dm_pdw_dms_workers о состоянии копирования удаленной таблицы  
 Этот запрос показывает, как просмотреть состояние копирования при копировании удаленной таблицы.  
  
```  
SELECT * FROM sys.dm_pdw_dms_workers   
WHERE type = 'PARALLEL_COPY_READER';  
```  
  
### <a name="c-using-a-query-join-hint-with-create-remote-table"></a>В. Использование указаний соединения для запросов с CREATE REMOTE TABLE  
 Этот запрос показывает базовый синтаксис для использования указания соединения для запроса с инструкцией CREATE REMOTE TABLE. После отправки запроса к узлу управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполняющемуся на вычислительных узлах, будет применена стратегия хэш-соединения при создании плана запроса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения об указаниях соединения и использовании предложения OPTION см. в разделе [Предложение OPTION (Transact-SQL)](../../t-sql/queries/option-clause-transact-sql.md).  
  
```  
USE ssawPDW;  
CREATE REMOTE TABLE OrderReporting.Orders.MyOrdersTable  
AT ( 'Data Source = SQLA, 1433; User ID = David; Password = e4n8@3;' )  
    AS SELECT T1.* FROM OrderReporting.Orders.MyOrdersTable T1   
    JOIN OrderReporting.Order.Customer T2  
    ON T1.CustomerID=T2.CustomerID OPTION (HASH JOIN);  
```  
  
  

