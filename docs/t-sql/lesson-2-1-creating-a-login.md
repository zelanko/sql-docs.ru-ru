---
title: "Создание имени для входа | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- creating a login
ms.assetid: a2512310-bdb6-41dc-858a-e866b2b58afc
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6bd2243866e52fbc855562757c7c041a36643c4d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-2-1---creating-a-login"></a>Урок 2–1. Создание данных для входа
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)] Чтобы получить доступ к компоненту [!INCLUDE[ssDE](../includes/ssde-md.md)], необходимо иметь имя для входа. Имя входа может идентифицировать пользователя как учетную запись Windows или как члена группы Windows, или имя входа может быть именем входа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , которое существует только в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При возможности используйте проверку подлинности Windows.  
  
По умолчанию администраторы компьютера имеют полный доступ к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Для этого занятия нужно иметь пользователя с меньшим правом доступа; следовательно, вы создадите новую локальную учетную запись проверки подлинности Windows на компьютере. Чтобы сделать это, нужно быть администратором на своем компьютере. После этого нужно предоставить новому пользователю доступ к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
### <a name="to-create-a-new-windows-account"></a>Создание новой учетной записи Windows  
  
1.  Нажмите кнопку **Пуск**, выберите **Выполнить**, в поле **Открыть** введите **%SystemRoot%\system32\compmgmt.msc /s**и нажмите кнопку **OK** , чтобы открыть программу "Управление компьютером".  
  
2.  В пункте **Служебные программы**откройте **Локальные пользователи и группы**, щелкните правой кнопкой мыши элемент **Пользователи**и выберите пункт **Новый пользователь**.  
  
3.  В поле **Имя пользователя** введите **Mary**.  
  
4.  В полях **Пароль** и **Подтверждение пароля** введите надежный пароль и нажмите кнопку **Создать** , чтобы создать нового локального пользователя Windows.  
  
### <a name="to-create-a-login"></a>Создание имени входа  
  
1.  В окне редактора запросов среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]введите и выполните следующий исходный код, заменив `computer_name` на имя компьютера. `FROM WINDOWS` указывает, что Windows проверит подлинность пользователя. Необязательный аргумент `DEFAULT_DATABASE` соединяет `Mary` с базой данных `TestData` , если только в ее строке соединения не указана другая база данных. Эта инструкция рассматривает точку с запятой в виде необязательного завершения инструкции языка [!INCLUDE[tsql](../includes/tsql-md.md)] .  
  
    ```  
    CREATE LOGIN [computer_name\Mary]  
        FROM WINDOWS  
        WITH DEFAULT_DATABASE = [TestData];  
    GO  
    ```  
  
    Этим авторизируется имя пользователя `Mary`, проверенное компьютером, чтобы получить доступ к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Если на компьютере находится более одного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , нужно создать имя входа для каждого экземпляра, к которому `Mary` должна иметь доступ.  
  
    > [!NOTE]  
    > Поскольку `Mary` не является доменной учетной записью, это имя пользователя может быть принято только на данном компьютере.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Предоставление доступа к базе данных](../t-sql/lesson-2-2-granting-access-to-a-database.md)  
  
## <a name="see-also"></a>См. также:  
[CREATE LOGIN &#40;Transact-SQL&#41;](../t-sql/statements/create-login-transact-sql.md)  
[Выбор режима проверки подлинности](../relational-databases/security/choose-an-authentication-mode.md)  
  
  
  
