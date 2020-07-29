---
title: View Job Step Information
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- displaying job step information
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- viewing job step information
ms.assetid: e3f06492-dc86-4e06-b186-ea58aff6d591
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2dc60fb5ef44ff4b94cf8326e97d552f34c3b1c7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85729725"
---
# <a name="view-job-step-information"></a>View Job Step Information
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В данном разделе описано, как просмотреть сведения о шаге задания в окне «Свойства шага задания». Также предоставляются сведения о просмотре выходных данных шага задания.  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [Безопасность](#Security)  
  
-   **Для просмотра сведений о шаге задания используется:**  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a>Ограничения  
Если шаг задания был настроен так, чтобы вывод производился в таблицу или файл, и задание было запущено хотя бы однажды, можно видеть его вывод на странице **Дополнительно** окна **Свойства шага задания** . При удалении задания или его шага журнал вывода удаляется автоматически.  
  
### <a name="security"></a><a name="Security"></a>безопасность  
  
#### <a name="permissions"></a><a name="Permissions"></a>Permissions  
Если пользователь не принадлежит к предопределенной роли сервера **sysadmin** , он может просматривать лишь те задания, которыми владеет. А члены указанной роли могут просматривать все задания и все сведения об их шагах.  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-view-job-step-information"></a>Просмотр сведений о шаге задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)] и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, затем пункт **Задания**, щелкните правой кнопкой мыши задание, содержащее шаг, который следует просмотреть, и выберите пункт **Свойства**.  
  
3.  В окне **Свойства задания** перейдите на страницу **Шаги** .  
  
4.  Щелкните шаг задания, который нужно просмотреть, и выберите **Изменить**.  
  
5.  На странице **Общие** окна **Свойства шага задания** можно видеть тип шага задания и его действие.  
  
6.  Щелкните страницу **Дополнительно** , чтобы просмотреть действия, которые должен предпринимать агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в случае успешного или неуспешного выполнения этого шага задания, а также количество попыток выполнения этого этапа, куда должны выводиться результаты шага задания и под учетной записью какого пользователя он должен выполняться.  
  
#### <a name="to-view-job-step-output"></a>Просмотр выходных данных шага задания  
  
1.  В окне **Свойства шага задания** перейдите на страницу **Дополнительно** .  
  
2.  В зависимости от версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которой имеется соединение, просмотреть таблицу или файл вывода шага задания можно различными способами.  
  
    -   Если установлено соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или более поздними версиями, кнопку **Просмотр** можно нажать только при установленном флажке **Сохранять данные журнала в таблице** . В этом случае вывод шага задания производится в таблицу **sysjobstepslogs** в базе данных **msdb** .  
  
    -   Кнопка **Просмотр** недоступна, если выходные данные шагов задания записываются в файл. Чтобы просмотреть файл вывода шага задания, используйте блокнот.  
  
