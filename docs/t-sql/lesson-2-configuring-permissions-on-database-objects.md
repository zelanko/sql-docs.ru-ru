---
title: Руководство. Настройка разрешений для объектов базы данных
ms.custom: seo-lt-2019
ms.date: 07/31/2018
ms.prod: sql
ms.technology: t-sql
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- database permissions
ms.assetid: f964b66a-ec32-44c2-a185-6a0f173bfa22
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 991bdef702b1ed298bb492172ef65c6d25d5d0ab
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75244749"
---
# <a name="lesson-2-configure-permissions-on-database-objects"></a>Урок 2. Настройка разрешений для объектов базы данных
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
Предоставление пользователю доступа к базе данных включает три шага. Вначале создается имя входа. Имя входа дает пользователю возможность подключиться к компоненту [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]. Затем имя входа настраивается как пользователь в заданной базе данных. Наконец, предоставляются пользовательские разрешения на объекты базы данных. В этом занятии показаны все три шага, а также создание представления и хранимой процедуры в виде объекта.  

  >[!NOTE]
  > В этом занятии используются объекты, созданные в разделе [Урок 1. Создание объектов баз данных](lesson-1-creating-database-objects.md). Пройдите урок 1, прежде чем переходить к уроку 2. 

## <a name="prerequisites"></a>предварительные требования
Для работы с этим руководством необходима среда SQL Server Management Studio и доступ к экземпляру SQL Server. 

- Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Если у вас нет доступа к экземпляру SQL Server, выберите свою платформу в следующих ссылках. При выборе проверки подлинности SQL используйте учетные данные SQL Server.
- **Windows**: [Скачать выпуск SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads)
- **macOS**: [скачать SQL Server 2017 для Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker).

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="create-a-login"></a>Создает вход
Чтобы получить доступ к компоненту [!INCLUDE[ssDE](../includes/ssde-md.md)], необходимо иметь имя входа. Имя входа может идентифицировать пользователя как учетную запись Windows или как члена группы Windows, или имя входа может быть именем входа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , которое существует только в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При возможности используйте проверку подлинности Windows.  
  
По умолчанию администраторы компьютера имеют полный доступ к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Для этого занятия нужно иметь пользователя с меньшим правом доступа; следовательно, вы создадите новую локальную учетную запись проверки подлинности Windows на компьютере. Чтобы сделать это, нужно быть администратором на своем компьютере. После этого нужно предоставить новому пользователю доступ к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
### <a name="create-a-new-windows-account"></a>Создание учетной записи Windows  
  
1.  Нажмите кнопку **Пуск**, выберите **Выполнить**, в поле **Открыть** введите **%SystemRoot%\system32\compmgmt.msc /s**и нажмите кнопку **OK** , чтобы открыть программу "Управление компьютером". 
2.  В пункте **Служебные программы**откройте **Локальные пользователи и группы**, щелкните правой кнопкой мыши элемент **Пользователи**и выберите пункт **Новый пользователь**.    
3.  В поле **Имя пользователя** введите **Mary**.    
4.  В полях **Пароль** и **Подтверждение пароля** введите надежный пароль и нажмите кнопку **Создать** , чтобы создать нового локального пользователя Windows.  
  
### <a name="create-a-sql-login"></a>Создание имени для входа SQL  

В окне редактора запросов среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]введите и выполните следующий исходный код, заменив `computer_name` на имя компьютера. `FROM WINDOWS` указывает, что Windows проверит подлинность пользователя. Необязательный аргумент `DEFAULT_DATABASE` соединяет `Mary` с базой данных `TestData` , если только в ее строке соединения не указана другая база данных. Эта инструкция рассматривает точку с запятой в виде необязательного завершения инструкции языка [!INCLUDE[tsql](../includes/tsql-md.md)] .
  
  ```sql  
  CREATE LOGIN [computer_name\Mary]  
      FROM WINDOWS  
      WITH DEFAULT_DATABASE = [TestData];  
  GO  
  ```  
  
  Этим авторизируется имя пользователя `Mary`, проверенное компьютером, чтобы получить доступ к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Если на компьютере находится более одного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , нужно создать имя входа для каждого экземпляра, к которому `Mary` должна иметь доступ.    
  > [!NOTE]  
  > Поскольку `Mary` не является доменной учетной записью, это имя пользователя может быть принято только на данном компьютере. 


## <a name="grant-access-to-a-database"></a>Предоставление доступа к базе данных
Теперь Mary имеет доступ к данному экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], но не имеет разрешения на доступ к базе данных. У нее даже нет доступа к своей базе данных по умолчанию **TestData** , пока вы не авторизируете ее в качестве пользователя базы данных.  
  
Чтобы предоставить Mary доступ, переключитесь на базу данных **TestData** и при помощи инструкции CREATE USER сопоставьте ее имя входа с именем пользователя «Mary».  
  
### <a name="to-create-a-user-in-a-database"></a>Создание пользователя в базе данных  
  
Введите и выполните следующие инструкции (заменяя `computer_name` на имя компьютера), чтобы предоставить пользователю `Mary` доступ к базе данных `TestData` .
  
 ```sql  
 USE [TestData];  
 GO  
 
 CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
 GO    
 ```  
  
 Теперь пользователь Mary имеет доступ к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и к базе данных `TestData` .  


## <a name="create-views-and-stored-procedures"></a>Создание представлений и хранимых процедур
Будучи администратором, можно выполнять инструкцию SELECT из таблицы **Products** и представления **vw_Names** , а также выполнять процедуру **pr_Names** ; однако Mary всего этого не может. Чтобы предоставить Mary необходимые разрешения, воспользуйтесь инструкцией GRANT.  

### <a name="grant-permission-to-stored-procedure"></a>Предоставление разрешений на хранимые процедуры  
Выполните следующую инструкцию, чтобы предоставить `Mary` разрешение на `EXECUTE` для хранимой процедуры `pr_Names` .
  
  ```sql  
  GRANT EXECUTE ON pr_Names TO Mary;  
  GO  
  ```  
  
В данном сценарии Mary имеет доступ только к таблице **Products** посредством хранимой процедуры. Если Mary нужно выполнять инструкцию SELECT к представлению, нужно выполнить инструкцию `GRANT SELECT ON vw_Names TO Mary`. Чтобы удалить доступ к объектам базы данных, воспользуйтесь инструкцией REVOKE.  
  
> [!NOTE]  
> Если таблицей, представлением или хранимой процедурой не владеет та же схема, процесс предоставления прав становится более сложным.  
  
### <a name="about-grant"></a>Об инструкции GRANT  
Нужно иметь разрешение на EXECUTE, чтобы выполнить хранимую процедуру. Нужно иметь разрешения на SELECT, INSERT, UPDATE и DELETE, чтобы получить доступ к данным и изменять их. Инструкция GRANT также используется для других разрешений, например для разрешений на создание таблиц.  
  
## <a name="next-steps"></a>Дальнейшие действия
В следующей статье вы узнаете, как удалить объекты базы данных, созданные в других уроках. 

Дополнительные сведения см. в следующей статье:
> [!div class="nextstepaction"]
>[Дальнейшие действия](lesson-3-deleting-database-objects.md)
  
