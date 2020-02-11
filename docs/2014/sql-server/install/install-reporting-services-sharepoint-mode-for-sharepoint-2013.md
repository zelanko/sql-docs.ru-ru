---
title: Установка Reporting Services режима SharePoint для SharePoint 2013 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: b29d0f45-0068-4c84-bd7e-5b8a9cd1b538
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 8874d4c57e2fb7b94e4efac44c90e93865d2b40f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "72798335"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2013"></a>Установка служб Reporting Services в режиме SharePoint для SharePoint 2013
  В данном разделе подробно описываются процедуры установки одиночного сервера [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме SharePoint. Эти шаги охватывают запуск мастера установки SQL Server, а также выполнение дополнительных задач по настройке с использованием центра администрирования SharePoint. В разделе также можно ознакомиться с отдельными процедурами обновления существующей установки, например с созданием приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; **Примечание.** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] режим интеграции с SharePoint **не** поддерживает мультитенантность SharePoint Server.|  
  
 Сведения о добавлении дополнительных серверов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в существующую ферму см. в следующих разделах:  
  
-   [Добавление дополнительного сервера отчетов в ферму &#40;горизонтальное масштабирование SSRS&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
-   [Добавление дополнительного клиентского веб-интерфейса служб Reporting Services в ферме](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 Установка на одиночный сервер полезна в сценариях разработки и тестирования, но не рекомендуется для рабочей среды.  
  
 **В этом разделе:**  
  
-   [Пример развертывания на одном сервере](#bkmk_singleserver)  
  
-   [Настройка учетных записей](#bkmk_setupaccounts)  
  
-   [Шаг 1. Установка Reporting Services сервера отчетов в режиме интеграции с SharePoint](#bkmk_install_SSRS)  
  
-   [Шаг 2. Регистрация и запуск службы Reporting Services SharePoint](#bkmk_install_SSRS_sharedservice)  
  
-   [Шаг 3. Создание приложения службы Reporting Services](#bkmk_create_serrviceapplication)  
  
-   [Шаг 4. Активация компонента семейства веб-сайтов Power View.](#bkmk_powerview)  
  
-   [Сценарий Windows PowerShell для шагов 1-4](#bkmk_full_script)  
  
-   [Дополнительная настройка](#bkmk_additional_config) , включая подготовку подписок и оповещений, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] типы содержимого и настройку служб Excel для использования сервера Analysis Services.  
  
-   [Проверка установки](#bkmk_verify_installation)  
  
##  <a name="bkmk_singleserver"></a>Пример развертывания на одном сервере  
 Установка на одиночный сервер полезна в сценариях разработки и тестирования, но не рекомендуется для рабочей среды. Под средой с одиночным сервером подразумевается один компьютер, на котором установлен пакет SharePoint, и компоненты [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , установленные на том же компьютере. В разделе не рассматриваются масштабные конфигурации с несколькими серверами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 На следующей диаграмме показаны компоненты, которые входят в состав развертывания [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] одиночного сервера.  
  
|||  
|-|-|  
|**одного**|Служба SharePoint, установленная из экземпляра SQL Server. Можно создать одно или несколько приложений службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|**открыт**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Надстройка служб для продуктов SharePoint предоставляет компоненты пользовательского интерфейса на серверах SharePoint.|  
|**(3)**|Приложение службы Excel используется в Power View и PowerPivot.|  
|**четырех**|Приложение службы PowerPivot|  
  
 ![Развертывание одиночного сервера в режиме интеграции служб SSRS с SharePoint](../../../2014/sql-server/install/media/rs-sharepoint-1server-deployment.gif "Развертывание одиночного сервера в режиме интеграции служб SSRS с SharePoint")  
  
> [!TIP]  
>  Более сложные примеры развертывания см. в разделе [Топологии развертывания для компонентов бизнес-аналитики SQL Server в SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).  
  
##  <a name="bkmk_setupaccounts"></a>Настройка учетных записей  
 В этом разделе описываются учетные записи и разрешения, используемые для основных шагов развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.  
  
 **Установка и регистрация [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] службы:**  
  
-   Текущая учетная запись во время установки (называемая учетной записью установки) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint должна иметь права администратора на локальном компьютере. Если установка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] выполняется после установки SharePoint и учетная запись установки также входит в группу администраторов фермы SharePoint, то [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] при установке будет зарегистрирована [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] служба. Если установка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] выполняется до установки SharePoint или учетная запись установки не входит в группу администраторов фермы, Служба регистрируется вручную. Обратитесь к разделу [Этап 2. Регистрация и запуск службы Reporting Services в SharePoint](#bkmk_install_SSRS_sharedservice).  
  
 **Создание [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] приложений службы**  
  
-   После установки и регистрации службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] создайте одно или несколько приложений службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Для создания приложения службы Reporting Services учетную запись службы фермы SharePoint необходимо временно включить в группу локальных администраторов. Дополнительные сведения о разрешениях учетной записи SharePoint 2013 см. [в разделе разрешения учетной записи и параметры безопасности в sharepoint 2013](https://technet.microsoft.com/library/cc678863.aspx) (https://technet.microsoft.com/library/cc678863.aspx).  
  
     В целях безопасности не рекомендуется, чтобы учетные записи администраторов фермы SharePoint также являлись учетными записями администраторов локальной операционной системы. Если вы добавили учетную запись администратора фермы в группу локальных администраторов в ходе процесса настройки, рекомендуется удалить учетную запись из группы локальных администраторов после завершения установки.  
  
##  <a name="bkmk_install_SSRS"></a>Шаг 1. Установка Reporting Services сервера отчетов в режиме интеграции с SharePoint  
 На этом шаге устанавливается сервер отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint и надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint. В зависимости от продуктов, уже установленных на компьютере, могут не отображаться некоторые страницы установки, описанные в следующих разделах.  
  
1.  Запустите мастер установки SQL Server (Setup.exe).  
  
2.  Нажмите кнопку **Установка** в левой части мастера, затем выберите пункт **Новая изолированная установка SQL Server или добавление функций в существующую установку**.  
  
3.  Нажмите кнопку **ОК** на странице **Правила поддержки установки** в предположении, что все правила выполнены.  
  
4.  Нажмите кнопку **Установить** на странице **Файлы поддержки установки** . В зависимости от продуктов, уже установленных на компьютере, может появиться следующее сообщение:  
  
    -   "Для одного или нескольких необходимых файлов существуют незавершенные операции. После завершения процесса установки следует перезагрузить компьютер".  
  
    -   Нажмите кнопку **ОК**.  
  
5.  Нажмите кнопку **Далее** после того, как будут установлены файлы поддержки, а на странице **Правила поддержки** отобразится состояние **Выполнено**. Просмотрите все предупреждения и определите критические препятствия.  
  
6.  На странице **Тип установки** нажмите **Добавить компоненты в существующий экземпляр SQL Server 2014**. Выберите нужный экземпляр в раскрывающемся списке и нажмите кнопку **Далее**.  
  
7.  Если отображается страница **Ключ продукта**, введите ключ или примите выбранный по умолчанию вариант "Enterprise (ознакомительная версия)".  
  
     Щелкните **Далее**.  
  
8.  Если отображаются условия лицензионного соглашения, ознакомьтесь с условиями лицензии и примите их. Корпорация Майкрософт будет признательна вам за согласие отправлять данные об использовании компонентов, которые помогут улучшить функции и поддержку продукта.  
  
     Щелкните **Далее**.  
  
9. Если отображается страница **Роль установки** , выберите **Установка компонентов SQL Server**.  
  
     Нажмите кнопку **Далее**.  
  
     ![Установка компонентов SQL Server для роли установки](../../../2014/sql-server/install/media/rs-setuprole.gif "Установка компонентов SQL Server для роли установки")  
  
10. Выберите следующие компоненты на странице **Выбор компонентов** :  
  
    -   **Reporting Services — SharePoint**  
  
    -   **Reporting Services надстройку для продуктов SharePoint**.  
  
         ![Примечание](../../../2014/reporting-services/media/rs-fyinote.png "note") . Параметр мастера установки для установки надстройки является новым в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] выпуске.  
  
    -   Если экземпляр компонента SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)]еще не установлен, для завершения установки можно также выбрать **Службы ядра СУБД** и **Полный набор средств управления** .  
  
     Щелкните **Далее**.  
  
     ![Выбор компонентов служб SSRS для режима интеграции с SharePoint](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "Выбор компонентов служб SSRS для режима интеграции с SharePoint")  
  
11. Если открылась страница **Правила установки** . Просмотрите все предупреждения и определите критические препятствия. Затем нажмите кнопку **Далее** .  
  
12. Если выбрана установка служб Database Engine, примите экземпляр **MSSQLSERVER** по умолчанию на странице **Настройка экземпляра** и нажмите кнопку **Далее**.  
  
     ![Примечание](../../../2014/reporting-services/media/rs-fyinote.png "note") . Архитектура службы Reporting Services SharePoint не основана на SQL Server "экземпляр", как в предыдущей архитектуре Reporting Services.  
  
13. Просмотрите страницу **Требования к месту на диске** и нажмите **Далее**.  
  
14. Если отображается страница **Настройка сервера** , введите соответствующие учетные данные. Если необходимо использовать функции предупреждения об изменении данных или подписки на данные служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , необходимо изменить **Тип запуска** для агента SQL Server на **Автоматический**. Страница **Конфигурация сервера** может не отображаться в зависимости от продуктов, уже установленных на компьютере.  
  
     Щелкните **Далее**.  
  
15. Если выбрана установка служб ядра СУБД, откроется страница **Настройка компонента Database Engine** , на которой следует добавить соответствующие учетные записи в список администраторов SQL и нажать кнопку **Далее**.  
  
16. На странице **Настройка служб Reporting Services** будет выбран вариант **Только установка** . Этот параметр устанавливает файлы сервера отчетов и не настраивает среду SharePoint для [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
    > [!NOTE]  
    >  По завершении установки SQL Server используйте сведения в других подразделах этого раздела для настройки среды SharePoint. В том числе надо будет установить общую службу [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и создать приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
     ![Мастер установки SQL Server — страница конфигурации служб SSRS](../../../2014/sql-server/install/media/rs-2012sp1-setup-ssrs-configpage-with-circles.gif "Мастер установки SQL Server — страница конфигурации служб SSRS")  
  
17. Помогите компании Майкрософт улучшить работу функций и служб SQL Server, установив флажок в знак согласия отправлять отчеты об ошибках на странице **Отчеты об ошибках** .  
  
     Щелкните **Далее**.  
  
18. Просмотрите возможные предупреждения и нажмите кнопку **Далее** на странице **Правила настройки установки** .  
  
19. На странице **Все готово для установки** просмотрите сводку по установке и нажмите кнопку **Далее**. Сводка должна охватывать дочерний сайт **Службы Reporting Services в режиме интеграции с SharePoint** , который покажет значение **SharePointFilesOnlyMode**. Нажмите кнопку **Установить**.  
  
20. Для выполнения программы установки требуется несколько минут. Появится страница **Готово** с перечислением функций и состояния каждого компонента. Возможно, откроется диалоговое окно с уведомлением о необходимости перезагрузки компьютера.  
  
##  <a name="bkmk_install_SSRS_sharedservice"></a>Шаг 2. Регистрация и запуск службы Reporting Services SharePoint  
 ![Содержимое, связанное с PowerShell](../../../2014/reporting-services/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")  
  
> [!NOTE]  
>  Если производится установка в существующую ферму SharePoint, шаги, описанные в этом подразделе, выполнять не нужно. Служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint была установлена и запущена в результате выполнения мастера установки SQL Server при изучении предыдущего раздела этого документа.  
  
 Ниже перечислены основные причины, по которым необходимо вручную зарегистрировать службу [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   Установка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] выполнена до установки SharePoint.  
  
-   Учетная запись, которая использовалась для установки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint, не принадлежит к группе администраторов фермы SharePoint. За дополнительной информацией обратитесь к разделу [Setup accounts](#bkmk_setupaccounts).  
  
 Необходимые файлы были установлены в процессе работы мастера установки SQL Server, но службы необходимо зарегистрировать в ферме SharePoint. В выпуске [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] появилась поддержка PowerShell для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме SharePoint.  
  
 Следующие шаги позволяют открыть консоль управления SharePoint и запустить командлеты.  
  
1.  Нажмите кнопку " **Пуск** "  
  
2.  Выберите группу **Продукты Microsoft SharePoint 2013** .  
  
3.  Щелкните пункт **Консоль управления SharePoint 2013** правой кнопкой мыши и выберите пункт **Запуск от имени администратора**. Примечание: команды SharePoint не распознаются в основном окне Windows PowerShell. Используйте **консоль управления SharePoint 2013**.  
  
4.  Выполните следующую команду PowerShell, чтобы установить службу SharePoint. При успешном завершении команды отобразится новая строка в консоли управления. После успешного завершения команды в оболочку управления **не возвращается сообщение** .  
  
    ```powershell
    Install-SPRSService  
    ```  
  
    > [!IMPORTANT]  
    >  Если вы появится примерно следующее сообщение об ошибке:  
    >   
    >  Install-SPRSService: термин Install-SPRSService **не распознается** как  
    > имя командлета, функции, файла скрипта или действующей программы. Узнайте о  
    > правильность написания имени или, если в команду включен путь, убедитесь, что он  
    > правильный, и повторите попытку.  
  
5.  Выполните следующую команду PowerShell, чтобы установить прокси-сервер службы: При успешном завершении команды отобразится новая строка в консоли управления. После успешного завершения команды в оболочку управления **не возвращается сообщение** .  
  
    ```powershell
    Install-SPRSServiceProxy  
    ```  
  
6.  Выполните следующую команду PowerShell, чтобы запустить службу, или просмотрите нижеперечисленные замечания для получения указаний по запуску службы из центра администрирования SharePoint.  
  
    ```powershell
    Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 Либо вы находитесь в Windows Powershell, а не в консоли управления SharePoint, либо не установлена служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. Дополнительные сведения о службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и PowerShell см. в статье [Командлеты PowerShell для режима служб SharePoint Reporting Services](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).  
  
 Можно также запустить службу из центра администрирования SharePoint, а не с помощью третьей команды PowerShell. С помощью следующих шагов можно также проверить, выполняется ли служба.  
  
1.  В центре администрирования SharePoint выберите пункт **Управление службами на сервере** в группе **Параметры системы** .  
  
2.  Найдите **Службу SQL Server Reporting Services** и нажмите кнопку **Запуск** в столбце «Действие».  
  
3.  Состояние службы Reporting Services изменится с **Остановлена** на **Запущена**. Если служба Reporting Services отсутствует в списке, используйте PowerShell для установки службы.  
  
    > [!NOTE]  
    >  Если служба Reporting Services остается в состоянии **Запускается** и не переходит в состояние **Запущена**, в диспетчере Windows Server убедитесь в том, что запущена служба "Администрирование SharePoint 2013".  
  
##  <a name="bkmk_create_serrviceapplication"></a>Шаг 3. Создание приложения службы Reporting Services  
 В этом разделе описаны шаги по созданию приложения службы и описания его свойств (в случае просмотра существующего приложения службы).  
  
1.  В центре администрирования SharePoint в группе **Управление** приложениями щелкните **Управление приложениями служб**.  
  
2.  На ленте SharePoint нажмите кнопку **Создать** .  
  
3.  В меню кнопки «Создать» выберите пункт **Приложение службы SQL Server Reporting Services**.  
  
    > [!IMPORTANT]  
    >  Если [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] параметр не отображается в списке, это **означает, что [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] общая служба не установлена**. Просмотрите предыдущий раздел, в котором описана установка службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с помощью командлетов PowerShell.  
  
4.  На странице **Создание приложения службы SQL Server Reporting Services** введите имя приложения. Если создается несколько приложений службы Reporting Services, описательные имена или контекст именования помогут упорядочить операции по администрированию и управлению.  
  
5.  В разделе **Пул приложений** создайте для данного приложения новый пул приложений (рекомендуется). Если использовать одно имя как для нового пула приложений, так и для приложения службы, дальнейшее администрирование может упроститься. Кроме того, многое зависит от количества создаваемых приложений служб и от того, требуется ли использовать несколько из них в одном пуле приложений. Рекомендации и сведения по управлению пулом приложений см. в документации по SharePoint Server.  
  
     Выберите или создайте учетную запись безопасности для пула приложений. Обязательно укажите учетную запись домена. Учетная запись пользователя домена позволяет использовать функцию управляемой учетной записи SharePoint, с помощью которой пароли и данные учетной записи можно изменять в одном месте. Учетные записи домена также требуются, если планируется расширение развернутой системы и включение дополнительных экземпляров службы, которые работают от лица одного идентификатора.  
  
6.  В поле **Сервер баз данных**можно указать текущий сервер или выбрать другой SQL Server.  
  
7.  В поле **Имя базы данных** будет содержаться значение по умолчанию `ReportingService_<guid>`, представляющее собой уникальное имя базы данных. При вводе нового значения оно должно быть уникальным. Это новая база данных, создаваемая специально для приложений служб.  
  
8.  В списке **Проверка подлинности базы данных**по умолчанию выбрано значение «Проверка подлинности Windows». Если выбран параметр **Проверка подлинности SQL**, то рекомендации по использованию этого типа проверки подлинности в развернутой системе SharePoint см. в документации SharePoint.  
  
9. В подразделе **Связь с веб-приложением** выберите веб-приложение, которое должно быть подготовлено для доступа со стороны текущего приложения службы Reporting Services. Одно приложение службы Reporting Services можно связать с одним веб-приложением. Если все имеющиеся веб-приложения уже связаны с приложением службы Reporting Services, отображается предупреждение.  
  
10. Нажмите кнопку **ОК**.  
  
11. Создание приложения службы может занять несколько минут. По завершении этого процесса отобразятся подтверждение и ссылка на страницу **Подготовка подписок и предупреждений** . Выполните шаг подготовки, если нужно использовать функции подписки и предупреждений данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе [Подготовка подписок и предупреждений для приложений служб SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).  
  
 ![Содержимое, связанное с PowerShell](../../../2014/reporting-services/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") Сведения об использовании PowerShell для создания приложения [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] службы см. в следующих статьях:  
  
-   Обратитесь к следующему разделу [Скрипт Windows PowerShell для шагов 1–4](#bkmk_full_script).  
  
-   Статья [Создание приложения службы Reporting Services с помощью PowerShell](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp).  
  
##  <a name="bkmk_powerview"></a>Шаг 4. Активация компонента семейства веб-сайтов Power View.  
 
  [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], компонент надстройки служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint, является компонентом семейства веб-сайтов. Этот компонент активируется автоматически для корневых семейств веб-сайтов, созданных после установки надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Если вы планируете использовать [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], необходимо удостовериться в том, что этот компонент активирован.  
  
 При установке надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint Server после установки SharePoint Server функции интеграции с сервером отчетов и с Power View будут активированы только для корневых семейств веб-сайтов. Для других семейств веб-сайтов необходимо активировать эти компоненты вручную.  
  
#### <a name="to-activate-or-verify-the-power-view-site-collection-feature"></a>Активация и проверка функции Power View семейства веб-сайтов.  
  
1.  При выполнении следующих шагов предполагается, что сайт SharePoint настроен для **версии взаимодействия**2013.  
  
     Откройте в браузере требуемый сайт SharePoint. Пример: http://\<имя_сервера>/sites/bi  
  
2.  Щелкните **Параметры**![Параметры SharePoint](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "Параметры SharePoint").  
  
3.  Щелкните **Параметры сайта**.  
  
4.  Щелкните **Компоненты семейства веб-сайтов** в группе **Администрирование семейства веб-сайтов**.  
  
5.  Найдите в списке **Компонент интеграции Power View** .  
  
6.  Нажмите кнопку **Активировать**. Состояние функции меняется на **Активно**.  
  
 Эта процедура выполняется для каждого семейства веб-сайтов. Дополнительные сведения см. в статье [Активация функций интеграции семейства веб-сайтов с сервером отчетов и Power View в SharePoint](../../../2014/reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md).  
  
##  <a name="bkmk_full_script"></a>Сценарий Windows PowerShell для шагов 1-4  
 Сценарии PowerShells в данном разделе эквивалентны выполнению шагов с 1 по 4 предыдущего раздела. Скрипт выполняет следующие действия.  
  
-   Устанавливает службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и прокси-сервера служб, а также запускает службу.  
  
-   Создает прокси-сервер службы с именем Reporting Services.  
  
-   Создает приложение [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] службы с именем "Reporting Services приложение".  
  
-   Включает компонент [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] для семейства веб-сайтов.  
  
 Параметры  
  
-   Обновите параметр **-Account** для прокси-сервера службы. В качестве учетной записи необходимо использовать управляемую учетную запись службы на ферме SharePoint. Дополнительные сведения см. в разделе, посвященном SharePoint, [Планирование учетных записей администрирования и служб в SharePoint 2013](https://technet.microsoft.com/library/cc263445.aspx).  
  
-   Изменяет параметр **-DatabaseServer** для приложения службы. Этот параметр является экземпляром компонента Database Engine.  
  
-   Изменяет параметр **-url** сайта, на котором необходимо включить функцию [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].  
  
 **Чтобы использовать скрипт, выполните следующие действия.**  
  
1.  Откройте Windows PowerShell с правами администратора.  
  
2.  Скопируйте следующий код в окно скрипта.  
  
3.  Измените три параметра, описанные в предыдущем разделе, а затем выполните скрипт.  
  
```powershell
#This script Configures SQL Server Reporting Services SharePoint mode  
  
$starttime = Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
  
Write-Host -ForegroundColor Green "Import the SharePoint PowerShell snappin"  
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0  
  
Write-Host -ForegroundColor Green "Install SSRS Service and Service Proxy, and start the service"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
  
    Write-Host -ForegroundColor Green "Install the Reporting Services Shared Service"  
    Install-SPRSService  
  
    Write-Host -ForegroundColor Green " Install the Reporting Services Service Proxy"  
    Install-SPRSServiceProxy  
  
    # Get the ID of the RS Service Instance and start the service   
    Write-Host -ForegroundColor Green "Start the Reporting Services Service"  
    $RS = Get-SPServiceInstance | Where {$_.TypeName -eq "SQL Server Reporting Services Service"}  
    Start-SPServiceInstance -Identity $RS.Id.ToString()  
  
    # Wait for the Reporting Services Service to start...  
    $Status = Get-SPServiceInstance $RS.Id.ToString()  
    While ($Status.Status -ne "Online")  
    {  
        Write-Host -ForegroundColor Green "SSRS Service Not Online...Current Status = " $Status.Status  
        Start-Sleep -Seconds 2  
        $Status = Get-SPServiceInstance $RS.Id.ToString()  
    }  
  
$time = Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
Write-Host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Create a new application pool and Reporting Services service application"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Write-Host -ForegroundColor Green "Create a new application pool"  
#!!!! update "-Account" with an existing Managed Service Account  
New-SPServiceApplicationPool -Name "Reporting Services" -Account "<domain>\User name>"  
$appPool = Get-SPServiceApplicationPool "Reporting Services"  
  
Write-Host -ForegroundColor Green " Create the Reporting Services Service Application"  
#!!!! Update "-DatabaseServer", an instance of the SQL Server database engine   
$rsService = New-SPRSServiceApplication -Name "Reporting Services Application" -ApplicationPool $appPool -DatabaseName "Reporting_Services_Application" -DatabaseServer "<server name>"  
  
Write-Host -ForegroundColor Green "Create the Reporting Services Service Application Proxy"  
$rsServiceProxy = New-SPRSServiceApplicationProxy -Name "Reporting Services Application Proxy" -ServiceApplication $rsService  
  
Write-Host -ForegroundColor Green "Associate service application proxy to default web site and grant web applications rights to SSRS application pool"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"     
# Associate the Reporting Services Service Applicatoin Proxy to the default web site...  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $rsServiceProxy  
  
$time=Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
Write-Host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Enable the PowerView and reportserver site features"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
#!!!! update "-url"  of the site where you want the features enabled  
Enable-SPfeature -identity "powerview" -Url http://server/sites/bi  
Enable-SPfeature -identity "reportserver" -Url http://server/sites/bi  
  
####To Verify, you can run the following:  
#Get-SPRSServiceApplication  
#Get-SPServiceApplicationPool | where {$_.name -like "reporting*"}  
#Get-SPRSServiceApplicationProxy
```  
  
##  <a name="bkmk_additional_config"></a>Дополнительная настройка  
 В этом разделе описываются дополнительные действия по настройке, которые важны для большинства развертываний SharePoint.  
  
###  <a name="bkmk_configure_ECS"></a>Настройка служб Excel и PowerPivot  
 Чтобы посмотреть отчеты [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Power View в книге Excel 2013 в SharePoint, необходимо настроить приложение служб Excel в ферме для использования сервера служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Кроме того, учетная запись безопасности для пула приложений, используемая приложением службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], должна иметь права администратора на сервере служб Analysis Services. Дополнительные сведения см. в следующих разделах:  
  
-   В разделе "Настройка служб Excel для интеграции Analysis Services" в [PowerPivot для SharePoint установки 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).  
  
-   [Управление параметрами модели данных служб Excel (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx).  
  
###  <a name="bkmk_provision_agent"></a>Подготавливайте подписки и оповещения  
 Для функций подписок и предупреждений об изменении данных в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] может потребоваться настройка разрешений для агента SQL Server. Если отображается сообщение об ошибке, указывающее, что необходим агент SQL Server, хотя агент SQL Server уже запущен, обновите разрешения. Щелкните ссылку **Подготовка подписок и предупреждений** на странице с сообщением об успешном создании приложения службы, чтобы перейти на страницу провизионирования агента SQL Server. Шаг подготовки необходим, если система развернута более чем на одном компьютере, например если экземпляр базы данных SQL Server находится на другом компьютере. Дополнительные сведения см. в статье о [подготовке подписок и предупреждений для приложений служб SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md) .  
  
### <a name="configure-e-mail-for-ssrs-service-applications"></a>Настройка электронной почты для приложений службы SSRS  
 Функция предупреждения об изменении данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] отправляет предупреждения в сообщениях электронной почты. Для отправки электронной почты могут потребоваться настройка приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и изменение модуля доставки электронной почты приложением службы. Параметры электронной почты необходимо настроить и в случае, если планируется использование модуля доставки электронной почты функцией подписки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в статье [Настройка электронной почты для приложения служб Reporting Services (SharePoint 2010 и SharePoint 2013)](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md).  
  
### <a name="add-reporting-services-content-types-to-content-libraries"></a>Добавьте типы содержимого служб Reporting Services в библиотеку документов  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]предоставляет предопределенные типы содержимого, используемые для управления файлами общих источников данных (RSDS), моделей отчетов (SMDL) и построитель отчетов RDL-файлов. После добавления в библиотеку типов содержимого **Отчет построителя отчетов**, **Модель отчета**и **Источник данных отчета** становится доступной команда **Создать** , позволяющая создавать новые документы этих типов. Дополнительные сведения см. в разделе [Добавление типов содержимого сервера отчетов в библиотеку &#40;Reporting Services в режиме интеграции с SharePoint&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).  
  
### <a name="activate-the-report-server-file-sync-feature"></a>Активация функции синхронизации файлов сервера отчетов  
 Если пользователи часто загружают элементы опубликованных отчетов непосредственно в библиотеки документов SharePoint, может оказаться полезной функция **синхронизации файлов сервера отчетов** уровня сайта. Функция синхронизации файлов позволяет синхронизировать каталог сервера отчетов с элементами библиотек документов на более регулярной основе. Дополнительные сведения см. в статье [активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).  
  
##  <a name="bkmk_verify_installation"></a>Проверка установки  
 Далее приведены действия и процедуры, которые предлагается выполнить для проверки развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.  
  
-   См. подраздел, посвященный SharePoint, в разделе [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md).  
  
-   В библиотеке документов SharePoint создайте базовый отчет служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который содержит только одно текстовое поле, например заголовок. Отчет не содержит никаких источников данных и наборов данных. Цель состоит в том, чтобы проверить возможность открытия построителя отчетов, создания простого отчета и просмотра этого отчета.  
  
     Сохраните отчет в библиотеке документов и запустите отчет из библиотеки. Дополнительные сведения о создании отчетов с помощью построителя отчетов см. в разделе [Запуск построителя отчетов (построитель отчетов)](https://technet.microsoft.com/library/ms159221.aspx).  
  
## <a name="see-also"></a>См. также:  
 [Командлеты PowerShell для Reporting Services режиме SharePoint](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)   
 [Обновление и миграция Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
 [Стратегия содержимого: Установка и настройка SharePoint Server и SQL Server BI](https://technet.microsoft.com/library/dn205112.aspx)   
 [Функции, поддерживаемые различными выпусками SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473)   
 [Reporting Services службы SharePoint и приложений служб](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)
