---
title: Настройка действий системы при успешном или неуспешном выполнении шага задания | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, action flow logic
- successful jobs [SQL Server]
- failed jobs [SQL Server]
- jobs [SQL Server Agent], action flow logic
ms.assetid: 23041ccf-8a07-41d3-85b9-c449a54b7e1e
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 51d32d8434280340d6c0352f5f31c16a0574b171
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681982"
---
# <a name="set-job-step-success-or-failure-flow"></a>Set Job Step Success or Failure Flow
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

При создании задания агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно определить действия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при возникновении ошибки в ходе его выполнения. Определите действия, которые должен предпринять [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при успешном и неуспешном завершении каждого шага задания. Затем с помощью агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настройте логику потока действий на шаге.  
  
-   **Перед началом:**  
  
    [безопасность](#Security)  
  
-   **Для настройки действий системы при успешном или неуспешном выполнении шага задания используется:**  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-set-job-step-success-or-failure-flow"></a>Настройка действий системы при успешном или неуспешном выполнении шага задания  
  
1.  В **обозревателе объектов**раскройте узел **Агент SQL Server**, а затем узел **Задания**.  
  
2.  Щелкните правой кнопкой мыши задание, которое необходимо изменить, и выберите **Свойства**.  
  
3.  Перейдите на страницу **Шаги** , выберите нужный шаг и щелкните **Редактировать**.  
  
4.  В диалоговом окне **Свойства шага задания** выберите страницу **Дополнительно** .  
  
5.  В диалоговом окне **Действие при успехе**выберите действие, которое необходимо выполнить при успешном окончании шага задания.  
  
6.  В поле **Количество повторных попыток** введите количество от 0 до 9999 повторных попыток выполнения шага задания, прежде чем будет принято решение о неуспешном завершении. При вводе в поле **Повторные попытки** значения, превышающего 0, введите значение в поле **Интервал повтора (в минутах)** . Указанное значение определяет длительность интервала от 1 до 9999 минут между повторными попытками выполнения шага задания.  
  
7.  В списке **Действия при неуспешном выполнении** выберите действие, которое необходимо выполнить в случае неуспешного завершения шага задания.  
  
8.  Если задание является скриптом [!INCLUDE[tsql](../../includes/tsql-md.md)] , возможен выбор из следующих вариантов.  
  
    -   В поле **Выходной файл** введите имя выходного файла, в который будет происходить запись выходных данных скрипта. По умолчанию файл перезаписывается при каждом выполнении шага задания. Если не нужно перезаписывать файл вывода, поставьте флажок **Дописать выходные данные в существующий файл**.  
  
    -   Установите флажок **Сохранять данные журнала в таблице** , если журнал шага задания необходимо вести в таблице базы данных. По умолчанию содержимое таблицы перезаписывается при каждом выполнении шага задания. Если не нужно, чтобы содержимое таблицы перезаписывалось, поставьте флажок **Дописать выходные данные в существующую запись в таблице**. После выполнения шага задания можно просмотреть содержимое этой таблицы, нажав **Просмотр**.  
  
    -   Установите флажок **Включить в журнал выходные данные шага** , если результаты шага должны быть включены в его журнал. Результат будет отображен только в случае отсутствия ошибок. Кроме того, отображаемый результат может быть усечен.  
  
9. В списке **Выполнять от имени пользователя** выберите учетную запись-посредник с учетными данными, которые должно использовать задание.  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-set-job-step-success-or-failure-flow"></a>Настройка действий системы при успешном или неуспешном выполнении шага задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @on_success_action = 1;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_add_jobstep (Transact-SQL)](http://msdn.microsoft.com/97900032-523d-49d6-9865-2734fba1c755).  
  
## <a name="SMO"></a>Использование управляющих объектов SQL Server  
**Настройка действий системы при успешном или неуспешном выполнении шага задания**  
  
Воспользуйтесь классом **JobStep** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
