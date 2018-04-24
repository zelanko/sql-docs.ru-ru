---
title: Просмотр сведений о шаге задания | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- displaying job step information
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- viewing job step information
ms.assetid: e3f06492-dc86-4e06-b186-ea58aff6d591
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: dab9aa3c092ad584f22a942bb88df6f07cd53f64
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="view-job-step-information"></a>View Job Step Information
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В данном разделе описано, как просмотреть сведения о шаге задания в окне «Свойства шага задания». Также предоставляются сведения о просмотре выходных данных шага задания.  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Для просмотра сведений о шаге задания используется:**  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
Если шаг задания был настроен так, чтобы вывод производился в таблицу или файл, и задание было запущено хотя бы однажды, можно видеть его вывод на странице **Дополнительно** окна **Свойства шага задания** . При удалении задания или его шага журнал вывода удаляется автоматически.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Если пользователь не принадлежит к предопределенной роли сервера **sysadmin** , он может просматривать лишь те задания, которыми владеет. А члены указанной роли могут просматривать все задания и все сведения об их шагах.  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-view-job-step-information"></a>Просмотр сведений о шаге задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните узел этого экземпляра.  
  
2.  Разверните узел **Агент SQL Server**, затем пункт **Задания**, щелкните правой кнопкой мыши задание, содержащее шаг, который следует просмотреть, и выберите пункт **Свойства**.  
  
3.  В окне **Свойства задания** перейдите на страницу **Шаги** .  
  
4.  Щелкните шаг задания, который нужно просмотреть, и выберите **Изменить**.  
  
5.  На странице **Общие** окна **Свойства шага задания** можно видеть тип шага задания и его действие.  
  
6.  Щелкните страницу **Дополнительно** , чтобы просмотреть действия, которые должен предпринимать агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в случае успешного или неуспешного выполнения этого шага задания, а также количество попыток выполнения этого этапа, куда должны выводиться результаты шага задания и под учетной записью какого пользователя он должен выполняться.  
  
#### <a name="to-view-job-step-output"></a>Просмотр выходных данных шага задания  
  
1.  В окне **Свойства шага задания** перейдите на страницу **Дополнительно** .  
  
2.  В зависимости от версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , с которой имеется соединение, просмотреть таблицу или файл вывода шага задания можно различными способами.  
  
    -   Если установлено соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или более поздними версиями, кнопку **Просмотр** можно нажать только при установленном флажке **Сохранять данные журнала в таблице** . В этом случае вывод шага задания производится в таблицу **sysjobstepslogs** в базе данных **msdb** .  
  
    -   Кнопка **Просмотр** недоступна, если выходные данные шагов задания записываются в файл. Чтобы просмотреть файл вывода шага задания, используйте блокнот.  
  
