---
title: "Создание расписания | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
- schedules [SQL Server], jobs
ms.assetid: 8c7ef3b3-c06d-4a27-802d-ed329dc86ef3
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 11a81362665a11eac2310b97378eb8b419d52f55
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="create-a-schedule"></a>Создание расписания
Расписание для заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] вы можете создать с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)]или управляющих объектов SQL Server.  
  
-   **Перед началом работы выполните следующие действия.**  
  
    [безопасность](#Security)  
  
-   **Для создания расписания используется:**  
  
    [Среда Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-schedule"></a>Создание расписания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, щелкните правой кнопкой мыши узел **Задания**и выберите **Управление расписаниями**.  
  
3.  В диалоговом окне **Управление расписаниями** щелкните **Создать**.  
  
4.  В поле **Имя** введите имя нового расписания.  
  
5.  Если не нужно, чтобы расписание вступило в силу немедленно после создания, снимите флажок **Включено** .  
  
6.  Выберите одно из следующих значений для параметра **Тип расписания**:  
  
    -   Чтобы запускать задание, когда процессоры переходят в состояние бездействия, щелкните **Запускать при бездействии процессоров**.  
  
    -   Если необходимо периодическое выполнение расписания, выберите пункт **Повторяющееся задание**. Затем в диалоговом окне заполните группы **Частота**, **Сколько раз в день**и **Продолжительность** .  
  
    -   Если планируется однократное выполнение, выберите **Один раз**. Для установки расписания **Один раз** заполните в диалоговом окне группу **Однократное выполнение** .  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-create-a-schedule"></a>Создание расписания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- creates a schedule named RunOnce.   
    -- The schedule runs one time, at 23:30 on the day that the schedule is created.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_add_schedule (Transact-SQL)](http://msdn.microsoft.com/en-us/9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7).  
  
## <a name="SMO"></a>Использование управляющих объектов SQL Server  
**Создание расписания**  
  
Воспользуйтесь классом **JobSchedule** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  

