---
title: Занятие 2. Создание и применение политики стандартов именования | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 87e51f4e-156c-4def-8572-76a15075d75e
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: fb7082aec21e75c2852ac7efdc2d7a4fa565768d
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2018
ms.locfileid: "51512829"
---
# <a name="lesson-2-create-and-apply-a-naming-standards-policy"></a>Занятие 2. Создание и применение политики стандартов именования
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Некоторые типы политик управления на основе политик могут создавать триггеры для обеспечения будущего соответствия с политикой. На этом занятии создается политика, обеспечивающая стандарт именования таблиц. Затем для ее проверки выполняется попытка создания таблицы, нарушающей политику.  


## <a name="prerequisites"></a>предварительные требования
Для работы с этим руководством требуется среда SQL Server Management Studio и доступ к серверу SQL Server.

- Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
  
## <a name="create-the-finance-database"></a>Создание базы данных Finance  
  
1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]откройте окно запросов и выполните следующую инструкцию:  
  
    ```sql  
    CREATE DATABASE Finance ;  
    GO  
    ```  
  
2.  В обозревателе объектов щелкните **Базы данных**и нажмите клавишу F5 для обновления списка баз данных.  


## <a name="create-the-finance-tables-condition"></a>Создание условия "Таблицы Finance" 

1.  В обозревателе объектов раскройте узлы **Управление**и **Управление политиками**, щелкните правой кнопкой мыши узел **Условия**и выберите пункт **Создать условие**. 

   ![Новое условие](Media/lesson-2-create-and-apply-a-naming-standards-policy/new-condition.png)
  
2.  В диалоговом окне **Создание нового условия** в поле **Имя** введите **Finance Tables**.  
    1. В списке **Аспект** выберите **Многокомпонентное имя**. 
    1. В диалоговом окне **Выражение** области **Поле** выберите **@Name**, в поле **Оператор** выберите **Like**, а в поле **Значение** введите ```'fintbl%'``` для того, чтобы все имена таблиц начинались с букв **fintbl**.
    1. На странице **Описание** введите **Имена таблиц Finance должны начинаться с букв "fintbl"**, а затем нажмите кнопку **ОК** для создания условия.  

    ![Условие "Таблицы Finance"](Media/lesson-2-create-and-apply-a-naming-standards-policy/finance-tables-condition.png)
 
## <a name="create-the-finance-name-policy"></a>Создание политики имен Finance  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши папку **Политики**и выберите в контекстном меню пункт **Создать политику**.  

   ![Новая политика](Media/lesson-2-create-and-apply-a-naming-standards-policy/new-policy.png)
  
2.  В диалоговом окне **Создание новой политики** в поле **Имя** введите **Finance Name**.
    1. В списке **Проверить условия** выберите пункт **Таблицы Finance**. Он находится в области **Многокомпонентное имя** . 
    1. В области **Применить к** отображается список объектов баз данных, к которым можно применить эту политику. Установите флажок **Каждая таблица**.
    1. Установите флажок **Включено** . (Флажок **Включено** не применяется к политикам **По запросу** .)
    1. В списке **Режим оценки** выберите **При изменении: запретить**. Это обеспечит создание политикой триггера базы данных в базе данных Finance. 
    1. В списке **Ограничение сервера** выберите пункт **Нет**. 
    1. На странице **Описание** добавьте следующее описание: "Имена таблиц в базе данных Finance должны содержать fintbl%". 
    1. Вернитесь на страницу **Общее**, а затем в области **Каждая база данных** разверните раздел **Каждые** и нажмите **Создать условие**.

    ![Создание политики имен Finance](Media/lesson-2-create-and-apply-a-naming-standards-policy/create-new-policy-finance-name.png)
  
6.  В диалоговом окне **Создание нового условия** в поле **Имя** введите **База данных Finance**.
    1. В окне **Выражение** добавьте в выражение @Name = 'Finance' и нажмите кнопку **ОК**, чтобы закрыть страницу условия. 
  
    ![Создание условия базы данных Finance](Media/lesson-2-create-and-apply-a-naming-standards-policy/create-new-condition.png)

    > [!NOTE]  
    > Возможно, потребуется выйти из поля **Значение** для включения кнопки **ОК** .  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="create-the-finance-policy-category"></a>Создание категории политики Finance  
  
