---
title: Удаление учетной записи-посредника агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting SQL Server Agent proxies
- proxies [SQL Server Agent], deleting
- removing SQL Server Agent proxies
ms.assetid: 9248841d-7294-47d4-94f3-b34a0521fabc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9222253c884fdf3cfa52d283f250580a02a9f7ee
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62523760"
---
# <a name="delete-a-sql-server-agent-proxy"></a>Delete a SQL Server Agent Proxy
  В этом разделе описывается, как удалить учетную запись-посредник агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Удаление учетной записи-посредника агента SQL Server с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   При удалении учетной записи-посредника агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] убедитесь в том, что она не ссылается ни на какие активные шаги задания. Чтобы узнать, на какие шаги задания ссылается учетная запись-посредник, щелкните ее правой кнопкой мыши, выберите **Свойства**и в диалоговом окне _Свойства учетной записи-посредника_**имя_учетной_записи-посредника** перейдите на страницу **Ссылки** . При удалении учетной записи-посредника существует возможность переназначить все шаги задания, которые ее используют, в диалоговом окне **Удаление объекта** .  
  
-   Учетные записи-посредники агента[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используют учетные данные для хранения сведений об учетных записях пользователей Windows. Указанный в учетных данных пользователь должен иметь разрешение «Вход в систему в качестве пакетного задания» на компьютере, где запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверяет действительность доступа к подсистеме учетной записи-посредника и предоставляет ей доступ при каждом выполнении шага задания. Если учетная запись-посредник больше не имеет доступа к подсистеме, шаг задания завершается ошибкой. В противном случае агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] олицетворяет пользователя, указанного в учетной записи-посреднике, и запускает шаг задания.  
  
-   Если имени входа пользователя предоставлен доступ к учетной записи-посреднику или пользователь принадлежит к любой роли с доступом к учетной записи-посреднику, то он может использовать учетную запись-посредник в шаге задания.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Создавать, изменять или удалять учетные записи-посредники могут только члены предопределенной роли сервера **sysadmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a>Удаление учетной записи-посредника агента SQL Server  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, содержащий учетную запись-посредник, которую необходимо удалить.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Учетные записи-посредники** .  
  
4.  Чтобы развернуть подсистему, содержащую учетную запись-посредник (например, **Скрипт ActiveX**), которую необходимо удалить, щелкните знак "плюс" (+).  
  
5.  Щелкните правой кнопкой мыши удаляемую учетную запись-посредник и выберите пункт **Удалить**.  
  
6.  В диалоговом окне **Удаление объекта** убедитесь, что выбрана соответствующая учетная запись-посредник. Установите флажок **Переназначить** для того, чтобы переназначить шаги задания, которые ссылаются на эту учетную запись-посредник, на другую учетную запись.  
  
7.  Нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a>Удаление учетной записи-посредника агента SQL Server  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- deletes the proxy "Catalog application proxy"  
    USE msdb ;  
    GO  
    EXEC dbo.sp_delete_proxy  
        @proxy_name = N'Catalog application proxy' ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_delete_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql).  
  
  
