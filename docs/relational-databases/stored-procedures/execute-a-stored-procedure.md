---
title: Выполнение хранимой процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.executeprocedure.general.f1
- sql13.swb.executeprocedure.f1
helpviewer_keywords:
- stored procedures [SQL Server], parameters
- extended stored procedures [SQL Server], executing
- system stored procedures [SQL Server], executing
- stored procedures [SQL Server], executing
- user-defined stored procedures [SQL Server]
ms.assetid: a0b1337d-2059-4872-8c62-3f967d8b170f
caps.latest.revision: 38
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b0ea510f0e8eed8fe626066700ed20a27a288b97
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43070523"
---
# <a name="execute-a-stored-procedure"></a>Выполнение хранимой процедуры
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 > Материалы по предыдущим версиям SQL Server см. в разделе [Выполнение хранимой процедуры](execute-a-stored-procedure.md).

  В этом разделе описывается, как выполнить хранимую процедуру [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Существует два способа выполнения хранимой процедуры. Первым и наиболее распространенным подходом является вызов процедуры приложением или пользователем. Второй подход — настройка автоматического выполнения процедуры при запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если процедура вызывается приложением или пользователем, то в вызове явно указывается ключевое слово [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE или EXEC. Процедуру также можно вызывать и выполнять без ключевого слова, если она является первой инструкцией в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Для выполнения хранимой процедуры используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   При сопоставлении имен системных процедур используются параметры сортировки вызывающей базы данных. Таким образом, в вызове процедур следует всегда использовать точный регистр имен системных процедур. Например, этот код завершится с ошибкой при выполнении в контексте базы данных, в параметрах сортировки которой учитывается регистр:  
  
    ```sql  
    EXEC SP_heLP; -- Will fail to resolve because SP_heLP does not equal sp_help  
    ```  
  
     Чтобы показать точные имена системных процедур, запросите представления каталога [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md) и [sys.system_parameters](../../relational-databases/system-catalog-views/sys-system-parameters-transact-sql.md) .  
  
-   Если определяемая пользователем процедура имеет имя, совпадающее с системной процедурой, то такая определяемая пользователем процедура никогда не будет выполняться.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Выполнение системных хранимых процедур  
  
     Имена системных процедур начинаются с префикса **sp_**. Поскольку они логически отображаются во всех базах данных, определяемых и пользователем и системой, то они могут выполняться из любой базы данных без полного указания имени процедуры. Однако рекомендуется уточнять имена всех системных процедур указанием схемы **sys** во избежание конфликтов имен. В следующем примере демонстрируется рекомендуемый метод вызова системной процедуры.  
  
    ```sql  
    EXEC sys.sp_who;  
    ```  
  
-   Выполнение пользовательских хранимых процедур  
  
     При выполнении определяемой пользователем процедуры рекомендуется дополнительно указывать имя схемы. Это позволяет немного увеличить производительность, поскольку компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] не нужно выполнять поиск в нескольких схемах. Также исключается выполнение неправильной процедуры в случае, если в нескольких схемах базы данных имеются процедуры с одним именем.  
  
     В следующем примере демонстрируется рекомендуемый метод выполнения определяемой пользователем процедуры. Обратите внимание, что процедура принимает один входной параметр. Сведения об указании входных и выходных параметров см. в статье [Указание параметров](../../relational-databases/stored-procedures/specify-parameters.md).  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    EXEC dbo.uspGetEmployeeManagers @BusinessEntityID = 50;  
    ```  
  
     -Или-  
  
    ```sql  
    EXEC AdventureWorks2012.dbo.uspGetEmployeeManagers 50;  
    GO  
    ```  
  
     Если не указано уточненное имя определяемой пользователем процедуры, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] производит поиск процедуры в следующем порядке.  
  
    1.  схема **sys** текущей базы данных;  
  
    2.  Схема по умолчанию вызывающей программы при выполнении в пакете или в динамическом коде SQL. Если неуточненное имя процедуры присутствует в тексте определения другой процедуры, в следующую очередь выполняется поиск в схеме, содержащей другую процедуру.  
  
    3.  Схема **dbo** в текущей базе данных.  
  
-   Автоматическое выполнение хранимых процедур  
  
     Процедуры, помеченные для автоматического выполнения, выполняются каждый раз, когда запускается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и в процессе запуска восстанавливается база данных **master** . Настройка процедур для автоматического выполнения удобна для операций обслуживания базы данных и для постоянного выполнения процедур в фоновом процессе. Кроме того, автоматический запуск процедур может применяться для выполнения системных или служебных задач в базе данных **tempdb**, таких как создание глобальной временной таблицы. Это обеспечивает наличие такой временной таблицы при повторном создании базы данных **tempdb** во время запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Автоматически выполняемая процедура работает с теми же разрешениями, что и члены предопределенной роли сервера **sysadmin** . Любое сообщение об ошибке, сформированное такой процедурой, записывается в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Ограничений на количество автоматически запускаемых процедур не существует, однако помните, что для выполнения каждой необходим один рабочий поток. Если необходимо выполнить несколько процедур при запуске, которые не должны выполняться параллельно, настройте одну процедуру на автоматический запуск, а вторую вызывайте в ее теле (в конце). Таким образом будет задействован только один рабочий поток.  
  
    > [!TIP]  
    >  Не возвращайте никаких результирующих наборов из автоматически запускаемой процедуры. Эта хранимая процедура выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а не приложением или пользователем, и поэтому результирующие наборы нигде не обрабатываются.  
  
-   Установка, очистка и контроль автоматического выполнения  
  
     Помечать процедуру для автоматического выполнения может только системный администратор (**sa**). Кроме того, процедура должна находиться в базе данных **master** , принадлежать пользователю **sa**и не иметь входных или выходных параметров.  
  
     Используйте процедуру [sp_procoption](../../relational-databases/system-stored-procedures/sp-procoption-transact-sql.md) чтобы:  
  
    1.  обозначить существующую процедуру как автоматически запускаемую;  
  
    2.  отменить выполнение процедуры при запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
###  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в статьях [EXECUTE AS (Transact-SQL)](../../t-sql/statements/execute-as-transact-sql.md) и [EXECUTE AS Clause (Transact-SQL)](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
####  <a name="Permissions"></a> Permissions  
 Дополнительные сведения см. в разделе "Разрешения" статьи [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-execute-a-stored-procedure"></a>Выполнение хранимой процедуры  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], разверните его, а затем разверните узел **Базы данных**.  
  
2.  Разверните нужную базу данных, разверните узлы **Программирование**и **Хранимые процедуры**.  
  
3.  Щелкните правой кнопкой мыши определяемую пользователем хранимую процедуру и выберите команду **Выполнить хранимую процедуру**.  
  
4.  В диалоговом окне **Выполнение процедуры** укажите значение для каждого параметра и необходимость передачи значения NULL.  
  
     **Параметр**  
     Указывает имя параметра.  
  
     **Тип данных**  
     Указывает тип данных параметра.  
  
     **Выходной параметр**  
     Указывает, является ли этот параметр выходным.  
  
     **Передать значение NULL**  
     Передать значение NULL в качестве значения параметра.  
  
     **Value**  
     Введите значение параметра, передаваемое ему при вызове процедуры.  
  
5.  Чтобы выполнить хранимую процедуру, нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-execute-a-stored-procedure"></a>Выполнение хранимой процедуры  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано, как выполнить хранимую процедуру, которая принимает один параметр. В примере выполняется хранимая процедура `uspGetEmployeeManagers` со значением  `6` , указанным в параметре `@EmployeeID` .  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC dbo.uspGetEmployeeManagers 6;  
GO  
```  
  
#### <a name="to-set-or-clear-a-procedure-for-executing-automatically"></a>Установка и отмена автоматического запуска процедуры  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано, как использовать процедуру [sp_procoption](../../relational-databases/system-stored-procedures/sp-procoption-transact-sql.md) , чтобы задать автоматическое выполнение процедуры.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionName = ] 'startup'   
    , @OptionValue = 'on';  
```  
  
#### <a name="to-stop-a-procedure-from-executing-automatically"></a>Отмена автоматического выполнения процедуры  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано, как использовать процедуру [sp_procoption](../../relational-databases/system-stored-procedures/sp-procoption-transact-sql.md) , чтобы отменить автоматическое выполнение процедуры.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionValue = 'off';  
```  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
  
## <a name="see-also"></a>См. также:  
 [Указание параметров](../../relational-databases/stored-procedures/specify-parameters.md)   
 [Настройка параметра конфигураци и сервера scan for startup procs](../../database-engine/configure-windows/configure-the-scan-for-startup-procs-server-configuration-option.md)   
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [Хранимые процедуры (компонент Database Engine)](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)  
  
  
