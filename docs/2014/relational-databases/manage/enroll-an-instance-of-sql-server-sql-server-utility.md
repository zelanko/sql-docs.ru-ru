---
title: Регистрация экземпляра SQL Server (служебная программа SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.makemanaged.agentaccount.F1
- SQL12.SWB.makemanaged.Summary.F1
- SQL12.SWB.makemanaged.enrolling.F1
- SQL12.SWB.makemanaged.progress.F1
- SQL12.SWB.makemanaged.instancename.F1
- SQL12.SWB.makemanaged.welcome.F1
- SQL12.SWB.makemanaged.validation.F1
helpviewer_keywords:
- Enroll instance
ms.assetid: a801c619-611b-4e82-a8d8-d1e01691b7a1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 98350d5d68990fdf31d42bacff2fc2ebb77c116b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62468276"
---
# <a name="enroll-an-instance-of-sql-server-sql-server-utility"></a>Регистрация экземпляра SQL Server (служебная программа SQL Server)
  Зарегистрируйте экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в существующей программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для наблюдения за его производительностью и конфигурацией как управляемого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Точка управления служебной программой (UCP) выполняет сбор данных о конфигурации и производительности от управляемых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] каждые 15 минут. Эти сведения хранятся в хранилище данных управления для программы (UMDW) в UCP, имя файла UMDW — sysutility_mdw. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сравниваются с политиками с целью определения того, в каких местах отмечается нехватка ресурсов, а также возможностей консолидации.  
  
 В этом выпуске точка управления служебной программой и все управляемые экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны удовлетворять следующим требованиям.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должна быть 10.50 или более поздняя.  
  
-   Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен иметь тип компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility должна работать в пределах одного домена Windows, либо в нескольких доменах с двусторонними отношениями доверия.  
  
-   Учетные записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в точке управления служебной программой и все управляемые экземпляры SQL Server должны предоставлять разрешение на чтение для пользователей в Active Directory.  
  
-   Регистрируемый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может быть Azure SQL.  
  
 В этом выпуске точка управления служебной программой должна удовлетворять следующим требованиям.  
  
-   Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен иметь поддерживаемый выпуск. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
-   Рекомендуется размещать точку управления служебной программой на экземпляре SQL Server, учитывающего регистр.  
  
-   Учтите приведенные ниже рекомендации по планированию ресурсных затрат для компьютера точки управления служебной программой.  
  
    -   Обычно место на диске, используемое базой данных UMDW (sysutility_mdw) в точке управления служебной программой, равно примерно 2 ГБ на один управляемый экземпляр SQL Server в год. Оценочные значения могут различаться в зависимости от количества баз данных и системных объектов, собираемых управляемым экземпляром. Темпы увеличения места на диске, занимаемого sysutility_mdw, наиболее высоки в течение первых двух дней.  
  
    -   Обычно место на диске, используемое базой данных msdb на пункте управления программой, равно примерно 20 МБ на один управляемый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Обратите внимание, что оценочные значения могут различаться в зависимости от политик загрузки ресурсов, а также количества баз данных и системных объектов, собираемых управляемым экземпляром. Как правило, место на диске используется более интенсивно по мере увеличения числа нарушений политики, а также по мере увеличения времени перемещения для непостоянных ресурсов.  
  
    -   Обратите внимание, что удаление управляемого экземпляра из пункта управления программой не приведет к уменьшению объема места на диске, занимаемого базами данных UCP, до истечения сроков хранения данных в управляемом экземпляре.  
  
 В этой версии все управляемые экземпляры SQL Server должны удовлетворять приведенным ниже требованиям.  
  
-   Если пункт управления программой расположен на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]с учетом регистра, рекомендуется, чтобы на управляемых экземплярах SQL Server также учитывался регистр.  
  
-   Данные FILESTREAM не поддерживаются при наблюдении с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.  
  
 Дополнительные сведения см. в разделе [спецификации максимально допустимых параметров SQL Server](../../sql-server/maximum-capacity-specifications-for-sql-server.md) и [функции, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Дополнительные сведения об основных понятиях служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md).  
  
