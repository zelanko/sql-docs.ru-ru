---
title: Установка служб Analysis Services в режиме Power Pivot | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 59d3f4dadc2de71f8fa4438ec48a2783164a485a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="install-analysis-services-in-power-pivot-mode"></a>Установка служб Analysis Services в режиме Power Pivot
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  В данном разделе описываются процедуры установки одного сервера служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в режиме [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для развертывания SharePoint. Эти шаги охватывают запуск мастера установки SQL Server, а также выполнение дополнительных задач по настройке с использованием центра администрирования SharePoint.  
  
##  <a name="bkmk_background"></a> Историческая справка  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint представляет собой набор служб среднего уровня и серверных служб, обеспечивающих доступ к данным [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в ферме SharePoint 2016 или SharePoint 2013.  
  
-   **Серверные службы** . Если для создания книг с аналитическими данными используется [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для Excel, то для доступа к этим данным в серверной среде потребуется [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint. Вы можете запустить программу установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на компьютере, где установлен SharePoint Server или на другом компьютере, где нет ПО SharePoint. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] нисколько не зависят от SharePoint.  
  
     **Примечание:** в этом разделе описывается установка сервера [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и серверных служб.  
  
-   **Службы среднего уровня** . Предоставляют дополнительные возможности работы с [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в SharePoint, включая коллекцию [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , обновление данных расписания, панель мониторинга управления и поставщики данных. Дополнительные сведения об установке и настройке среднего уровня см. в следующем документе:  
  
    -   [Установка или удаление надстройки Power Pivot для SharePoint (SharePoint 2016)](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2016.md)  
  
    -   [Установка или удаление надстройки Power Pivot для SharePoint (SharePoint 2013)](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)  
  
    -   [Настройка Power Pivot и развертывание решений (SharePoint 2016)](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2016.md)  
  
    -   [Настройка Power Pivot и развертывание решений (SharePoint 2013)](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)  
  
##  <a name="bkmk_prereq"></a> Предварительные требования  
  
1.  Чтобы запустить программу установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , требуются права локального администратора.  
  
2.  Чтобы работать с [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint, необходим выпуск Enterprise Edition сервера SharePoint Server. Можно также использовать ознакомительный выпуск Enterprise Edition.  
  
3.  Компьютер должен быть присоединен к домену в том же лесу Active Directory, что и сервер Office Online Server (SharePoint 2016) или службы Excel (SharePoint 2013).  
  
4.  Должно быть доступно имя экземпляра [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] . На компьютере, где устанавливаются службы Analysis Services в режиме [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)], не может присутствовать именованный экземпляр [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] .  
  
     **Примечание** . Имя экземпляра должно быть POWERPIVOT.  
  
5.  См. раздел [Требования к оборудованию и программному обеспечению для сервера служб Analysis Services в режиме интеграции с SharePoint](http://msdn.microsoft.com/library/fb86ca0a-518c-4c61-ae78-7680c57fae1f).  
  
6.  Ознакомьтесь с заметками о выпуске в статье [SQL Server 2016 Release Notes](../../../sql-server/sql-server-2016-release-notes.md).  
  
###  <a name="bkmk_sqleditions"></a> Требования к выпуску SQL Server  
 Не все функции бизнес-аналитики доступны во всех выпусках [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [Analysis Services функции, поддерживаемые различными выпусками SQL Server 2016](../../../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md) и [выпуски и компоненты SQL Server 2016](../../../sql-server/editions-and-components-of-sql-server-2016.md).  
  
##  <a name="InstallSQL"></a> Шаг 1. Установка Power Pivot для SharePoint  
 На этом шаге запускается программа установки SQL Server Setup, чтобы установить сервер [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в режиме [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] . На следующем шаге необходимо настроить службы Excel на использование данного сервера для моделей данных книги.  
  
1.  Запустите мастер установки SQL Server (Setup.exe).  
  
2.  Щелкните **Установка** на панели навигации слева.  
  
3.  Выберите **Новая установка изолированного экземпляра SQL Server или добавление компонентов к существующей установке**.  
  
4.  Если откроется страница **Ключ продукта** , выберите выпуск Evaluation Edition или введите ключ продукта для лицензированной копии выпуска Enterprise Edition. Нажмите кнопку **Далее**. Дополнительные сведения о выпусках см. в разделе [Editions and Components of SQL Server 2016](../../../sql-server/editions-and-components-of-sql-server-2016.md).  
  
5.  Прочтите и примите условия лицензионного соглашения на использование программного обеспечения корпорации Майкрософт и нажмите кнопку **Далее**.  
  
6.  Если появится страница **Глобальные правила** , просмотрите все сведения о правилах, показанных в мастере установки.  
  
7.  На странице **Центр обновления Майкрософт** рекомендуется использовать центр обновления Майкрософт, чтобы проверять наличие обновлений, а затем нажмите кнопку **Далее**.  
  
8.  Выполнение страницы **Установка файлов установки** занимает несколько минут. Просмотрите все предупреждения или ошибки правил, а затем нажмите кнопку **Далее**.  
  
9. Если отображаются другие **правила поддержки установки**, просмотрите все предупреждения и нажмите кнопку **Далее**.  
  
     **Примечание:** так как брандмауэр Windows включен, появится предупреждение о том, что для включения удаленного доступа необходимо открыть порты.  
  
10. На странице **Роль установки** выберите пункт **Установка компонентов SQL Server**.  
  
     Выберите **Далее**.  
  
11. На странице "Выбор компонентов" выберите **Службы Analysis Services**. Этот параметр позволяет установить один из трех режимов служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Вы сможете выбрать необходимый режим на более позднем этапе. Выберите **Далее**.  
  
12. На странице **Конфигурация экземпляра** установите переключатель **Именованный экземпляр** , введите в поле имени **POWERPIVOT** и нажмите кнопку **Далее**.  
  
     ![Программа установки SQL — начальная страница конфигурации экземпляра](../../../analysis-services/instances/install-windows/media/sql2016-pp-instance-config-landing-page.png "программа установки SQL — начальная страница конфигурации экземпляра")  
  
13. На странице **Конфигурация сервера** настройте все службы для автоматического **типа запуска**. При желании укажите учетную запись домена и пароль для **Служб SQL Server Analysis Services** **(1)** на следующей схеме.  
  
    -   Для [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]вы можете использовать учетную запись **пользователя домена** или учетную запись **Сетевая служба** . Запрещается использовать учетные записи LocalService или LocalSystem.  
  
    -   Если был добавлен компонент SQL Server Database Engine и агент SQL Server, можно настроить запуск служб под учетной записью пользователя домена или виртуальной учетной записью по умолчанию.  
  
    -   Никогда не предоставляйте собственную учетную запись пользователя домена для работы служб. Это приведет к тому, что серверу будут предоставлены те же разрешения на сетевые ресурсы, что и вам. Если злоумышленник взломает сервер, он выполнит вход с помощью ваших учетных данных домена. Пользователь получил такие же разрешения для загрузки или использования данных и приложений, как и вы.  
  
     Выберите **Далее**.  
  
     ![Программа установки SQL — конфигурация сервера целевая страница](../../../analysis-services/instances/install-windows/media/sql2016-pp-server-config-landing-page.png "программа установки SQL — исходная страница конфигурации сервера")  
  
14. При установке компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)]откроется страница **Настройки ядра СУБД** . На странице настройки компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)] нажмите кнопку **Добавить текущего пользователя** , чтобы предоставить учетной записи пользователя разрешения администратора для экземпляра ядра СУБД.  
  
     Выберите **Далее**.  
  
15. На странице **Настройка служб Analysis Services** в разделе **Режим сервера** установите переключатель **Режим PowerPivot**.  
  
     ![Программа установки SQL — Настройка служб Analysis Services целевая страница](../../../analysis-services/instances/install-windows/media/sql2016-pp-as-config-landing-page.png "программа установки SQL — Настройка служб Analysis Services целевая страница")  
  
16. На странице **Настройка служб Analysis Services** нажмите кнопку **Добавить текущего пользователя** , чтобы предоставить учетной записи пользователя разрешения администратора. Для настройки сервера по окончании установки потребуются разрешения администратора.  
  
    -   На этой же странице добавьте учетную запись пользователя Windows, которому также требуются административные разрешения. Например, любой пользователь, который собирается подключиться к экземпляру [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] в [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] для поиска и устранения проблем с подключением к базе данных, должен обладать разрешениями администратора. Добавьте учетную запись пользователя, который сможет производить устранение проблем или администрирование сервера.  
  
    -   > [!NOTE]  
        >  Все приложения служб, которым необходим доступ к экземпляру служб Analysis Services, должны иметь административные разрешения для служб Analysis Services. Например, можно добавить учетную запись служб Excel, Power View и Performance Point. Кроме того, добавьте учетную запись фермы SharePoint, которая используется в качестве идентификатора этого веб-приложения, размещающего центр администрирования.  
  
     Выберите **Далее**.  
  
17. На странице **Отчет об ошибках** нажмите кнопку **Далее**.  
  
18. На странице **Все готово для установки** нажмите кнопку **Установить**.  
  
19. Если отображается диалоговое окно **Необходима перезагрузка компьютера**, нажмите кнопку **ОК**.  
  
20. После завершения установки нажмите кнопку **Закрыть**.  
  
21. Перезагрузите компьютер.  
  
22. Если в среде используется брандмауэр, см. раздел электронной документации по SQL Server [Configure the Windows Firewall to Allow Analysis Services Access](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
### <a name="verify-the-sql-server-installation"></a>Проверка установки SQL Server  
 Убедитесь, что службы Analysis Services запущены.  
  
1.  В Microsoft Windows нажмите кнопку **Пуск**, выберите **Все программы**и щелкните группу **Microsoft SQL Server 2016** .  
  
2.  Запустите среду **SQL Server Management Studio**.  
  
3.  Подключитесь к экземпляру служб Analysis Services, например к **[имя сервера]\POWERPIVOT**. Если вы можете подключиться к экземпляру, то служба запущена.  
  
##  <a name="bkmk_config"></a> Этап 2. Настройка базовой интеграции служб Analysis Services с SharePoint  
 Следующие шаги описывают изменения в конфигурации, необходимые для взаимодействия с расширенными моделями данных Excel в библиотеке документов SharePoint. Выполните эти шаги после того, как установите SharePoint и службы SQL Server Analysis Services.  
  
### <a name="sharepoint-2016"></a>SharePoint 2016  
 Из SharePoint 2016 удалены службы Excel, а вместо них для размещения Excel используется сервер Office Online Server.  
  
#### <a name="grant-office-online-server-machine-account-administration-rights-on-analysis-services"></a>Предоставление учетной записи компьютера Office Online Server права администратора служб Analysis Services  
 Не нужно выполнять процедуру, описанную в этом разделе, если в процессе установки служб Analysis Services в качестве администратора служб Analysis Services была добавлена учетная запись компьютера Office Online Server.  
  
1.  На сервере служб Analysis Services запустите среду SQL Server Management Studio и подключитесь к экземпляру служб Analysis Services, например `[MyServer]\POWERPIVOT`.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши имя экземпляра и выберите пункт **Свойства**.  
  
     ![Просмотр свойств сервера служб SSAS](../../../analysis-services/instances/install-windows/media/as-ssms-proeprties.gif "Просмотр свойств сервера служб SSAS")  
  
3.  На панели слева выберите **Безопасность**. Добавьте учетную запись компьютера, на котором установлен сервер Office Online Server.  
  
     ![Параметры безопасности сервера служб SSAS](../../../analysis-services/instances/install-windows/media/as-ssms-security.gif "параметры безопасности сервера служб SSAS")  
  
#### <a name="register-analysis-services-server-with-office-online-server"></a>Зарегистрируйте сервер служб Analysis Services на сервере Office Online Server.  
 На сервере Office Online Server необходимо сделать следующее:  
  
-   Откройте командное окно PowerShell от имени администратора.  
  
-   Загрузите модуль `OfficeWebApps` PowerShell.  
  
     `Import-Module OfficeWebApps`  
  
-   Добавьте сервер служб Analysis Services, например `[MyServer]\POWERPIVOT`.  
  
     `New-OfficeWebAppsExcelBIServer -ServerId [MyServer]\POWERPIVOT]`  
  
### <a name="sharepoint-2013"></a>SharePoint 2013  
  
#### <a name="grant-excel-services-server-administration-rights-on-analysis-services"></a>Предоставление прав администрирования сервером служб Excel в службах Analysis Services  
 Не нужно выполнять этот процедуру, описанную в этом разделе, если в процессе установки служб Analysis Services была добавлена учетная запись приложения служб Excel в качестве администратора служб Analysis Services.  
  
1.  На сервере служб Analysis Services запустите среду SQL Server Management Studio и подключитесь к экземпляру служб Analysis Services, например `[MyServer]\POWERPIVOT`.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши имя экземпляра и выберите пункт **Свойства**.  
  
     ![Просмотр свойств сервера служб SSAS](../../../analysis-services/instances/install-windows/media/as-ssms-proeprties.gif "Просмотр свойств сервера служб SSAS")  
  
3.  На панели слева выберите **Безопасность**. Добавьте имя входа домена, настроенного для приложения служб Excel в шаге 1.  
  
     ![Параметры безопасности сервера служб SSAS](../../../analysis-services/instances/install-windows/media/as-ssms-security.gif "параметры безопасности сервера служб SSAS")  
  
#### <a name="configure-excel-services-for-analysis-services-integration"></a>Настройка служб Excel для интеграции со службами Analysis Services  
  
1.  В центре администрирования SharePoint в группе «Управление приложениями» выберите **Управление приложениями служб**.  
  
2.  Щелкните имя приложения службы, по умолчанию это **Приложение служб Excel**.  
  
3.  Нажмите кнопку **Параметры модели данных**на странице **Управление приложением служб Excel**.  
  
4.  Щелкните **Добавить сервер**.  
  
5.  В поле **Имя сервера**введите имя сервера служб Analysis Services и имя экземпляра [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] . Например, `MyServer\POWERPIVOT`. В качестве имени экземпляра необходимо указать [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] .  
  
     Введите описание.  
  
6.  Нажмите кнопку **ОК**.  
  
7.  Изменения вступят в силу через несколько минут, также вы можете **Остановить** и **Запустить** **Службы вычислений Excel**. Чтобы  
  
     Также можно открыть командную строку с правами администратора и ввести `iisreset /noforce`.  
  
     Вы можете проверить факт распознавания сервера службами Excel, просмотрев записи в журнале ULS. Будут отображены записи следующего вида:  
  
    ```  
    Excel Services Application            Data Model        27           Medium                Check Administrator Access ([ServerName]\POWERPIVOT): Pass.        f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Server Version ([ServerName]\POWERPIVOT): Pass (11.0.2809.24 >= 11.0.2800.0).         f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Deployment Mode ([ServerName]\POWERPIVOT): Pass.            f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
  
    ```  
  
##  <a name="bkmk_verify"></a> Этап 3. Проверка интеграции  
 Следующие шаги содержат пошаговые инструкции для создания и передачи новой книги как способа проверки интеграции служб Analysis Services. Для выполнения этих шагов потребуется база данных SQL Server.  
  
1.  **Примечание:** если уже имеется книга с такими дополнительными функциями, как срезы и фильтры, то вы можете передать ее в библиотеку документов SharePoint и проверить, есть ли возможность взаимодействия со срезами и фильтрами из представления библиотеки документов.  
  
2.  Создайте новую книгу в Excel.  
  
3.  На ленте вкладки "Данные" в группе **Получение внешних данных** выберите **Из других источников**.  
  
4.  Выберите **Из SQL Server**.  
  
5.  В **мастере подключения к данным**введите имя экземпляра SQL Server, содержащего базу данных, которую необходимо использовать.  
  
6.  В разделе "Учетные данные входа в систему" установите флажок **Использовать проверку подлинности Windows** и нажмите кнопку **Далее**.  
  
7.  Выберите необходимую базу данных.  
  
8.  Проверьте, установлен ли флажок **Подключение к заданной таблице** .  
  
9. Установите флажок **Включение возможности выбора нескольких таблиц и добавления таблицы в модель данных Excel** .  
  
10. Выберите таблицы для импортирования.  
  
11. Установите флажок **Импортировать связи между выбранными таблицами**и нажмите кнопку **Далее**. Импортирование нескольких таблиц из реляционной базы данных позволяет работать с таблицами, которые уже связаны между собой. Такой подход экономит время, поскольку не нужно создавать связи вручную.  
  
12. На странице **Сохранение файла подключения данных и завершение работы** мастера введите имя подключения и нажмите кнопку **Готово**.  
  
13. Появится диалоговое окно **Импорт данных** . Выберите **Отчет сводной таблицы**и нажмите кнопку **ОК**.  
  
14. Список полей сводной таблицы появится в книге.   
    В списке полей перейдите на вкладку **Все** .  
  
15. Добавьте поля в области строк, столбцов и значений в списке полей.  
  
16. Добавьте срез или фильтр в сводную таблицу. **Не пропускайте этот шаг**. Срез или фильтр позволяет проверить правильность установки служб Analysis Services.  
  
17. Сохраните книгу в библиотеке документов в ферме SharePoint. Вы можете также сохранить книгу в общую папку, а затем передать ее в библиотеку документов SharePoint.  
  
18. Щелкните название книги для ее просмотра в Excel Online и выберите срез или измените ранее добавленный фильтр. Если произойдет обновление данных, то это означает, что службы Analysis Services установлены и доступны для Excel. При открытии книги в Excel будет использоваться кэшированная копия, а не версия с сервера служб Analysis Services.  
  
##  <a name="bkmk_firewall"></a> Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services  
 Сведения в разделе [Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) помогут определить, требуется ли разблокировать порты брандмауэра для доступа к службам Analysis Services или [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint, необходим выпуск Enterprise Edition сервера SharePoint Server. Выполнив шаги, приведенные в этом разделе, можно настроить параметры порта и брандмауэра. На практике, чтобы разрешить доступ к серверу служб Analysis Services, необходимо выполнять эти шаги вместе.  
  
##  <a name="bkmk_upgrade_workbook"></a> Обновление книг и создание расписания обновления данных  
 Шаги, необходимые для обновления книг, созданных в предыдущих версиях [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , зависят от того, в какой версии [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] создана книга. Дополнительные сведения см. в статье [Обновление книг и запланированное обновление данных (SharePoint 2013 )](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
##  <a name="bkmk_multiple_servers"></a> После установки одного сервера — Power Pivot для Microsoft SharePoint  
 **Интерфейсный веб-компонент** или **сервер среднего уровня**. Чтобы использовать сервер [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint в более крупной ферме SharePoint и установить дополнительные компоненты [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в ферме, запустите пакет установщика **spPowerPivot16.msi (SharePoint 2016) или spPowerPivot.msi (SharePoint 2013)** на каждом из серверов SharePoint. Пакет spPowerPivot16.msi или spPowerPivot.msi устанавливает необходимые поставщики данных и средство настройки служб [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint 2016 или 2013.  
  
 Дополнительные сведения об установке и настройке среднего уровня см. в следующем документе:  
  
-   [Установка или удаление надстройки Power Pivot для SharePoint (SharePoint 2013)](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)  
  
-   [Установка или удаление надстройки Power Pivot для SharePoint (SharePoint 2013)](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)  
  
-   Сведения о загрузке MSI-файла см. в разделе [Microsoft SQL Server 2016 Power Pivot для Microsoft SharePoint 2016](http://go.microsoft.com/fwlink/?LinkID=324854).  
  
-   [Настройка Power Pivot и развертывание решений (SharePoint 2013)](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)  
  
 **Избыточность и загрузка сервера** . Установка двух или более серверов [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в режиме [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] обеспечивает избыточность функциональности сервера [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Ввод в действие дополнительных серверов приводит к дальнейшему распределению нагрузки между серверами. Дополнительные сведения см. в следующих разделах:  
  
-   [Настройка служб Analysis Services для обработки моделей данных в службах Excel (SharePoint 2013)](http://technet.microsoft.com/library/jj614437(v=office.15)).  
  
-   [Управление параметрами модели данных служб Excel (SharePoint 2013)](http://technet.microsoft.com/library/jj219780(v=office.15)).  
  
 ![Параметры SharePoint](../../../analysis-services/media/as-sharepoint2013-settings-gear.gif "параметры SharePoint") [отправки отзывов и контактных данных через отзывов о SQL Server](https://feedback.azure.com/forums/908035-sql-server).  
  
## <a name="see-also"></a>См. также  
 [Перенос Power Pivot в SharePoint 2013](../../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)   
 [Установка или удаление надстройки Power Pivot для SharePoint (SharePoint 2013)](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)   
 [Обновление книг и запланированное обновление данных & #40; SharePoint 2013 & #41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
