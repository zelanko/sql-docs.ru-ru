---
title: Установка PowerPivot для SharePoint 2010 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: eec38696-5e26-46fa-bc83-aa776f470ce8
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: b7d478761a1051114e0189c7fd11eddafcef086b
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78172346"
---
# <a name="install-powerpivot-for-sharepoint-2010"></a>Установка PowerPivot для SharePoint 2010
  
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] представляет собой набор служб среднего уровня и серверных служб, которые обеспечивают доступ к данным PowerPivot в ферме SharePoint 2010. Если для создания книг с аналитическими данными в компании используется клиентское приложение [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel 2010, то для доступа к этим данным в серверной среде потребуется [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . В этой теме пошагово рассматривается процесс установки и приводятся ссылки на другие темы, которые помогут при настройке PowerPivot.

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010|

 

 Инструкции по установке [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] размещению на том же сервере см. в разделе [контрольный список развертывания: Reporting Services, Power View и PowerPivot для SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md).

## <a name="prerequisites"></a>Предварительные требования

1.  Для запуска программы установки SQL Server необходимо быть локальным администратором.

2.  Для [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]требуется выпуск SharePoint Server 2010 Enterprise. Можно также использовать ознакомительный выпуск Enterprise Edition.

3.  Должен быть установлен SharePoint Server 2010 с пакетом обновления 2 (SP2). Без него не удастся настроить ферму для использования возможностей [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .

4.  Компьютер должен быть присоединен к домену.

5.  Для подготовки к работе [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]необходимо иметь учетную запись пользователя домена. В установке [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] учетная запись служб Analysis Services должна быть учетной записью пользователя домена, чтобы службами можно было управлять из центра администрирования. Вы введете учетную запись и учетные данные на странице **Конфигурация сервера** во время выполнения шагов в этом документе.

6.  Должно быть доступно имя экземпляра [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Не допускается, чтобы на компьютере, где устанавливается PowerPivot для SharePoint, уже имелся именованный экземпляр [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .

7.  Экземпляр [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] не может входить в состав отказоустойчивого кластера SQL Server. Используйте функции высокого уровня доступности продукта SharePoint. Например, службы Excel управляют распределением нагрузки серверов PowerPivot для SharePoint. Дополнительные сведения см. в разделе [Управление параметрами модели данных служб Excel (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx) (https://technet.microsoft.com/library/jj219780.aspx).

8.  Если [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] устанавливается в существующей ферме, необходимо наличие одного или нескольких веб-приложений SharePoint, в которых настроен классический режим проверки подлинности. Доступ к данным [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] поддерживается только в веб-приложениях, использующих классическую проверку подлинности Windows. Дополнительные сведения о требованиях к классическому режиму см. в разделе [PowerPivot Authentication and Authorization](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-authentication-and-authorization).

9. Изучите следующие дополнительные разделы, чтобы ознакомиться с требованиями к системе и версиям:

    -   [Указания по использованию функций бизнес-аналитики SQL Server в ферме SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)

##  <a name="InstallSQL"></a>Шаг 1. Установка PowerPivot для SharePoint
 На этом шаге запускается программа установки SQL Server для установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. На следующем шаге после установки выполняется настройка сервера.

1.  Вставьте установочный носитель в привод или откройте папку, в которой содержатся установочные файлы SQL Server, и дважды щелкните **setup.exe**.

2.  Щелкните **Установка** в левой навигационной панели.

3.  Щелкните **Новая установка изолированного экземпляра SQL Server или добавление компонентов к существующей установке**.

4.  На странице **Ключ продукта** укажите выпуск Evaluation Edition или введите ключ продукта для лицензированной копии выпуска Enterprise Edition.

     Щелкните **Далее**.

5.  Примите условия лицензионного соглашения на использование программного обеспечения Майкрософт. Мы будем благодарны, если вы также включите функции отправки отзывов и сообщений об ошибках. Щелкните **Далее**.

6.  Обновите файлы установки, если появится соответствующий запрос.

7.  На странице **Правила установки** программа установки определяет наличие любых проблем, которые могут помешать установке. Просмотрите список, чтобы определить, определила ли программа установки наличие потенциальных проблем в системе.

    > [!NOTE]
    >  Так как брандмауэр Windows включен, отобразится предупреждение о том, что для включения удаленного доступа необходимо открыть порты. Как правило, к установкам [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] это предупреждение неприменимо. Соединения со службами и файлами данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] выполняются с использованием портов SharePoint, уже открытых для взаимодействия служб SharePoint.

     Щелкните **Далее**. Дождитесь окончания установки на сервере программных файлов программы установки SQL Server.

8.  На странице **Роль установки** выберите **SQL Server PowerPivot для SharePoint**.

9. В установку при необходимости можно добавить экземпляр компонента Database Engine. Это можно сделать, если вы настраиваете новую ферму и вам нужен сервер базы данных для запуска конфигурации и баз данных содержимого фермы. Если добавить компонент Database Engine, он будет установлен как именованный экземпляр PowerPivot. Если необходимо указать соединение с этим экземпляром (например, в мастере настройки фермы, если для настройки фермы используется этот мастер), введите имя базы данных в следующем формате: <`servername`> \PowerPivot..

     ![GMNI_SetupUI_FeatureRole](../../../2014/sql-server/install/media/gmni-setupui-featurerole.gif "GMNI_SetupUI_FeatureRole")

10. Щелкните **Далее**.

11. На странице **Выбор компонентов** в ознакомительных целях отображается список компонентов, которые будут установлены (только для чтения). Представленные для этой роли элементы нельзя дополнить или удалить. Щелкните **Далее**.

12. На странице **правила функций** щелкните **Далее**. Эту страницу можно пропустить.

13. На странице **Конфигурация экземпляра** в ознакомительных целях отображается имя экземпляра «PowerPivot», доступное только для чтения. Имя экземпляра **POWERPIVOT** является **обязательным и не может быть изменено**. Однако можно ввести уникальный идентификатор экземпляра, а также описательное имя каталога и разделы реестра. Щелкните **Далее**.

14. На странице **Конфигурация сервера** введите требуемые сведения об учетной записи.

     Для служб SQL Server Analysis Services необходимо указать учетную запись пользователя домена. Не указывайте встроенную учетную запись. Учетная запись домена требуется для управления учетной записью службы Analysis Services как *управляемой учетной записью* в центре администрирования SharePoint Central.

     ![Настройка SSAS Server](../../../2014/sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "Настройка SSAS Server")

     Если был добавлен компонент SQL Server Database Engine и агент SQL Server, можно настроить запуск служб под учетной записью пользователя домена или виртуальной учетной записью по умолчанию.

     Никогда не указывайте собственную учетную запись пользователя домена для обеспечения работы служб. Это приведет к тому, что серверу будут предоставлены те же разрешения на сетевые ресурсы, что и вам. В случае получения злоумышленником доступа к серверу он сможет воспользоваться вашими учетными данными домена, что откроет ему доступ к тем же данным и приложениям, которыми можете пользоваться вы сами.

15. Щелкните **Далее**.

16. При установке компонента Database Engine откроется страница настройки компонента Database Engine. На странице «Настройка ядра СУБД» нажмите **Добавить текущего пользователя** , чтобы предоставить учетной записи пользователя разрешения администратора для экземпляра ядра СУБД. Нажмите кнопку **Добавить** , чтобы добавить дополнительные учетные записи. Щелкните **Далее**.

17. На странице **Конфигурация служб Analysis Services** нажмите **Добавить текущего пользователя** , чтобы предоставить учетной записи пользователя разрешения администратора. Для настройки сервера по окончании установки потребуются разрешения администратора.

18. На этой же странице добавьте учетную запись пользователя Windows, которому также требуются административные разрешения. Например, административные разрешения на сервере необходимы любому пользователю, который собирается подключаться к экземпляру [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] из среды SQL Server Management Studio для устранения неполадок подключения к базе данных или получения сведений о версии. Добавьте учетную запись пользователя, который сможет производить устранение проблем или администрирование сервера.

19. Щелкните **Далее**.

20. Нажимайте кнопку **Далее** на всех оставшихся страницах, пока не откроется страница «Все готово для установки».

21. Нажмите кнопку **Установить**.

> [!TIP]
>  Если требуется выполнить устранение неисправностей при установке SQL Server, см. раздел [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).

##  <a name="bkmk_config"></a>Шаг 2. Настройка сервера

> [!IMPORTANT]
>  Перед настройкой [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] или фермы SharePoint, в которой используется сервер баз данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , необходимо установить пакет обновления SharePoint 2010 SP2. Если пакет обновления еще не установлен, установите его перед тем, как начать настройку сервера.

 Установка не будет завершена до настройки сервера. В этом выпуске настройка сервера всегда выполняется после установки с использованием одного из следующих средств: Средство настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , центр администрирования или PowerShell. Для продолжения выберите один из следующих вариантов.

-   [Настройка или восстановление PowerPivot для SharePoint 2010 &#40;средства настройки PowerPivot&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md)

-   [Настройка и администрирование сервера PowerPivot в центре администрирования](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)

-   [Настройка PowerPivot с помощью Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell)

 **Соединение с экземпляром компонента Database Engine.** После установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]программа установки SQL Server предлагает возможность добавить к установке экземпляр компонента Database Engine. Возможно, вы добавили в установку экземпляр ядро СУБД, если вы настраиваете новую ферму и вам нужен сервер базы данных для запуска конфигурации и баз данных содержимого фермы. Если вы добавили компонент Database Engine, то он был установлен как именованный экземпляр [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Всякий раз, когда необходимо указать соединение с этим экземпляром (например, в мастере настройки фермы, если для настройки фермы используется этот мастер), не забудьте ввести имя базы данных в следующем формате: <`servername`> \PowerPivot..

##  <a name="bkmk_redist"></a>Шаг 3. Установка поставщиков OLE DB Analysis Services на серверах приложений служб Excel
 Потребуются дополнительные шаги установки, если службы вычислений Excel и [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] запускаются на разных серверах приложений. На серверах приложений, использующих службы вычислений Excel, установите соответствующую версию поставщика OLE DB для служб Analysis Services (MSOLAP).

-   Версия [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] MSOLAP включена в программу установки SQL Server, поэтому установка версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] MSOLAP требуется только в том случае, если сервер приложений не является сервером приложений PowerPivot.

    > [!NOTE]
    >  Серверу приложений служб вычислений Excel также требуется экземпляр файла **Microsoft.AnalysisServices.Xmla.dll** в глобальной сборке. Чтобы установить библиотеку DLL на сервере приложений, установите [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. На странице **Выбор компонентов** мастера установки SQL Server выберите "средства управления — Готово".

-   Если сервер приложений должен поддерживать старые книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , необходимо установить версию MSOLAP для SQL Server 2008 R2.

 Дополнительные сведения об установке поставщика, включая шаги для проверки, см. в разделе [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).

##  <a name="bkmk_verify"></a>Шаг 4. Проверка установки
 На этом последнем шаге убедитесь в полной работоспособности SharePoint 2010 и [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . Инструкции см. в разделе [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation).

## <a name="see-also"></a>См. также:
 Контрольный список развертывания [установки PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md) . Контрольный список развертывания [Reporting Services, Power View и PowerPivot для SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) [. Развертывание с добавлением серверов PowerPivot в ферму SharePoint 2010](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md) [контрольный список: Установка нескольких серверов PowerPivot для SharePoint 2010](../../../2014/sql-server/install/deployment-checklist-multiserver-installation-powerpivot-sharepoint-2010.md)


