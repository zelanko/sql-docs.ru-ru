---
title: "Удаление учетной записи-посредника агента SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting SQL Server Agent proxies
- proxies [SQL Server Agent], deleting
- removing SQL Server Agent proxies
ms.assetid: 9248841d-7294-47d4-94f3-b34a0521fabc
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 79937166e8bbd119f2bb5d5e98b7a49dd969047b
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="delete-a-sql-server-agent-proxy"></a>Delete a SQL Server Agent Proxy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описывается, как удалить учетную запись-посредник агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] или [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Удаление учетной записи-посредника агента SQL Server с помощью:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   При удалении учетной записи-посредника агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] убедитесь в том, что она не ссылается ни на какие активные шаги задания. Чтобы узнать, на какие шаги задания ссылается учетная запись-посредник, щелкните ее правой кнопкой мыши, выберите **Свойства** и в диалоговом окне *Свойства учетной записи-посредника***имя_учетной_записи-посредника* перейдите на страницу **Ссылки**. При удалении учетной записи-посредника существует возможность переназначить все шаги задания, которые ее используют, в диалоговом окне **Удаление объекта** .  
  
-   Учетные записи-посредники агента[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] используют учетные данные для хранения сведений об учетных записях пользователей Windows. Указанный в учетных данных пользователь должен иметь разрешение «Вход в систему в качестве пакетного задания» на компьютере, где запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверяет действительность доступа к подсистеме учетной записи-посредника и предоставляет ей доступ при каждом выполнении шага задания. Если учетная запись-посредник больше не имеет доступа к подсистеме, шаг задания завершается ошибкой. В противном случае агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] олицетворяет пользователя, указанного в учетной записи-посреднике, и запускает шаг задания.  
  
-   Если имени входа пользователя предоставлен доступ к учетной записи-посреднику или пользователь принадлежит к любой роли с доступом к учетной записи-посреднику, то он может использовать учетную запись-посредник в шаге задания.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Создавать, изменять или удалять учетные записи-посредники могут только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a>Удаление учетной записи-посредника агента SQL Server  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, содержащий учетную запись-посредник, которую необходимо удалить.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Учетные записи-посредники** .  
  
4.  Чтобы развернуть подсистему, содержащую учетную запись-посредник (например, **Скрипт ActiveX**), которую необходимо удалить, щелкните знак "плюс" (+).  
  
5.  Щелкните правой кнопкой мыши удаляемую учетную запись-посредник и выберите пункт **Удалить**.  
  
6.  В диалоговом окне **Удаление объекта** убедитесь, что выбрана соответствующая учетная запись-посредник. Установите флажок **Переназначить** для того, чтобы переназначить шаги задания, которые ссылаются на эту учетную запись-посредник, на другую учетную запись.  
  
7.  Нажмите кнопку **ОК**.  
  
## <a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a>Удаление учетной записи-посредника агента SQL Server  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
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
  
Дополнительные сведения см. в разделе [sp_delete_proxy (Transact-SQL)](http://msdn.microsoft.com/en-us/44a1db13-b7f2-4dab-a1b5-b8dafb41737c).  
  
