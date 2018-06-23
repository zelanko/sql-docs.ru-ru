---
title: Запуск помощника по обновлению (Командная строка) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Upgrade Advisor [SQL Server], running
- command prompt [Upgrade Advisor]
- UpgradeAdvisorWizardCmd utility
- XML formats [Upgrade Advisor]
ms.assetid: 7c83049b-9227-4723-9b7f-66288bc6bd1d
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 525cb2237795e778bef2aa33ad43cff7c2e5ad6d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086851"
---
# <a name="running-upgrade-advisor-command-prompt"></a>Запуск помощника по обновлению (командная строка)
  Используйте **UpgradeAdvisorWizardCmd** служебная программа для запуска помощника по обновлению из командной строки. Можно задать вывод результата в формате XML или в файле формата CSV (с разделителями-запятыми).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      UpgradeAdvisorWizardCmd [ -? ]  |   
    [ -ConfigFilefilename | <server_info> ]  
    [ -SqlUserlogin_id-SqlPasswordpassword ]  
    [ -CSV ]  
  
where <server_info> is any combination of the following:  
        -Serverserver_name-Instanceinstance_name-ASInstanceAS_instance_name-RSInstanceRS_instance_name  
```  
  
## <a name="arguments"></a>Аргументы  
 **-?**  
 Отображает синтаксис команды.  
  
 **-ConfigFile** *имя файла*  
 Путь и имя файла в XML-файл, содержащий параметры для использования при запуске **UpgradeAdvisorWizardCmd** программы.  
  
 *< сведения_о_сервере >*  
 Задает анализируемый компьютер и экземпляр. Используйте эти параметры, если не применяется файл конфигурации.  
  
 *< сведения_о_сервере >* может быть любым сочетанием следующих четырех аргументов:  
  
 **-Сервер** *имя_сервера*  
 Задает имя компьютера для проведения анализа. Это может быть локальный компьютер (значение по умолчанию) или удаленный компьютер.  
  
 **-Экземпляр** *имя_экземпляра*  
 Задает имя анализируемого экземпляра. Значение по умолчанию отсутствует. Если этот параметр не указан, то компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] просматриваться не будет. Значением для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию является MSSQLSERVER. Для именованного экземпляра укажите имя экземпляра.  
  
 **-ASInstance***AS_instance_name*   
 Задает имя экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для анализа. Значение по умолчанию отсутствует. Если это значение не указано, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] просматриваться не будут. Значением для экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] по умолчанию является MSSQLServerOLAPService. Для именованного экземпляра укажите имя экземпляра.  
  
 **-RSInstance***RS_instance_name*   
 Задает имя экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для анализа. Значение по умолчанию отсутствует. Если это значение не указано, то службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] просматриваться не будут. Значением для экземпляра по умолчанию служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] является ReportServer. Для именованного экземпляра укажите имя экземпляра.  
  
 **-SqlUser** *login_id*  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это значение является именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которое помощник по обновлению использует для соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если имя входа не указано, для соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется проверка подлинности Windows.  
  
 **-SqlPassword** *пароля*  
 Если вы используете **- SqlUser** аргумент, этот аргумент используется, чтобы указать пароль для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа.  
  
 **-CSV**  
 Укажите этот аргумент, чтобы сформировать результат в виде CSV-файла с разделителями-запятыми дополнительно к стандартному представлению результатов в виде XML. Результаты записываются в Мои документы\\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \110\отчеты».  
  
## <a name="return-values"></a>Возвращаемые значения  
 Следующая таблица показывает значения **UpgradeAdvisorWizardCmd** возвращает.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Анализ успешно завершен, проблем с обновлением не обнаружено.|  
|положительное целое число|Анализ успешно завершен, обнаружены проблемы с обновлением.|  
|отрицательное целое число|Анализ не выполнен.|  
  
## <a name="remarks"></a>Примечания  
 За исключением имен пользователей и паролей для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], вся информация, необходимая для запуска анализа, может быть предоставлена в XML-файле конфигурации. Этот XML-файл конфигурации документирован в шаблоне. Можно анализировать все установленные компоненты в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] без применения файла конфигурации со значениями по умолчанию, указав имена компьютеров и имена экземпляров. Описания настроек файла конфигурации по умолчанию см. далее в этом разделе в таблице «Описание элементов».  
  
## <a name="configuration-file-template"></a>Шаблон файла конфигурации  
 Следующий XML-файл можно использовать в качестве шаблона для создания собственных файлов конфигурации. Шаблон можно изменить в соответствии с потребностями конкретной организации.  
  
```xml  
<Configuration>  
    <Server> </Server>  
    <Instance></Instance>  
    <Components>  
        <SQLServer>  
            <Databases>  
                <Database></Database>  
            </Databases>  
            <TraceFiles>  
                <TraceFile></TraceFile>  
            </TraceFiles>  
            <BatchFiles>  
                <BatchFile></BatchFile>  
            </BatchFiles>  
            <BatchSeparator></BatchSeparator>  
        </SQLServer>  
        <AnalysisServices>  
            <ASInstance></ASInstance>  
            <Databases>  
                <Database></Database>  
            </Databases>  
        </AnalysisServices>  
        <ReportingServices>  
            <RSInstance></RSInstance>  
        </ReportingServices>  
        <IntegrationServices>  
            <PackagePath></PackagePath>  
        </IntegrationServices>  
    </Components>  
