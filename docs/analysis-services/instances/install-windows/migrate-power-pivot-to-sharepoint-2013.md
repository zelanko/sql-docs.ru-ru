---
title: Перенос Power Pivot в SharePoint 2013 | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8df7cc04ea0682212f5a046ca4c614e83ebe9c86
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68231869"
---
# <a name="migrate-power-pivot-to-sharepoint-2013"></a>Перенос Power Pivot в SharePoint 2013
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  
  
 SharePoint 2013 не поддерживает обновление на месте. Однако процедура **обновления присоединением базы данных поддерживается**. Это поведение отличается от обновления до версии SharePoint 2010, при котором клиент может выбрать между двумя базовыми подходами к обновлению: обновление на месте и обновление присоединением базы данных.  
  
 Если имеется установленная версия [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] , интегрированная с SharePoint 2010, нельзя обновить сервер SharePoint на месте. Однако можно выполнить миграцию баз данных содержимого и баз данных приложения службы из фермы SharePoint 2010 в ферму SharePoint 2013. В этом разделе описаны действия, необходимые, чтобы завершить обновление с переподключением баз данных и миграцию, связанные со службами [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)].  
  
### <a name="migration-overview"></a>Общие сведения о переносе  
  
|1|2|3|4|  
|-------|-------|-------|-------|  
|Подготовка фермы SharePoint 2013|Резервное копирование, копирование и восстановление баз данных.|Подключение баз данных содержимого|Перенос расписаний [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]|  
||[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|Центр администрирования SharePoint<br /><br /> Windows PowerShell|Страницы приложения SharePoint<br /><br /> Windows PowerShell|  
  
##  <a name="bkmk_prepare_sharepoint2013"></a>Подготовка фермы SharePoint 2013  
  
> [!TIP]
>  Просмотр метода проверки подлинности, для которого настроены существующие веб-приложения. В веб-приложениях для SharePoint 2013 по умолчанию применяется проверка подлинности на основе утверждений. Веб-приложения SharePoint 2010, настроенные для проверки подлинности в классическом режиме, требуют дополнительных действий при переносе баз данных из SharePoint 2010 в SharePoint 2013. Если веб-приложения настроены для проверки подлинности в классическом режиме, см. документацию по продукту SharePoint 2013.  
  
1.  Установка новой фермы SharePoint Server 2013  
  
2.  Установите экземпляр сервера [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Дополнительные сведения см. в разделе [Install Analysis Services in Power Pivot Mode](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md).  
  
3.  Запустите пакет установки [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 **spPowerPivot.msi** на каждом сервере в ферме SharePoint. Дополнительные сведения см. в разделе [Установка или удаление надстройки Power Pivot для SharePoint (SharePoint 2013)](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)необходимо быть администратором служб Analysis Services и членом локальной группы администраторов.  
  
4.  В центре администрирования SharePoint 2013 настройте приложение служб Excel для использования сервера служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint, созданного на предыдущем шаге. Дополнительные сведения см. в разделе «Настройка базовой Analysis Services SharePoint интеграции» из [Установка служб Analysis Services в режиме Power Pivot](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md).  
  
##  <a name="bkmk_backup_restore"></a>Резервное копирование, копирование и восстановление баз данных  
 Процесс «SharePoint обновление присоединением базы данных» — это последовательность шагов для резервного копирования, копирования и восстановления [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] связанного содержимого и базах данных приложения службы в ферму SharePoint 2013.  
  
1.  **Перевод базы данных только для чтения.** В [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], щелкните правой кнопкой мыши имя базы данных и нажмите кнопку **свойства**. На странице **Параметры** установите значение свойства **База данных доступна только для чтения** , равное **True**.  
  
2.  **Подавай назад:** Резервную копию каждой базы данных содержимого и базы данных приложения службы, которые требуется перенести в ферму SharePoint 2013. В [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]щелкните правой кнопкой мыши имя базы данных, выберите пункт **Задачи**, а затем команду **Создать резервную копию**.  
  
3.  Скопируйте файлы резервной копии базы данных (BAK) на целевой сервер.  
  
4.  **Восстановление:** Восстановление баз данных в назначение [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]. Этот этап можно выполнить с помощью [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
5.  **Перевод базы данных для чтения и записи.** Задайте **базы данных только для чтения** для **False**.  
  
##  <a name="bkmk_prepare_mount_databases"></a>Подготовка веб-приложений и присоединение баз данных содержимого  
 Более подробное описание следующих процедур, см. в разделе [обновление баз данных SharePoint 2010 до SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256690) (http://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
1.  **Перевод баз данных в режим «вне сети».**  
  
     Переведите в режим «вне сети» все базы данных содержимого SharePoint 2013 с помощью центра администрирования SharePoint. Базы данных содержимого заменяются базами данных, скопированными с перекрытием. Выберите оптимальную последовательность для вашей среды. Рекомендуется перевести каждую базу данных в режим «вне сети» и подключить соответствующую ей заменяющую базу данных перед переводом следующей базы данных содержимого в режим «вне сети». Еще один вариант состоит в переводе всех баз данных содержимого в режим «вне сети» в виде группы.  
  
    1.  В центре администрирования SharePoint перейдите на страницу **Управление приложением**.  
  
    2.  Нажмите кнопку **Управление базами данных содержимого**.  
  
    3.  Нажмите имя пользователя базы данных.  
  
    4.  В окне **Управление параметрами базы данных содержимого**установите значение **Состояние базы данных** , равное **Вне сети**.  
  
    5.  Выберите **Удалить базу данных содержимого**. Обратите внимание на предупреждение о том, что сайты, сохраненные в базе данных содержимого, становятся недоступными.  
  
-   **Подключение баз данных содержимого.**  
  
     Используйте командлеты PowerShell в консоли управления SharePoint 2013 для подключения перенесенной базы данных содержимого. База данных приложения службы не требует подключения, это необходимо только для баз данных содержимого. ![Содержимое, связанное с PowerShell](../../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")  
  
    ```  
    Mount-SPContentDatabase "SharePoint_Content_O14-KJSP1" -DatabaseServer "[server name]\powerpivot" -WebApplication [web application URL]  
    ```  
  
     Дополнительные сведения см. в разделе [присоединение и отсоединение баз данных содержимого (SharePoint Server 2010)](http://technet.microsoft.com/library/ff628582.aspx) (http://technet.microsoft.com/library/ff628582.aspx).  
  
     **Состояние после завершения этого шага:**  По завершении операции подключения пользователи могут видеть файлы, которые присутствовали в старой базе данных содержимого. Поэтому пользователи могут видеть и открывать книги в библиотеке документов.  
  
    -   > [!TIP]  
        >  На этом этапе в процессе переноса можно создавать новые расписания для перенесенных книг. Однако эти расписания создаются в новой базе данных приложения службы [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , а не в базе данных, скопированной из старой фермы SharePoint. Поэтому она не содержит ни одного из старых расписаний. После выполнения следующей процедуры для использования старой базы данных и переноса старых расписаний новые расписания недоступны.  
  
### <a name="troubleshoot-issues-when-you-attempt-to-mount-databases"></a>Устранение неполадок при попытке подключения баз данных  
 В этом разделе описаны возможные проблемы, обнаруживаемые при подключении базы данных.  
  
1.  **Ошибки проверки подлинности:** Если возникают ошибки, связанные с проверкой подлинности, определите, какой режим проверки подлинности, при использовании исходных веб-приложениях. Ошибка может быть вызвана несовпадением способов проверки подлинности между веб-приложением SharePoint 2013 и веб-приложением SharePoint 2010. Дополнительные сведения см. в разделе [1) Подготовка фермы SharePoint 2013](#bkmk_prepare_sharepoint2013) .  
  
2.  **Отсутствие PowerPivot.Files.** При обнаружении ошибок, связанных с отсутствием [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] библиотеки DLL, **spPowerPivot.msi** не установлена или [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] не использовалось средство настройки для настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)].  
  
##  <a name="bkmk_upgrade_powerpivot_schedules"></a>Обновление расписаний Power Pivot  
 Этот раздел содержит описание и параметры для переноса расписаний [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] . Изменение расписания — двухэтапный процесс. Сначала настройте приложение службы [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для использования перенесенной базы данных приложения службы. После этого необходимо выбрать один из двух вариантов переноса расписания.  
  
 **Настройка приложения службы на использование перенесенной базы данных приложения службы.**  
  
 Использование центра администрирования SharePoint, чтобы настроить приложение службы [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] на использование старой базы данных приложения службы, поверх которой было выполнено копирование. Служба [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] обновляет базу данных приложения службы до новой схемы.  
  
1.  В центре администрирования SharePoint выберите **Управление приложениями службы**.  
  
2.  Найти [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] службы приложения, например «по умолчанию [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] приложение службы», щелкните имя приложения службы и нажмите кнопку **свойства** на ленте SharePoint.  
  
3.  Обновление имен экземпляра сервера базы данных и базы данных. Исправление имен для базы данных, для которой была создана резервная копия, проведено копирование и восстановление. После нажатия кнопки **ОК**обновляется база данных приложения службы. Ошибки будут записаны в журнал ULS.  
  
 **Обновление расписаний [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]**  
  
 Чтобы перенести расписания обновления, настройте приложение службы [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] .  
  
-   **Перенос расписаний, вариант 1. Администратор фермы SharePoint**  
  
    1.  В сеансе управления SharePoint 2013 `Set-PowerPivotServiceApplication` командлет с `-StartMigratingRefreshSchedules` переключатель для включения автоматического переноса по запросу расписания ![содержимое, связанное с PowerShell](../../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "содержимое,связанноесPowerShell"). При использовании следующего сценария Windows PowerShell предполагается наличие только одного приложения службы [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] .  
  
        ```  
        $app=Get-PowerPivotServiceApplication  
        Set-PowerPivotServiceApplication $app -StartMigratingRefreshSchedules  
        ```  
  
         После выполнения скрипта Windows PowerShell расписания активны и запускаются в следующий плановый момент времени. Однако одна из страниц обновления расписания не переходит в состояние «включено». После первого запуска расписания выполняется его перенос и на странице обновления расписания значение **Включено**  становится равным true.  
  
    2.  Чтобы проверить текущее значение свойства StartMigratingRefreshSchedules, выполните следующий скрипт PowerShell. Этот сценарий обрабатывает в цикле все объекты приложения службы [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] и отображает имя и значения свойств.  
  
        ```  
        $apps = Get-PowerPivotServiceApplication  
        foreach ($app in $apps){}  
        Get-PowerPivotServiceApplication $appp | format-table -property displayname,id,StartMigratingRefreshSchedules  
        ```  
  
     **Перенос расписаний, вариант 2. Пользователь обновляет каждую книгу**  
  
    1.  Еще один способ переноса расписания состоит в том, чтобы включить обновление расписания для каждой книги. Перейдите к библиотеке документов, которая содержит книги.  
  
    2.  Откройте контекстное меню книги и щелкните **Управление обновлением данных [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]** .  
  
    3.  В разделе **Обновление по расписанию** щелкните **Включить**.  
  
    4.  Можно выбрать **Кроме того, обновить данные как можно скорее**. Этот параметр добавляет один экземпляр обновления в очередь после нажатия кнопки «ОК». В соответствующий момент времени все равно запускается обычное расписание обновления.  
  
    5.  Нажмите кнопку **ОК**. На странице расписания обновления отображается журнал обновления и в обычное время активизируется расписание.  
  
 **Книги SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]**  
  
-   Книги SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] не обновляются автоматически при их использовании в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)][!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint 2013. После переноса базы данных содержимого, которая содержит книги 2008 R2, можно использовать книги, но обновление расписаний не происходит.  
  
-   Дополнительные сведения см. в статье [Обновление книг и запланированное обновление данных (SharePoint 2013 )](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
##  <a name="bkmk_additional_resources"></a> Дополнительные ресурсы  
  
> [!NOTE]  
>  Дополнительные сведения по [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] и обновлению присоединением базы данных SharePoint см. в разделах:  
  
-   [Обновление книг и запланированное обновление данных (SharePoint 2013)](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
-   [Общие сведения о процессе обновления до SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256688) (http://go.microsoft.com/fwlink/p/?LinkId=256688).  
  
-   [Очисткой перед обновлением до SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256689) (http://go.microsoft.com/fwlink/p/?LinkId=256689).  
  
-   [Обновление баз данных SharePoint 2010 до SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256690) (http://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
  