1.  В обозревателе объектов разверните узел **Управление**, щелкните правой кнопкой мыши узел **Управление политиками**и выберите пункт **Управление категориями**.  

   ![Управление категориями](Media/lesson-2-create-and-apply-a-naming-standards-policy/manage-categories.png)
  
2.  В диалоговом окне **Управление категориями политик** на вкладке **Имя**введите **Finance** в пустое поле и снимите флажок **Сделать подписки базы данных обязательными**. Параметр**Сделать подписки базы данных обязательными** принудительно подписывает каждую базу данных в экземпляре на политики, которые относятся к данной категории политик. В рамках этого занятия только база данных Finance должна быть подписана на политику "Finance Name".  

    ![Управление категориями политики](Media/lesson-2-create-and-apply-a-naming-standards-policy/manage-policy-categories.png)
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

## <a name="subscribe-to-the-finance-policy-category"></a>Подписка на категорию политик Finance  
  
1.  В обозревателе объектов разверните узел **Базы данных**, щелкните правой кнопкой мыши **Finance**, наведите указатель на пункт **Политики**и выберите пункт **Категории**. 

   ![Категории политик Finance](Media/lesson-2-create-and-apply-a-naming-standards-policy/finance-categories.png)
  
2.  Установите флажок **Есть подписка** для категории **Finance** .  

   ![Подписка на политику Finance](Media/lesson-2-create-and-apply-a-naming-standards-policy/subscribe-to-finance.png)
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="test-the-enforcement-of-the-finance-name-policy"></a>Тестирование принудительного применения политики названий финансов  
  
1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]откройте окно запроса. Выполните приведенные ниже инструкции, которые попытаются создать таблицу, нарушающую политику **Имена финансов** . Таблица нарушает политику, так как ее имя не начинается с букв **fintbl**.  
  
    ```sql  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO    
    ```  
  
    Обратите внимание, что политика предотвращает создание таблицы и возвращает информационное сообщение, содержащее имя политики. 

   ```
     Policy 'Finance Name' has been violated by 'SQLSERVER:\SQL\SQL\SQL2017\Databases\Finance\Tables\dbo.NewTable'.
     This transaction will be rolled back.
     Policy condition: '@Name LIKE 'fintbl%''
     Policy description: 'Tables names in the Finance database must contain 'fintbl%''.
     Additional help: '' : ''
     Statement: 'CREATE TABLE NewTable  
         (Col1 int)'.
     Msg 515, Level 16, State 2, Procedure msdb.sys.sp_syspolicy_execute_policy, Line 69 [Batch Start Line 2]
     Cannot insert the value NULL into column 'target_query_expression', table 'msdb.dbo.syspolicy_policy_execution_history_details_internal'; column does not allow nulls. INSERT fails.
     The statement has been terminated.
   ``` 
  
2.  Для предоставления достоверного имени измените код, как указано ниже, и снова запустите инструкцию.  
  
    ```sql  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO    
    ```  
  
    В это время создается таблица.  
  
## <a name="apply-the-policy-to-the-whole-server"></a>Применение политики ко всему серверу  
  
1.  В данный момент на категорию политики финансов подписана только база данных Finance. В большинстве случаев легче применить категорию политики ко всему серверу. В обозревателе объектов разверните узел **Управление**, щелкните правой кнопкой мыши узел **Управление политиками**и выберите пункт **Управление категориями**.  
  
2.  Найдите категорию Finance в диалоговом окне **Управление категориями политик** и установите флажок **Сделать подписки базы данных обязательными** для категории Finance.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Теперь категория Finance применяется ко всем базам данных, но созданное условие ограничивает политику имен финансов для базы данных Finance. Это показывает то, как используются сложные сочетания условий для целевых политик для их правильного применения к нескольким серверам.  
  
## <a name="summary"></a>Сводка  
В этом учебнике показано создание условий управления на основе политик, политик и групп политик, а также применение фильтров и проверка соответствия целей управления на основе политик.  
  
## <a name="next"></a>Дальше  
Данный учебник завершен. Чтобы вернуться к началу, обратитесь к статье [Учебник. Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/tutorial-administering-servers-by-using-policy-based-management.md).  
  
Список учебников см. в разделе [Учебные материалы по SQL Server 2016](../../sql-server/tutorials-for-sql-server-2016.md).  
  
## <a name="see-also"></a>См. также:  
[Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