</Configuration>  
```  
  
## <a name="element-descriptions"></a>Описание элементов  
  
|Тег|Определение|Наличие|  
|---------|----------------|----------------|  
|`Configuration`|Родительский элемент для файла конфигурации помощника по обновлению.|Должен присутствовать один раз в каждом файле конфигурации.|  
|`Server`|Имя анализируемого сервера.|Может присутствовать один раз в каждом файле конфигурации. Значением по умолчанию является локальный компьютер.|  
|`Instance`|Имя экземпляра анализируемого компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].|Может присутствовать один раз в каждом файле конфигурации. Значением по умолчанию является экземпляр по умолчанию.<br /><br /> Требуется один раз для каждого файла конфигурации, если на сервере имеется элемент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или элемент `IntegrationServices`.|  
|`Components`|Содержит элементы, указывающие анализируемые компоненты.|Должен присутствовать один раз в каждом файле конфигурации.|  
|`SQLServer`|Содержит настройки анализа для экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].|Может присутствовать один раз в каждом файле конфигурации. Если не задан, базы данных компонента служб [!INCLUDE[ssDE](../../includes/ssde-md.md)] не анализируются.|  
|Значение `Databases` для элемента `SQLServer`|Содержит список анализируемых баз данных.|Один раз для каждого `SQLServer` элемента. Если этот элемент отсутствует, выполняется анализ всех баз данных на экземпляре.|  
|Значение `Database` для элемента `SQLServer`|Задает имя базы данных для анализа.|Должен присутствовать не менее одного раза, если присутствует элемент `Databases`. Если элемент `Database` содержит значение «*», будут проанализированы все базы данных в экземпляре. Значение по умолчанию отсутствует.|  
|`TraceFiles`|Содержит список анализируемых файлов трассировки.|Один раз для каждого `SQLServer` элемента.|  
|`TraceFile`|Задает путь и имя анализируемого файла трассировки.|Должен присутствовать не менее одного раза, если присутствует элемент `TraceFiles`. Значение по умолчанию отсутствует.|  
|`BatchFiles`|Содержит список анализируемых пакетных файлов.|Один раз для каждого `SQLServer` элемента.|  
|`BatchFile`|Задает анализируемый пакетный файл. Может быть указан несколько раз.|Должен присутствовать не менее одного раза, если присутствует элемент `BatchFiles`. Значение по умолчанию отсутствует.|  
|`BatchSeparator`|Задает разделитель пакетов, используемый в пакетных файлах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Один раз для каждого `SQLServer` элемента. Значение по умолчанию — GO.|  
|`AnalysisServices`|Содержит параметры анализа для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|Может присутствовать один раз в каждом файле конфигурации. Если не задан, базы данных компонента служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не анализируются.|  
|`ASInstance`|Задает имя экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|Требуется один раз на `AnalysisServices` элемент. Значение по умолчанию отсутствует.|  
|Значение `Databases` для элемента `Analysis Services`|Содержит список анализируемых баз данных.|Один раз для каждого `AnalysisServices` элемента. Если этот элемент отсутствует, выполняется анализ всех баз данных на экземпляре.|  
|Значение `Database` для элемента `AnalysisServices`|Задает имя базы данных для анализа.|Должен присутствовать не менее одного раза, если присутствует элемент `Databases`. Если элемент `Database` содержит значение «*», будут проанализированы все базы данных в экземпляре. Значение по умолчанию отсутствует.|  
|`ReportingServices`|Указывает, что будет запущен анализ служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|Может присутствовать один раз в каждом файле конфигурации. Если не указан, анализ служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не выполняется.|  
|`RSInstance`|Задает имя экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|Требуется один раз на `ReportingServices` элемент. Значение по умолчанию отсутствует.|  
|`IntegrationServices`|Содержит параметры анализа для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|Может присутствовать один раз в каждом файле конфигурации. Если не указан, анализ служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не выполняется.|  
|`PackagePath`|Задает путь к набору пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|Один раз для каждого `IntegrationServices` элемента. Если этот элемент отсутствует, будет выполнен анализ экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а пакеты, хранящиеся вне экземпляра, анализироваться не будут. Значение по умолчанию отсутствует.|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-run-upgrade-advisor-using-a-configuration-file"></a>A. Запуск помощника по обновлению с помощью файла конфигурации  
 В следующем примере показано, как запустить помощник по обновлению из командной строки с использованием файла конфигурации, в котором определена область анализа. Для соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в данном примере используется проверка подлинности Windows.  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"  
```  
  
### <a name="b-run-upgrade-advisor-using-default-configuration-settings"></a>Б. Запуск помощника по обновлению с помощью настроек конфигурации, установленных по умолчанию  
 В следующем примере показано, как запустить помощник по обновлению из командной строки, используя параметры конфигурации по умолчанию и проверку подлинности Windows.  
  
```  
UpgradeAdvisorWizardCmd -Server MyServer -Instance MyInst   
```  
  
### <a name="c-run-upgrade-advisor-using-includessnoversionincludesssnoversion-mdmd-authentication"></a>В. Запуск помощника по обновлению с помощью проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 В следующем примере показано, как запустить помощник по обновлению из командной строки с использованием файла конфигурации. В примере указывается имя пользователя и пароль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"   
    -SqlUser "MyUserName" -SqlPassword "QweRTy-55"  
```  
  
## <a name="see-also"></a>См. также  
 [Разрешение проблем с обновлением](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Запуск помощника по обновлению &#40;пользовательского интерфейса&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)  
  
  