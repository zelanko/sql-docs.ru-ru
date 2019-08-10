---
title: Установка PowerPivot для SharePoint 2013 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d3310562-82c1-454f-9c48-33a241749238
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0cd41c3a139a2e4be03d0204a16cb698b3d36c89
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68888654"
---
# <a name="powerpivot-for-sharepoint-2013-installation"></a>Установка PowerPivot для SharePoint 2013
  В данном разделе описываются процедуры установки одиночного сервера [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в режиме развертывания SharePoint. Эти шаги охватывают запуск мастера установки SQL Server, а также выполнение дополнительных задач по настройке с использованием центра администрирования SharePoint 2013.  
  
 **[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 201  
  
 **В этом разделе:**  
  
 [Историческая справка](#bkmk_background)  
  
 [Предварительные требования](#bkmk_prereq)  
  
 [Шаг 1. Установка PowerPivot для SharePoint](#InstallSQL)  
  
 [Шаг 2. Настройка базовой Analysis Services интеграции с SharePoint](#bkmk_config)  
  
 [Шаг 3. Проверка интеграции](#bkmk_verify)  
  
 [Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services](#bkmk_firewall)  
  
 [Обновление книг и создание расписания обновления данных](#bkmk_upgrade_workbook)  
  
 [Помимо установки одного сервера — PowerPivot для Microsoft SharePoint](#bkmk_multiple_servers)  
  
##  <a name="bkmk_background"></a> Историческая справка  
 PowerPivot для SharePoint представляет собой набор служб среднего уровня и внутренних служб, обеспечивающих доступ к данным PowerPivot в ферме SharePoint 2013.  
  
-   **Серверные службы:** При использовании PowerPivot для Excel для создания книг, содержащих аналитические данные, необходимо иметь PowerPivot для SharePoint для доступа к этим данным в серверной среде. Вы можете запустить программу установки SQL Server на компьютере, где установлен SharePoint Server 2013 или на другом компьютере, где нет ПО SharePoint. Службы Analysis services нисколько не зависят от SharePoint.  
  
     **Примечание.** В этом разделе описывается установка [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] сервера и серверных служб.  
  
-   **Промежуточный уровень:** Улучшения в работе с PowerPivot в SharePoint, включая галерею PowerPivot, обновление данных по расписанию, панель мониторинга управления и поставщики данных. Дополнительные сведения об установке и настройке среднего уровня см. в следующем документе:  
  
    -   [Установка или удаление надстройки PowerPivot для SharePoint &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)  
  
    -   [Настройка PowerPivot и развертывание решений &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)  
  
##  <a name="bkmk_prereq"></a> Предварительные требования  
  
1.  Для запуска программы установки SQL Server необходимо быть локальным администратором.  
  
2.  Для работы PowerPivot для SharePoint необходим выпуск Enterprise Edition сервера SharePoint Server 2013. Можно также использовать ознакомительный выпуск Enterprise Edition.  
  
3.  Компьютер должен быть присоединен к домену в том же лесе Active Directory, что и службы Excel.  
  
4.  Должно быть доступно имя экземпляра PowerPivot. На компьютере, где устанавливаются службы Analysis Services для SharePoint, не может присутствовать именованный экземпляр PowerPivot.  
  
5.  Ознакомьтесь [с требованиями к оборудованию и программному обеспечению &#40;для Analysis Services&#41;Server в режиме интеграции с SharePoint SQL Server 2014](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).  
  
6.  Заметки о выпуске см. в заметках [о выпуске пакета обновления 1 для SQL Server 2012](https://go.microsoft.com/fwlink/?LinkID=248389) (https://go.microsoft.com/fwlink/?LinkID=248389).  
  
###  <a name="bkmk_sqleditions"></a> Требования к выпуску SQL Server  
 Не все функции бизнес-аналитики доступны во всех выпусках [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Дополнительные сведения см. [в разделе функции, поддерживаемые различными выпусками https://go.microsoft.com/fwlink/?linkid=232473) SQL Server 2012 (](https://go.microsoft.com/fwlink/?linkid=232473) и выпусками [и компонентами SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).  
  
 Текущие заметки о выпуске можно найти в заметках [о Выпуске SQL Server 2012 SP1](ttp://go.microsoft.com/fwlink/?LinkID=248389) (https://go.microsoft.com/fwlink/?LinkID=248389).  
  
 [Заметки о Выпуске https://go.microsoft.com/fwlink/?LinkId=236893) Microsoft SQL Server 2012 (](https://go.microsoft.com/fwlink/?LinkId=236893).  
  
##  <a name="InstallSQL"></a> Шаг 1. Установка PowerPivot для SharePoint  
 На этом шаге запускается программа установки SQL Server Setup, чтобы установить сервер [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. На следующем шаге необходимо настроить службы Excel на использование данного сервера для моделей данных книги.  
  
1.  Запустите мастер установки SQL Server (Setup.exe).  
  
2.  Нажмите кнопку **Установка** на левой навигационной панели.  
  
3.  Щелкните **Новая установка изолированного экземпляра SQL Server или добавление компонентов к существующей установке**.  
  
4.  Если откроется страница **Ключ продукта** , выберите выпуск Evaluation Edition или введите ключ продукта для лицензированной копии выпуска Enterprise Edition. Нажмите кнопку **Далее**. Дополнительные сведения о выпусках см. в разделе [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).  
  
5.  Изучите и примите условия лицензионного соглашения на использование программного обеспечения корпорации Майкрософт и нажмите кнопку **Далее**.  
  
6.  Если появится страница **Глобальные правила** , просмотрите все сведения о правилах, показанных в мастере установки.  
  
7.  На странице **Центр обновления Майкрософт** рекомендуется использовать центр обновления Майкрософт для проверки наличия обновлений, затем нажать кнопку **Далее**.  
  
8.  Выполнение страницы **Установка файлов установки** занимает несколько минут. Просмотрите все предупреждения или ошибки правил, затем нажмите кнопку **Далее**.  
  
9. Если выводятся другие **Правила поддержки установки**, просмотрите все предупреждения и нажмите **Далее**.  
  
     **Примечание.** Так как брандмауэр Windows включен, появится предупреждение о том, что необходимо открыть порты, чтобы включить удаленный доступ.  
  
10. На странице **Роль установки** выберите **SQL Server PowerPivot для SharePoint**. В таком случае устанавливаются службы Analysis Services в режиме интеграции с SharePoint.  
  
     В установку при необходимости можно добавить экземпляр компонента Database Engine. Вы можете добавить ядро СУБД при настройке новой фермы и потребовать сервер базы данных для запуска конфигурации и баз данных содержимого фермы. В таком случае также устанавливается компонент [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
     Если добавлен компонент ядра СУБД, то он устанавливается как именованный экземпляр **PowerPivot** . Указывая подключение к этому экземпляру, каждый раз вводите имя базы данных в следующем формате: [`servername`]\PowerPivot.  
  
     Нажмите кнопку **Далее**.  
  
     ![Роль установки](../../../sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "Роль установки")  
  
11. На странице «Выбор компонентов» в ознакомительных целях отображается список компонентов (только для чтения). Заранее выбранные для этой роли элементы нельзя дополнять или удалять. Нажмите кнопку **Далее**.  
  
12. На странице **Конфигурация экземпляра** в ознакомительных целях отображается имя экземпляра «PowerPivot», доступное только для чтения. Имя этого экземпляра является обязательным и не может быть изменено. Однако можно ввести уникальный идентификатор экземпляра, а также описательное имя каталога и разделы реестра. Нажмите кнопку **Далее**.  
  
13. На странице **Конфигурация сервера** настройте все службы для автоматического **типа запуска**. При желании укажите учетную запись домена и пароль для **Служб SQL Server Analysis Services** **(1)** на следующей схеме.  
  
    -   Для [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]вы можете использовать учетную запись **пользователя домена** или учетную запись **Сетевая служба** . Запрещается использовать учетные записи LocalService или LocalSystem.  
  
    -   Если был добавлен компонент SQL Server Database Engine и агент SQL Server, можно настроить запуск служб под учетной записью пользователя домена или виртуальной учетной записью по умолчанию.  
  
    -   Никогда не предоставляйте собственную учетную запись пользователя домена для работы служб. Это приведет к тому, что серверу будут предоставлены те же разрешения на сетевые ресурсы, что и вам. Если злоумышленник взломает сервер, он выполнит вход с помощью ваших учетных данных домена. Пользователь получил такие же разрешения для загрузки или использования данных и приложений, как и вы.  
  
     Нажмите кнопку **Далее**.  
  
     ![Конфигурация сервера SSAS](../../../sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "Конфигурация сервера SSAS")  
  
14. При установке компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)]откроется страница **Настройки ядра СУБД** . На странице настройки компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)] нажмите **Добавить текущего пользователя** , чтобы предоставить учетной записи пользователя разрешения администратора для экземпляра ядра СУБД.  
  
     Нажмите кнопку **Далее**.  
  
15. На странице **Конфигурация служб Analysis Services** нажмите **Добавить текущего пользователя** , чтобы предоставить учетной записи пользователя разрешения администратора. Для настройки сервера по окончании установки потребуются разрешения администратора.  
  
    -   На этой же странице добавьте учетную запись пользователя Windows, которому также требуются административные разрешения. Например, любой пользователь, который собирается подключиться к экземпляру [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] в [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] для поиска и устранения проблем с подключением к базе данных, должен обладать разрешениями администратора. Добавьте учетную запись пользователя, который сможет производить устранение проблем или администрирование сервера.  
  
    -   > [!NOTE]  
        >  Все приложения служб, которым необходим доступ к экземпляру служб Analysis Services, должны иметь административные разрешения для служб Analysis Services. Например, можно добавить учетную запись служб Excel, Power View и Performance Point. Кроме того, добавьте учетную запись фермы SharePoint, которая используется в качестве идентификатора этого веб-приложения, размещающего центр администрирования.  
  
     Нажмите кнопку **Далее**.  
  
16. На странице **Отчет об ошибках** нажмите кнопку **Далее**.  
  
17. На странице **Все готово для установки** нажмите кнопку **Установить**.  
  
18. Если отображается диалоговое окно **Необходима перезагрузка компьютера**, нажмите кнопку **ОК**.  
  
19. После завершения установки нажмите кнопку **Закрыть**.  
  
20. Перезагрузите компьютер.  
  
21. Если в среде используется брандмауэр, см. раздел электронной документации по SQL Server [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
### <a name="verify-the-sql-server-installation"></a>Проверка установки SQL Server  
 Убедитесь, что службы Analysis Services запущены.  
  
1.  В Microsoft Windows нажмите **Пуск**, выберите **Все программы**и щелкните группу **Microsoft SQL Server 2012** .  
  
2.  Выберите **SQL Server Management Studio**.  
  
3.  Подключитесь к экземпляру служб Analysis Services, например к **[имя сервера]\POWERPIVOT**. Если вы можете подключиться к экземпляру, то служба запущена.  
  
##  <a name="bkmk_config"></a> Шаг 2. Настройка базовой Analysis Services интеграции с SharePoint  
 Следующие шаги описывают изменения в конфигурации, необходимые для взаимодействия с расширенными моделями данных Excel в библиотеке документов SharePoint. Выполните эти шаги после того, как установите SharePoint Server 2013 и службы SQL Server Analysis Services.  
  
### <a name="grant-excel-services-server-administration-rights-on-analysis-services"></a>Предоставление прав администрирования сервером служб Excel в службах Analysis Services  
 Не нужно выполнять этот процедуру, описанную в этом разделе, если в процессе установки служб Analysis Services была добавлена учетная запись приложения служб Excel в качестве администратора служб Analysis Services.  
  
1.  На сервере служб Analysis Services запустите среду SQL Server Management Studio и подключитесь к экземпляру служб Analysis Services, например `[MyServer]\POWERPIVOT`.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши название экземпляра и выберите пункт **Свойства**.  
  
     ![Просмотр свойств сервера SSAS](../../../sql-server/install/media/as-ssms-proeprties.gif "Просмотр свойств сервера SSAS")  
  
3.  На панели слева выберите **Безопасность**. Добавьте имя входа домена, настроенного для приложения служб Excel в шаге 1.  
  
     ![Параметры безопасности сервера SSAS](../../../sql-server/install/media/as-ssms-security.gif "Параметры безопасности сервера SSAS")  
  
### <a name="configure-excel-services-for-analysis-services-integration"></a>Настройка служб Excel для интеграции со службами Analysis Services  
  
1.  В центре администрирования SharePoint в группе «Управление приложениями» выберите **Управление приложениями служб**.  
  
2.  Щелкните имя приложения службы, по умолчанию это **Приложение служб Excel**.  
  
3.  Нажмите кнопку **Параметры модели данных**на странице **Управление приложением служб Excel**.  
  
4.  Щелкните **Добавить сервер**.  
  
5.  В поле **Имя сервера**введите имя сервера служб Analysis Services и имя экземпляра PowerPivot. Например, `MyServer\POWERPIVOT`. Указание имени экземпляра PowerPivot является обязательным.  
  
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
  
##  <a name="bkmk_verify"></a> Шаг 3. Проверка интеграции  
 Следующие шаги содержат пошаговые инструкции для создания и передачи новой книги как способа проверки интеграции служб Analysis Services. Для выполнения этих шагов потребуется база данных SQL Server.  
  
1.  **Примечание.** Если у вас уже есть Расширенная книга с срезами или фильтрами, можно передать ее в библиотеку документов SharePoint и убедиться, что вы можете взаимодействовать с срезами и фильтрами из представления библиотеки документов.  
  
2.  Создайте новую книгу в Excel.  
  
3.  На вкладке «Данные» щелкните ленту **Из других источников** в разделе **Получение внешних данных**.  
  
4.  Выберите **Из SQL Server**.  
  
5.  В **мастере подключения к данным**введите имя экземпляра SQL Server, содержащего базу данных, которую необходимо использовать.  
  
6.  Или в разделе «Учетные данные для входа в систему» убедитесь, что установлен флажок **Использовать проверку подлинности Windows** и нажмите кнопку **Далее**.  
  
7.  Выберите необходимую базу данных.  
  
8.  Проверьте, установлен ли флажок **Подключение к заданной таблице** .  
  
9. Установите флажок **Включение возможности выбора нескольких таблиц и добавления таблицы в модель данных Excel** .  
  
10. Выберите таблицы для импортирования.  
  
11. Установите флажок **Импортировать связи между выбранными таблицами**и нажмите кнопку **Далее**. Импортирование нескольких таблиц из реляционной базы данных позволяет работать с таблицами, которые уже связаны между собой. Такой подход экономит время, поскольку не нужно создавать связи вручную.  
  
12. На странице **Сохранение файла подключения к данным и завершение работы** мастера введите имя соединения и нажмите **Готово**.  
  
13. Появится диалоговое окно **Импорт данных** . Выберите **Отчет сводной таблицы**и нажмите кнопку **ОК**.  
  
14. Список полей сводной таблицы появится в книге.   
    В списке полей перейдите на вкладку **Все**  
  
15. Добавьте поля в области строк, столбцов и значений в списке полей.  
  
16. Добавьте срез или фильтр в сводную таблицу. **Не пропускайте этот шаг**. Срез или фильтр позволяет проверить правильность установки служб Analysis Services.  
  
17. Сохраните книгу в библиотеке документов в SharePoint Server 2013 с настроенными службами Excel. Вы можете также сохранить книгу в общую папку, а затем передать ее в библиотеку документов SharePoint Server 2013.  
  
18. Щелкните название книги для ее просмотра в SharePoint и выберите срез или измените ранее добавленный фильтр. Если произойдет обновление данных, то это означает, что службы Analysis Services установлены и доступны для служб Excel. При открытии книги в Excel будет использоваться кэшированная копия, а не версия с сервера служб Analysis Services.  
  
##  <a name="bkmk_firewall"></a> Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services  
 Сведения в разделе [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md) помогут определить, требуется ли разблокировать порты брандмауэра для доступа к службам Analysis Services или PowerPivot для SharePoint. Выполнив шаги, приведенные в этом разделе, можно настроить параметры порта и брандмауэра. На практике, чтобы разрешить доступ к серверу служб Analysis Services, необходимо выполнять эти шаги вместе.  
  
##  <a name="bkmk_upgrade_workbook"></a> Обновление книг и создание расписания обновления данных  
 Шаги, необходимые для обновления книг, созданных в предыдущих версиях PowerPivot, зависят от того, в какой версии PowerPivot создана книга. Дополнительные сведения см. в статье [Обновление книг и запланированное обновление данных (SharePoint 2013 )](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).  
  
##  <a name="bkmk_multiple_servers"></a>Помимо установки одного сервера — PowerPivot для Microsoft SharePoint  
 **Веб-интерфейс (WFE)** или **средний уровень:** : Чтобы использовать [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] сервер в режиме интеграции с SharePoint в более крупной ферме SharePoint и установить дополнительные компоненты PowerPivot в ферме, запустите пакет установщика SPFarm **. msi** на каждом сервере SharePoint. Пакет spPowerPivot.msi устанавливает необходимые поставщики данных и средство настройки служб PowerPivot для SharePoint 2013.  
  
 Дополнительные сведения об установке и настройке среднего уровня см. в следующем документе:  
  
-   [Установка или удаление надстройки PowerPivot для SharePoint &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)  
  
-   Чтобы загрузить файл MSI, обратитесь в раздел [Microsoft SQL Server 2014 PowerPivot для Microsoft SharePoint 2013](https://go.microsoft.com/fwlink/?LinkID=324854)  
  
-   [Настройка PowerPivot и развертывание решений &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)  
  
 **Избыточность и загрузка сервера:** Установка второго или более [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] серверов в режиме интеграции с SharePoint обеспечит избыточность [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] функциональности сервера. Ввод в действие дополнительных серверов приводит к дальнейшему распределению нагрузки между серверами. Дополнительные сведения см. в следующих разделах:  
  
-   [Настройка Analysis Services для обработки моделей данных в службах Excel](https://technet.microsoft.com/library/jj614437\(v=office.15\)) (https://technet.microsoft.com/library/jj614437(v=office.15)).  
  
-   [Управление параметрами модели данных служб Excel (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780\(v=office.15\)) (https://technet.microsoft.com/library/jj219780(v=office.15)).  
  
 ![Параметры SharePoint](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "Параметры SharePoint") [Отправка отзыва и контактной информации через Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>См. также  
 [Перенос PowerPivot в SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013)   
 [Установка или удаление надстройки PowerPivot для SharePoint &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)   
 [Обновление книг и запланированное обновление данных (SharePoint 2013 )](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)  
  
  
