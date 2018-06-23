---
title: Установка PowerPivot для SharePoint 2010 | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eec38696-5e26-46fa-bc83-aa776f470ce8
caps.latest.revision: 52
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: c77fa146f7703fb67cf0d1ad5c9aa0c042737976
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193298"
---
# <a name="install-powerpivot-for-sharepoint-2010"></a>Установка PowerPivot для SharePoint 2010
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] представляет собой набор служб среднего уровня и серверных служб, которые обеспечивают доступ к данным PowerPivot в ферме SharePoint 2010. Если для создания книг с аналитическими данными в компании используется клиентское приложение [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel 2010, то для доступа к этим данным в серверной среде потребуется [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. В этой теме пошагово рассматривается процесс установки и приводятся ссылки на другие темы, которые помогут при настройке PowerPivot.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010|  
  
 
  
 Инструкции по установке [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на том же сервере. в разделе [контрольный список развертывания: службы Reporting Services, Power View и PowerPivot для SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md).  
  
## <a name="prerequisites"></a>предварительные требования  
  
1.  Для запуска программы установки SQL Server необходимо быть локальным администратором.  
  
2.  Для [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] требуется выпуск SharePoint Server 2010 Enterprise. Можно также использовать ознакомительный выпуск Enterprise Edition.  
  
3.  Должен быть установлен SharePoint Server 2010 с пакетом обновления 2 (SP2). Без него не удастся настроить ферму для использования возможностей [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
4.  Компьютер должен быть присоединен к домену.  
  
5.  Для подготовки к работе [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо иметь учетную запись пользователя домена. В установке [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] учетная запись служб Analysis Services должна быть учетной записью пользователя домена, чтобы службами можно было управлять из центра администрирования. Вы введете учетную запись и учетные данные на странице **Конфигурация сервера** во время выполнения шагов в этом документе.  
  
6.  Должно быть доступно имя экземпляра [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Не допускается, чтобы на компьютере, где устанавливается PowerPivot для SharePoint, уже имелся именованный экземпляр [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
7.  Экземпляр [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] не может входить в состав отказоустойчивого кластера SQL Server. Используйте функции высокого уровня доступности продукта SharePoint. Например, службы Excel управляют распределением нагрузки серверов PowerPivot для SharePoint. Дополнительные сведения см. в разделе [управление данных служб Excel параметрами (SharePoint Server 2013) модели](http://technet.microsoft.com/library/jj219780.aspx) (http://technet.microsoft.com/library/jj219780.aspx).  
  
8.  Если [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] устанавливается в существующей ферме, необходимо наличие одного или нескольких веб-приложений SharePoint, в которых настроен классический режим проверки подлинности. Доступ к данным [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] поддерживается только в веб-приложениях, использующих классическую проверку подлинности Windows. Дополнительные сведения о требованиях к классическому режиму см. в разделе [PowerPivot проверки подлинности и авторизации](../../analysis-services/power-pivot-sharepoint/power-pivot-authentication-and-authorization.md).  
  
9. Изучите следующие дополнительные разделы, чтобы ознакомиться с требованиями к системе и версиям:  
  
    -   [Указания по использованию функций бизнес-аналитики SQL Server в ферме SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
##  <a name="InstallSQL"></a> Шаг 1: Установка PowerPivot для SharePoint  
 На этом шаге запускается программа установки SQL Server для установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. На следующем шаге после установки выполняется настройка сервера.  
  
1.  Вставьте установочный носитель в привод или откройте папку, в которой содержатся установочные файлы SQL Server, и дважды щелкните **setup.exe**.  
  
2.  Щелкните **Установка** в левой навигационной панели.  
  
3.  Щелкните **Новая установка изолированного экземпляра SQL Server или добавление компонентов к существующей установке**.  
  
4.  На странице **Ключ продукта** укажите выпуск Evaluation Edition или введите ключ продукта для лицензированной копии выпуска Enterprise Edition.  
  
     Нажмите кнопку **Далее**.  
  
5.  Примите условия лицензионного соглашения на использование программного обеспечения Майкрософт. Мы будем благодарны, если вы также включите функции отправки отзывов и сообщений об ошибках. Нажмите кнопку **Далее**.  
  
6.  Обновите файлы установки, если появится соответствующий запрос.  
  
7.  На странице **Правила установки** программа установки определяет наличие любых проблем, которые могут помешать установке. Просмотрите список, чтобы определить, определила ли программа установки наличие потенциальных проблем в системе.  
  
    > [!NOTE]  
    >  Так как брандмауэр Windows включен, отобразится предупреждение о том, что для включения удаленного доступа необходимо открыть порты. Как правило, к установкам [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] это предупреждение неприменимо. Соединения со службами и файлами данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] выполняются с использованием портов SharePoint, уже открытых для взаимодействия служб SharePoint.  
  
     Нажмите кнопку **Далее**. Дождитесь окончания установки на сервере программных файлов программы установки SQL Server.  
  
8.  На странице **Роль установки** выберите **SQL Server PowerPivot для SharePoint**.  
  
9. В установку при необходимости можно добавить экземпляр компонента Database Engine. Это может потребоваться сделать, если выполняется настройка новой фермы и для работы баз данных конфигурации и контента фермы нужен сервер баз данных. Если добавить компонент Database Engine, он будет установлен как именованный экземпляр PowerPivot. Каждый раз, когда необходимо указать подключение к этому экземпляру (например, в мастере настройки фермы при использовании этого мастера для настройки фермы), введите имя базы данных в следующем формате: <`servername`> \PowerPivot.  
  
     ![GMNI_SetupUI_FeatureRole](../../../2014/sql-server/install/media/gmni-setupui-featurerole.gif "GMNI_SetupUI_FeatureRole")  
  
10. Нажмите кнопку **Далее**.  
  
11. На странице **Выбор компонентов** в ознакомительных целях отображается список компонентов, которые будут установлены (только для чтения). Представленные для этой роли элементы нельзя дополнить или удалить. Нажмите кнопку **Далее**.  
  
12. На странице **правила функций** щелкните **Далее**. Эту страницу можно пропустить.  
  
13. На странице **Конфигурация экземпляра** в ознакомительных целях отображается имя экземпляра «PowerPivot», доступное только для чтения. Имя экземпляра **POWERPIVOT** является **обязательным и не может быть изменено**. Однако можно ввести уникальный идентификатор экземпляра, а также описательное имя каталога и разделы реестра. Нажмите кнопку **Далее**.  
  
14. На странице **Конфигурация сервера** введите требуемые сведения об учетной записи.  
  
     Для служб SQL Server Analysis Services необходимо указать учетную запись пользователя домена. Не указывайте встроенную учетную запись. Учетная запись домена требуется для управления учетной записью службы Analysis Services как *управляемой учетной записью* в центре администрирования SharePoint Central.  
  
     ![Настройка SSAS Server](../../../2014/sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "Настройка SSAS Server")  
  
     Если был добавлен компонент SQL Server Database Engine и агент SQL Server, можно настроить запуск служб под учетной записью пользователя домена или виртуальной учетной записью по умолчанию.  
  
     Никогда не указывайте собственную учетную запись пользователя домена для обеспечения работы служб. Это приведет к тому, что серверу будут предоставлены те же разрешения на сетевые ресурсы, что и вам. В случае получения злоумышленником доступа к серверу он сможет воспользоваться вашими учетными данными домена, что откроет ему доступ к тем же данным и приложениям, которыми можете пользоваться вы сами.  
  
15. Нажмите кнопку **Далее**.  
  
16. При установке компонента Database Engine откроется страница настройки компонента Database Engine. На странице «Настройка ядра СУБД» нажмите **Добавить текущего пользователя** , чтобы предоставить учетной записи пользователя разрешения администратора для экземпляра ядра СУБД. Нажмите кнопку **Добавить** , чтобы добавить дополнительные учетные записи. Нажмите кнопку **Далее**.  
  
17. На странице **Конфигурация служб Analysis Services** нажмите **Добавить текущего пользователя** , чтобы предоставить учетной записи пользователя разрешения администратора. Для настройки сервера по окончании установки потребуются разрешения администратора.  
  
18. На этой же странице добавьте учетную запись пользователя Windows, которому также требуются административные разрешения. Например, административные разрешения на сервере необходимы любому пользователю, который собирается подключаться к экземпляру [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] из среды SQL Server Management Studio для устранения неполадок подключения к базе данных или получения сведений о версии. Добавьте учетную запись пользователя, который сможет производить устранение проблем или администрирование сервера.  
  
19. Нажмите кнопку **Далее**.  
  
20. Нажимайте кнопку **Далее** на всех оставшихся страницах, пока не откроется страница «Все готово для установки».  
  
21. Нажмите кнопку **Установить**.  
  
> [!TIP]  
>  Если необходимо устранение неисправностей установки SQL Server см. в разделе [Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
##  <a name="bkmk_config"></a> Шаг 2: Настройка сервера  
  
> [!IMPORTANT]  
>  Перед настройкой [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] или фермы SharePoint, в которой используется сервер баз данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], необходимо установить пакет обновления SharePoint 2010 SP2. Если пакет обновления еще не установлен, установите его перед тем, как начать настройку сервера.  
  
 Установка не будет завершена до настройки сервера. В этом выпуске Настройка сервера всегда выполняется как задача после установки, используя один из следующих подходов: [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] средства настройки, администрирования или PowerShell. Для продолжения выберите один из следующих вариантов.  
  
-   [Настройка или восстановление PowerPivot для SharePoint 2010 &#40;средство настройки PowerPivot&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md)  
  
-   [Настройка и администрирование сервера PowerPivot в центре администрирования](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
-   [Настройка PowerPivot с помощью Windows PowerShell](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)  
  
 **Соединение с экземпляром компонента Database Engine.** После установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] программа установки SQL Server предлагает возможность добавить к установке экземпляр компонента Database Engine. Возможно, вы добавили установку экземпляра компонента Database Engine, если выполнялась настройка новой фермы, и для выполнения баз данных конфигурации и контента фермы был нужен сервер баз данных. Если вы добавили компонент Database Engine, то он был установлен как именованный экземпляр [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Каждый раз, когда необходимо указать подключение к этому экземпляру (например, в мастере настройки фермы при использовании этого мастера для настройки фермы), не забудьте ввести имя базы данных в следующем формате: <`servername`> \PowerPivot.  
  
##  <a name="bkmk_redist"></a> Шаг 3: Установка OLE DB служб Analysis Services поставщиков на серверах приложений служб Excel  
 Потребуются дополнительные шаги установки, если службы вычислений Excel и [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] запускаются на разных серверах приложений. На серверах приложений, использующих службы вычислений Excel, установите соответствующую версию поставщика OLE DB для служб Analysis Services (MSOLAP).  
  
-   Версия [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] MSOLAP включена в программу установки SQL Server, поэтому установка версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] MSOLAP требуется только в том случае, если сервер приложений не является сервером приложений PowerPivot.  
  
    > [!NOTE]  
    >  Серверу приложений служб вычислений Excel также требуется экземпляр файла **Microsoft.AnalysisServices.Xmla.dll** в глобальной сборке. Чтобы установить библиотеку DLL на сервере приложений, установите [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Выберите вариант «Средства управления — полный набор» на странице **Выбор компонентов** мастера программы установки SQL Server.  
  
-   Если сервер приложений должен поддерживать старые книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], необходимо установить версию MSOLAP для SQL Server 2008 R2.  
  
 Дополнительные сведения об установке поставщика, включая проверку, см. в разделе [Установка Analysis Services поставщика OLE DB на серверах SharePoint](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
##  <a name="bkmk_verify"></a> Шаг 4: Проверка установки  
 На этом последнем шаге убедитесь в полной работоспособности SharePoint 2010 и [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Инструкции см. в разделе [Verify a PowerPivot for SharePoint Installation](../../analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation.md).  
  
## <a name="see-also"></a>См. также  
 [Установка PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [Контрольный список развертывания: Службы Reporting Services, Power View и PowerPivot для SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)   
 [Контрольный список развертывания: Масштабирование путем добавления серверов PowerPivot в ферме SharePoint 2010](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)   
 [Контрольный список развертывания: Установка нескольких серверов PowerPivot для SharePoint 2010](../../../2014/sql-server/install/deployment-checklist-multiserver-installation-powerpivot-sharepoint-2010.md)  
  
  