> [!IMPORTANT]  
>  Набор элементов сбора служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживается параллельно с наборами элементов сбора, не касающимися служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Таким образом, управляемый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно наблюдать по другим наборам элементов сбора, поскольку он является элементом служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Следует, однако, отметить, что все наборы элементов сбора, находящиеся в управляемом экземпляре, передают свои данные в хранилище данных управления программы. Дополнительные сведения см. в разделах [Замечания по выполнению программы, не относящиеся к прочим наборам элементов сбора на том же экземпляре SQL Server](run-utility-and-non-utility-collection-sets-on-same-sql-instance.md) и [Настройка хранилища данных для точки управления служебной программой (служебная программа SQL Server)](configure-your-utility-control-point-data-warehouse-sql-server-utility.md).  
  
## <a name="wizard-steps"></a>Шаги мастера  
 В следующих разделах содержатся подробные сведения о каждой странице потока операций мастера. Щелкните ссылку, чтобы перейти в мастере к подробностям, относящимся к этой странице. Дополнительные сведения о скрипте PowerShell этой операции см. в [примере](#PowerShell_enroll).  
  
-   [Введение в мастер регистрации экземпляров](#Welcome)  
  
-   [Укажите экземпляр SQL Server](#Instance_name)  
  
-   [Диалоговое окно соединения](#Connection_dialog)  
  
-   [Учетная запись набора элементов сбора служебной программы](#Proxy_configuration)  
  
-   [Проверка экземпляра SQL Server](#Validation_rules)  
  
-   [Сводка регистрации экземпляров](#Summary)  
  
-   [Регистрация экземпляра SQL Server](#Enrolling)  
  
##  <a name="Welcome"></a> Введение в мастер регистрации экземпляров  
 Чтобы запустить мастер, раскройте дерево обозревателя программ в пункте управления программой, щелкните правой кнопкой мыши узел **Управляемые экземпляры** и выберите команду **Добавить экземпляр...**  
  
 Чтобы продолжить, нажмите кнопку **Далее**.  
  
##  <a name="Instance_name"></a> Укажите экземпляр SQL Server  
 Чтобы выбрать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в диалоговом окне соединения, нажмите кнопку **Подключить...**. Введите имя компьютера и имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в формате "имя_компьютера\имя_экземпляра". Дополнительные сведения см. в статье [Соединение с сервером (компонент Database Engine)](../../ssms/f1-help/connect-to-server-database-engine.md).  
  
 Чтобы продолжить, нажмите кнопку **Далее**.  
  
##  <a name="Connection_dialog"></a> Диалоговое окно соединения  
 Проверьте в диалоговом окне «Соединение с сервером» тип сервера, имя компьютера и сведения обо имени экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье [Соединение с сервером (компонент Database Engine)](../../ssms/f1-help/connect-to-server-database-engine.md).  
  
> [!NOTE]  
>  Если соединение зашифровано, используется зашифрованное соединение. Если соединение не зашифровано, то программа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установит соединение повторно с использованием зашифрованного соединения.  
  
 Для продолжения нажмите кнопку **Подключить...**.  
  
##  <a name="Proxy_configuration"></a> Учетная запись набора элементов сбора служебной программы  
 Укажите учетную запись домена Windows для выполнения набора элементов сбора служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Эта учетная запись используется как учетная запись-посредник агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для набора элементов сбора служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Можно также использовать имеющуюся служебную учетную запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы требования проверки были удовлетворены, следуйте приведенным ниже рекомендациям по настройке учетной записи.  
  
 Если выбран вариант со служебной учетной записью службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Служебная учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не должна быть встроенной учетной записью домена Windows (например, LocalSystem, NetworkService или LocalService).  
  
 Чтобы продолжить, нажмите кнопку **Далее**.  
  
##  <a name="Validation_rules"></a> Проверка экземпляра SQL Server  
 В этой версии для регистрации экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны соблюдаться следующие условия.  
  
|Условие|Действие по исправлению|  
|---------------|-----------------------|  
|Необходимо обладать правами администратора для указанного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и точки управления служебной программой.|Войдите в систему от учетной записи, имеющей права администратора на указанном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и точке управления служебной программой.|  
|Выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен поддерживать регистрацию экземпляров.|Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).|  
|В точке управления служебной программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должна быть включена поддержка TCP/IP.|Включите TCP/IP в точке управления служебной программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не должен быть зарегистрирован в какой-либо другой точка управления служебной программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|Если указанный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] уже управляется как часть существующей программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то его нельзя будет зарегистрировать в другой точке управления служебной программой.|  
|Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не должен уже являться точкой управления служебной программой.|Если указанный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] уже является точкой управления служебной программой, отличающейся от той, с которой установлено соединение, то выполнить регистрацию в этой точке управления служебной программой будет нельзя.|  
|На экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны быть установлены наборы элементов сбора служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|Переустановите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Наборы элементов сбора на указанном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны быть остановлены.|Наборы элементов сбора должны быть остановлены на указанном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если сборщик данных отключен, включите его, остановите все работающие наборы элементов сбора, а затем снова запустите правила проверки для операции создания точки управления служебной программой.<br /><br /> Включение сборщика данных:<br /><br /> В обозревателе объектов раскройте узел **Управление** .<br /><br /> Щелкните правой кнопкой мыши **Сбор данных**, затем выберите **Включить сбор данных**.<br /><br /> Остановка набора элементов сбора:<br /><br /> В обозревателе объектов разверните узел **Управление**, затем узел **Сбор данных**и узел &lt;ui&gt;Наборы элементов сбора системных данных&lt;/ui&gt;.<br /><br /> Щелкните правой кнопкой мыши набор элементов сбора, который необходимо остановить, и выберите команду **Остановить набор сбора данных**.<br /><br /> Результат этого действия будет отображен в окне сообщения, а красный круг на значке набора элементов сбора означает его остановку.|  
|Служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должна быть запущена на указанном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|Запустите службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на указанном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если указанный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является экземпляром отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , настройте ручной запуск службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В противном случае настройте автоматический запуск службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|В точке управления служебной программой должна быть запущена служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|Запустите службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в точке управления служебной программой. Если точка управления служебной программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является экземпляром отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , настройте ручной запуск службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В противном случае настройте автоматический запуск службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|WMI должна быть правильно настроена.|Сведения об устранении неполадок настройки WMI см. в статье [Устранение неполадок служебной программы SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md).|  
|Учетная запись-посредник агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должна быть учетной записью действующего домена Windows в точке управления служебной программой.|Укажите допустимую учетную запись домена Windows. Чтобы проверить допустимость учетной записи, войдите в точку управления служебной программой с помощью этой учетной записи домена Windows.|  
|Если выбран параметр учетной записи-посредника, то учетная запись-посредник агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должна быть допустимой учетной записью домена Windows на указанном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Укажите допустимую учетную запись домена Windows. Чтобы проверить допустимость учетной записи, войдите на указанный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью этой учетной записи домена Windows.|  
|Учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может быть встроенной учетной записью, как, например, «Сетевая служба».|Переназначьте учетную запись на учетную запись домена Windows. Чтобы проверить допустимость учетной записи, войдите на указанный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью этой учетной записи домена Windows.|  
|Учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должна быть учетной записью действующего домена Windows в точке управления служебной программой.|Укажите допустимую учетную запись домена Windows. Чтобы проверить допустимость учетной записи, войдите в точку управления служебной программой с помощью этой учетной записи домена Windows.|  
|Если выбран параметр учетной записи службы, то учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должна быть допустимой учетной записью домена Windows на указанном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Укажите допустимую учетную запись домена Windows. Чтобы проверить допустимость учетной записи, войдите на указанный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью этой учетной записи домена Windows.|  
  
 Если результаты проверки содержат невыполненные условия, устраните критические препятствия и нажмите кнопку **Повторная проверка** , чтобы проверить конфигурацию компьютера.  
  
 Чтобы сохранить отчет о проверке, нажмите кнопку **Сохранить отчет** и укажите расположение для файла.  
  
 Чтобы продолжить, нажмите кнопку **Далее**.  
  
##  <a name="Summary"></a> Сводка регистрации экземпляров  
 На странице со сводкой приведены сведения об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , добавляемом в программу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Параметры управляемого экземпляра:  
  
-   Имя экземпляра SQL Server: "Имя_компьютера\имя_экземпляра"  
  
-   Учетная запись набора элементов сбора служебной программы: Имя_домена\имя_пользователя  
  
 Чтобы продолжить, нажмите кнопку **Далее**.  
  
##  <a name="Enrolling"></a> Регистрация экземпляра SQL Server  
 На странице регистрации отображается состояние операции.  
  
-   Подготовка экземпляра к регистрации.  
  
-   Создание каталога кэша для собранных данных.  
  
-   Настройка набора элементов сбора служебной программы.  
  
 Чтобы сохранить отчет об операции регистрации, нажмите кнопку **Сохранить отчет** и укажите местоположение для файла.  
  
 Чтобы завершить работу мастера, нажмите кнопку **Готово**.  
  
> [!NOTE]  
>  Если для подключения к экземпляру SQL Server используется проверка подлинности SQL Server, а указанная при этом учетная запись-посредник принадлежит домену Active Directory, отличному от домена, в котором находится точка управления служебной программой, то проверка экземпляра завершится успешно, но во время операции регистрации произойдет ошибка и появится следующее сообщение об ошибке:  
>   
>  Возникло исключение при выполнении пакета или инструкции Transact-SQL. (Microsoft.SqlServer.ConnectionInfo)  
>   
>  Дополнительные сведения:  Не удалось получить сведения о пользователе/группе Windows NT "\<Имя_домена\имя_учетной_записи >", код ошибки 0x5. (Microsoft SQL Server, ошибка: 15404)  
>   
>  Дополнительные сведения об устранении этой неполадки см. в статье [Устранение неполадок служебной программы SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md).  
  
> [!IMPORTANT]  
>  Не меняйте свойства набора элементов сбора "Сведения о программе" на управляемом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не включайте и не выключайте сбор данных вручную, так как сбор данных происходит под управлением задания агента программы.  
  
 Завершив работу мастера регистрации экземпляра, щелкните узел **Управляемые экземпляры** на панели **Навигация проводника служебной программы** в среде SSMS. Зарегистрированные экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображаются в списке на панели **Содержимое обозревателя служебных программ** .  
  
 Процесс сбора данных начнется сразу, однако до появления первых сведений на панели и в точках обзора на панели мониторинга содержимого проводника служебной программы может пройти до 30 минут. Сбор данных выполняется каждые 15 минут. Чтобы обновить данные, щелкните правой кнопкой мыши узел **Управляемые экземпляры** на панели **Навигация обозревателя программ** и выберите команду **Обновить**, либо щелкните правой кнопкой мыши имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в представлении списка и выберите **Обновить**.  
  
 Чтобы удалить управляемые экземпляры из служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на панели **Навигация обозревателя программ** выберите **Управляемые экземпляры** , чтобы заполнить представление списка управляемых экземпляров, в представлении списка на панели [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Содержимое обозревателя программ **щелкните правой кнопкой мыши имя экземпляра** и выберите команду **Удалить экземпляр из списка управляемых**.  
  
##  <a name="PowerShell_enroll"></a> Регистрация экземпляра SQL Server с помощью PowerShell  
 В следующем примере показана регистрация экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в существующей служебной программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```  
> $UtilityInstance = new-object -Type Microsoft.SqlServer.Management.Smo.Server "ComputerName\UCP-Name";  
> $SqlStoreConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $UtilityInstance.ConnectionContext.SqlConnectionObject;  
> $Utility = [Microsoft.SqlServer.Management.Utility.Utility]::Connect($SqlStoreConnection);  
> $Instance = new-object -Type Microsoft.SqlServer.Management.Smo.Server "ComputerName\ManagedInstanceName";  
> $InstanceConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $Instance.ConnectionContext.SqlConnectionObject;  
> $ManagedInstance = $Utility.EnrollInstance($InstanceConnection, "ProxyAccount", "ProxyPassword");  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md)   
 [Наблюдение за экземплярами SQL Server в служебной программе SQL Server](monitor-instances-of-sql-server-in-the-sql-server-utility.md)   
 [Устранение неполадок служебной программы SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
