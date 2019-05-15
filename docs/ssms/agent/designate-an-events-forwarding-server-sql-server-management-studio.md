---
title: Назначение сервера для перенаправления событий | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 425fa57e064f5bebb76a1de1149ba56f43dcfce2
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65096616"
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a>Назначение сервера для перенаправления событий (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как назначить сервер, на который [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перенаправляет события в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Обратите внимание, что пересылка событий применяется к событиям между серверами, а не к событиям между экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , размещенными на одном компьютере. Также заметьте, что для получения перенаправленных событий сервер управления предупреждениями должен быть назначен экземпляром SQL Server по умолчанию.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Назначение сервера перенаправления событий с помощью:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-designate-an-events-forwarding-server"></a>Назначение сервера пересылки событий  
  
1.  В **обозревателе объектов** щелкните значок «плюс», чтобы развернуть сервер, с которого требуется перенаправлять события на другой сервер.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server** и выберите пункт **Свойства**.  
  
3.  В диалоговом окне ***Свойства агента SQL Server —**_имя_сервера_ в разделе **Выберите страницу** выберите **Дополнительно**.  
  
4.  В области **Пересылка событий SQL Server**установите флажок **Перенаправить события на другой сервер** .  
  
5.  В списке **Сервер** выберите сервер, а затем на вкладке **События**выполните одно из следующих действий:  
  
    -   Выберите **Необработанные события** , чтобы выполнялась переадресация только событий, не обработанных локальными предупреждениями.  
  
    -   Выберите пункт **Все события** , чтобы выполнялась переадресация всех событий вне зависимости от того, обрабатывались они локальными предупреждениями или нет.  
  
6.  В списке **Если серьезность события равна или превышает** выберите степень серьезности, при которой события переадресуются выбранному серверу.  
  
7.  После завершения нажмите кнопку **ОК**.  
  
