---
title: Обновление служб Data Quality Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: f396666b-7754-4efc-9507-0fd114cc32d5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5c76fda112acae7b8a9314d217f5c32d197e87f9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62775634"
---
# <a name="upgrade-data-quality-services"></a>Обновление служб Data Quality Services
  Этот раздел предоставляет сведения о том, как обновить существующую установку служб Data Quality Services (DQS) в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии CTP2. В процессе обновления сервера служб DQS в службах DQS в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], необходимо обновить схему базы данных служб DQS.  
  
> [!IMPORTANT]
>  -   Необходимо создать резервную копию баз данных DQS, прежде чем обновлять DQS, чтобы предотвратить любую случайную потерю данных при обновлении схемы. Дополнительные сведения о создании резервной копии баз данных DQS см. в разделе [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
> -   Для выполнения задач по обеспечению качества данных вы можете подключиться к версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] сервера DQS, используя текущую или более раннюю версию клиента DQS или [преобразование "Очистка DQS"](../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) в службах Integration Services.  
> -   Можно продолжить использование надстройки служб Master Data Services для Excel версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 1 (SP1) после обновления служб Data Quality Services и Master Data Services до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2. Однако любая более ранняя версия надстройки служб Master Data Services для Excel перестанет работать после обновления до версии SQL Server 2014 CTP2. Можно загрузить надстройку служб Master Data Services для Excel версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 1 (SP1) по [этой ссылке](https://go.microsoft.com/fwlink/?LinkId=328664).  
  
##  <a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо выполнить вход от имени члена группы администраторов на компьютере [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
-   Учетная запись пользователя Windows должна входить в предопределенную роль сервера sysadmin на экземпляре SQL Server, где установлен сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
##  <a name="Upgrade"></a> Обновление DQS  
 Обновление DQS:  
  
1.  Создайте резервные копии баз данных DQS перед началом процесса обновления. Дополнительные сведения о создании резервной копии баз данных DQS см. в разделе [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
  
2.  Обновите экземпляр SQL Server, на котором установлен компонент DQS для служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    1.  Запустите мастер установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
    2.  На панели слева щелкните **Установка**.  
  
    3.  В области справа щелкните **обновление с SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 или SQL Server 2012**.  
  
    4.  Завершите работу мастера установки.  
  
        > [!NOTE]  
        >  Это обновит экземпляр SQL Server в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , а также задает последнюю Data Quality Client, если клиент DQS был ранее установлен на этом компьютере. При наличии клиента служб DQS установлены на других компьютерах, необходимо выполнить шаги по в шаге 2 на этих компьютерах, чтобы установить текущую версию клиента служб DQS. Мастер установки установит текущую версию служб Data Quality Client вместе с текущей версией клиента служб DQS. После обновления схемы баз данных DQS можно подключиться к [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версию сервера служб DQS с помощью текущего или более ранней версией клиента служб DQS.  
  
3.  Обновите схему баз данных DQS.  
  
    1.  Откройте командную строку от имени администратора.  
  
    2.  В командной строке перейдите в папку, где находится файл DQSInstaller.exe. Для экземпляра SQL Server по умолчанию файл DQSInstaller.exe будет находиться в папке «C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn».  
  
        ```  
        cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
        ```  
  
    3.  В командной строке введите следующую команду и нажмите клавишу ВВОД:  
  
        ```  
        dqsinstaller.exe -upgrade  
        ```  
  
    4.  Установщик предложит создать резервную копию базы данных DQS, прежде чем продолжить. Если резервное копирование баз данных DQS уже выполнено, введите `Y` или `Yes` и нажмите клавишу ВВОД, чтобы продолжить обновление.  
  
    5.  После успешного обновления схемы баз данных DQS отображается сообщение о завершении.  
  
##  <a name="Verify"></a> Проверка обновления баз данных DQS схемы  
 Для проверки, что схема баз данных DQS обновлена успешно, можно проверить в текущей версии базы данных DQS_MAIN и DQS_PROJECTS с помощью запроса к таблице A_DB_VERSION в каждой базе данных. Для этого сделайте следующее:  
  
1.  Запустите среду SQL Server Management Studio и установите соединение с экземпляром SQL Server, содержащий обновленные базы данных DQS схемы.  
  
2.  Выполните следующий запрос:  
  
    ```  
    SELECT * FROM DQS_MAIN.dbo.A_DB_VERSION WHERE STATUS=2;  
    SELECT * FROM DQS_PROJECTS.dbo.A_DB_VERSION WHERE STATUS=2;  
    ```  
  
3.  Выводится запись для каждой операции обновления, а также дата создания обновления. Максимальное VERSION_ID и ASSEMBLY_VERSION на самой последней даты текущую версию. Значение 2 в столбце STATUS означает успешное выполнение процедуры. Если возникла ошибка, то ОШИБКА перечисляются в столбец. Образец вывода:  
  
    |ID|UPGRADE_DATE|VERSION_ID|ASSEMBLY_VERSION|USER_NAME|STATUS|ошибка|  
    |--------|-------------------|-----------------|-----------------------|----------------|------------|-----------|  
    |1000|2013-08-11 05:26:39.567|1200|11.0.3000.0|\<Домен\имя_пользователя>|2||  
    |1001|2013-09-19 15:09:37.750|1600|12.0.xxxx.0|\<Домен\имя_пользователя>|2||  
  
## <a name="see-also"></a>См. также  
 [Установка служб Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Удаление объектов сервера служб Data Quality](../../sql-server/install/remove-data-quality-server-objects.md)   
 [Обновление до SQL Server 2014](upgrade-sql-server.md)  
  
  
