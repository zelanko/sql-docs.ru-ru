---
title: Изменение учетной записи-посредника агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], modifying
- modifying SQL Server Agent proxy
ms.assetid: 6e1dfbaa-8089-4813-940c-d5a2e13d8552
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dc2bf4573408606c38f368e58b3a245dfdea4ece
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52806856"
---
# <a name="modify-a-sql-server-agent-proxy"></a>Изменение учетной записи-посредника агента SQL Server
  В этом разделе описывается, как изменить запись-посредник агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Изменение учетной записи-посредника агента SQL Server с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Учетные записи-посредники агента[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используют учетные данные для хранения сведений об учетных записях пользователей Windows. Указанный в учетных данных пользователь должен иметь разрешение «Вход в систему в качестве пакетного задания» на компьютере, где запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверяет действительность доступа к подсистеме учетной записи-посредника и предоставляет ей доступ при каждом выполнении шага задания. Если учетная запись-посредник больше не имеет доступа к подсистеме, шаг задания завершается ошибкой. В противном случае агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] олицетворяет пользователя, указанного в учетной записи-посреднике, и запускает шаг задания.  
  
-   Если имени входа пользователя предоставлен доступ к учетной записи-посреднику или пользователь принадлежит к любой роли с доступом к учетной записи-посреднику, то он может использовать учетную запись-посредник в шаге задания.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Создавать, изменять или удалять учетные записи-посредники могут только члены предопределенной роли сервера **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-a-includessnoversionincludesssnoversion-mdmd-agent-proxy"></a>Изменение учетной записи-посредника агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, содержащий учетную запись-посредник агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которую необходимо изменить.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Учетные записи-посредники** .  
  
4.  Щелкните знак "плюс", чтобы развернуть узел подсистемы, содержащий учетную запись-посредник (например, **Скрипт ActiveX**).  
  
5.  Щелкните правой кнопкой мыши учетную запись-посредник, которую требуется изменить, и выберите пункт **Свойства**.  
  
6.  В диалоговом окне *Свойства учетной записи-посредника***имя_учетной_записи-посредника** внесите необходимые изменения в учетную запись-посредник. Дополнительные сведения о параметрах данного диалогового окна см. в разделе [Создание учетной записи-посредника агента SQL Server](create-a-sql-server-agent-proxy.md).  
  
7.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-modify-a-includessnoversionincludesssnoversion-mdmd-agent-proxy"></a>Изменение учетной записи-посредника агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Disables the proxy named 'Catalog application proxy'.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 0;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_update_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-proxy-transact-sql).  
  
  
