---
title: "Always On for SSIS Catalog (SSISDB) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.ssms.alwayson.f1"
ms.assetid: 7f089455-35ee-4c13-884e-9254b685d07d
caps.latest.revision: 17
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Always On for SSIS Catalog (SSISDB)
  Группы доступности AlwaysOn — это решение для высокой доступности и аварийного восстановления, являющееся альтернативой зеркальному отображению баз данных на уровне предприятия. Группа доступности поддерживает среду отработки отказа для дискретного набора пользовательских баз данных, известных как базы данных доступности, которые совместно выполняют переход на другой ресурс. Дополнительные сведения см. в разделе [Группы доступности AlwaysOn](https://msdn.microsoft.com/library/hh510230.aspx).  
  
 Для обеспечения высокого уровня доступности для каталога служб SSIS (SSISDB) и его содержимого (проектов, пакетов, журналов выполнения и т. д.) можно добавить базу данных SSISDB (практически так же, как и любую другую базу данных) в группу доступности AlwaysOn. В случае сбоя один из вторичных узлов автоматически становится новым основным узлом.  
 
 > [!IMPORTANT]  В случае сбоя выполнявшиеся пакеты не перезапускаются и не возобновляются. 
 
 **В этом разделе**  
  
1.  [Предварительные требования](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#prereq)  
  
2.  [Настройка поддержки служб SSIS для AlwaysOn](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Firsttime)  
  
3.  [Обновление SSISDB в группе доступности](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Upgrade)  
  
##  <a name="a-nameprereqa-prerequisites"></a><a name="prereq"></a> Предварительные требования  
 Перед включением поддержки AlwaysOn для базы данных SSISDB необходимо выполнить указанные далее предварительные действия.  
  
1.  Настроить отказоустойчивый кластер Windows. Инструкции см. в записи блога [Установка компонентов и средств отказоустойчивого кластера для Windows Server 2012)](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) (Installing the Failover Cluster Feature and Tools for Windows Server 2012). Компоненты и средства необходимо установить на всех узлах кластера.  
  
2.  Установить SQL Server 2016 с компонентом Integration Services (SSIS) на каждом узле кластера.  
  
3.  Включить функцию AlwaysOn для каждого экземпляра SQL Server. Более подробные сведения см. в разделе [Включение групп доступности AlwaysOn](https://msdn.microsoft.com/library/ff878259.aspx) .  
  
##  <a name="a-namefirsttimea-configure-ssis-support-for-always-on"></a><a name="Firsttime"></a> Настройка поддержки служб SSIS для AlwaysOn  
  
-   [Шаг 1. Создание каталога служб Integration Services](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step1)  
  
-   [Шаг 2. Добавление SSISDB в группу доступности AlwaysOn](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step2)  
  
-   [Шаг 3. Включение поддержки служб SSIS для AlwaysOn](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step3)  
  
> [!IMPORTANT]  
>  -   Эти действия необходимо выполнить на **основном узле** группы доступности.  
> -   После добавления SSISDB в группу AlwaysOn необходимо включить **поддержку SSIS для AlwaysOn** .  
  
###  <a name="a-namestep1a-step-1-create-integration-services-catalog"></a><a name="Step1"></a> Шаг 1. Создание каталога служб Integration Services  
  
1.  Запустите **SQL Server Management Studio** и подключитесь к экземпляру SQL Server в кластере, который нужно задать в качестве **основного узла** группы высокой доступности AlwaysOn для SSISDB.  
  
2.  В обозревателе объектов разверните узел сервера, щелкните правой кнопкой мыши узел **Каталоги служб Integration Services** и выберите пункт **Создать каталог**.  
  
3.  Установите флажок **Включить интеграцию со средой CLR**. Каталог использует хранимые процедуры CLR.  
  
4.  Щелкните **Включить автоматическое выполнение хранимой процедуры служб Integration Services при запуске SQL Server** , чтобы хранимая процедура [catalog.startup](https://msdn.microsoft.com/library/hh230984.aspx) выполнялась каждый раз при перезапуске экземпляра сервера служб SSIS. Хранимая процедура осуществляет обслуживание состояния операций для каталога SSISDB. Она исправляет состояние любых пакетов, выполнявшихся в момент отключения экземпляра сервера служб SSIS.  
  
5.  Введите **пароль**и нажмите кнопку **ОК**. Этот пароль защищает главный ключ базы данных, используемый для шифрования данных каталога. Сохраните пароль в надежном месте. Рекомендуется также создать резервную копию главного ключа базы данных. Дополнительные сведения см. в статье [Back Up a Database Master Key](https://msdn.microsoft.com/library/aa337546.aspx).  
  
###  <a name="a-namestep2a-step-2-add-ssisdb-to-an-always-on-availability-group"></a><a name="Step2"></a> Шаг 2. Добавление SSISDB в группу доступности AlwaysOn  
 Процедура добавления базы данных SSISDB в группу доступности AlwaysOn практически не отличается от добавления другой базы данных пользователей в группу доступности. См. раздел [Использование мастера групп доступности](https://msdn.microsoft.com/library/hh403415.aspx).  
  
 Необходимо ввести пароль, указанный при создании каталога служб SSIS на странице **Выбор баз данных** мастера **создания групп доступности** .  
  
 ![New Availability Group](../../integration-services/service/media/ssis-newavailabilitygroup.png "New Availability Group")  
  
###  <a name="a-namestep3a-step-3-enable-ssis-support-for-always-on"></a><a name="Step3"></a> Шаг 3. Включение поддержки служб SSIS для AlwaysOn  
 После создания каталога служб Integration Service щелкните правой кнопкой мыши узел **Каталоги служб Integration Service** и выберите команду **Включить поддержку AlwaysOn**. Вы должны увидеть следующие диалоговое окно **Включение поддержки AlwaysOn** . Если этот пункт меню неактивен, убедитесь, что установлены все необходимые компоненты, и нажмите кнопку **Обновить**.  
  
 ![Enable Support for AlwaysOn](../../integration-services/service/media/ssis-enablesupportforalwayson.png "Enable Support for AlwaysOn")  
  
> [!WARNING]  
>  Автоматическая отработка отказа базы данных SSISDB поддерживается только после включения поддержки служб SSIS для AlwaysOn.  
  
 Вторичные реплики, добавленные из группы доступности AlwayOn, будут отображены в таблице. Установите флажок **Подключить** для каждой реплики в списке и введите учетные данные для подключения к реплике. Для включения поддержки служб SSIS для AlwaysOn учетная запись пользователя должна входить в группу системных администраторов на каждой реплике. После успешного подключения к каждой реплике нажмите кнопку **ОК** , чтобы включить поддержку служб SSIS для AlwaysOn.  
  
##  <a name="a-nameupgradea-upgrading-ssisdb-in-an-availability-group"></a><a name="Upgrade"></a> Обновление SSISDB в группе доступности  
 Если вы обновляете SQL Server с предыдущей версии и SSISDB находится в группе доступности AlwaysOn, обновление может блокироваться правилом "Проверка SSISDB в группе доступности AlwaysOn". Эта блокировка связана с тем, что обновление выполняется в однопользовательском режиме, а база данных доступности должна быть многопользовательской. Таким образом, во время обновления или применения исправлений все базы данных доступности, включая SSISDB, переводятся в автономный режим и не обновляются или исправляются. Чтобы продолжить обновление, необходимо сначала удалить SSISDB из группы доступности, затем обновить каждый узел или применить к нему исправление, а после этого добавить SSISDB обратно в группу доступности.  
  
 Если обновление заблокировано правилом "Проверка SSISDB в группе доступности AlwaysOn", нужно выполнить следующие действия, чтобы обновить SQL Server.  
  
1.  Удалите базу данных SSISDB из группы доступности. Дополнительные сведения см. в разделах [Удаление базы данных-получателя из группы доступности (SQL Server)](../../database-engine/availability-groups/windows/remove-a-secondary-database-from-an-availability-group-sql-server.md) и [Удаление базы данных-источника из группы доступности (SQL Server)](../../database-engine/availability-groups/windows/remove-a-primary-database-from-an-availability-group-sql-server.md).  
  
2.  В мастере обновления щелкните **Выполнить повторно**. Правило "Проверка SSISDB в группе доступности AlwaysOn" будет соблюдено.  
  
3.  Нажмите кнопку **Далее** , чтобы продолжить обновление.  
  
4.  После обновления всех узлов добавьте базу данных SSISDB обратно в группу доступности AlwaysOn. Дополнительные сведения см. в разделе [Добавление базы данных в группу доступности (SQL Server)](../../database-engine/availability-groups/windows/add-a-database-to-an-availability-group-sql-server.md).  
  
 Если при обновлении SQL Server блокировка применена не была и SSISDB находится в группе доступности AlwaysOn, необходимо отдельно обновить SSISDB после обновления компонента SQL Server Database Engine. Используйте мастер обновления служб SSIS для обновления SSISDB, как описано в следующей процедуре.  
  
1.  Переместите базу данных SSISDB из группы доступности или удалите группу доступности, если SSISDB является единственной базой данных в группе доступности. Для выполнения этой задачи необходимо запустить **SQL Server Management Studio** на **основном узле** группы доступности.  
  
2.  Удалите базу данных SSISDB со всех **узлов реплики**.  
  
3.  Обновите базу данных SSISDB на **основном узле**. В**обозревателе объектов** в SQL Server Management Studio разверните **Каталоги служб Integration Services**, щелкните правой кнопкой мыши **SSISDB**, а затем выберите команду **Обновить базу данных**. Следуйте инструкциям в **мастере обновления SSISDB** по обновлению базы данных. **Мастер обновления SSIDB** необходимо запустить локально на **основном узле**.  
  
4.  Следуйте инструкциям по добавлению SSISDB обратно в группу доступности, приведенным в пункте [Шаг 2. Добавление SSISDB в группу доступности AlwaysOn](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step2) .  
  
5.  Следуйте инструкциям в пункте [Шаг 3. Включение поддержки служб SSIS для AlwaysOn](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step3).  
  
  