---
title: Запуск помощника по обновлению (Командная строка) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], running
- command prompt [Upgrade Advisor]
- UpgradeAdvisorWizardCmd utility
- XML formats [Upgrade Advisor]
ms.assetid: 7c83049b-9227-4723-9b7f-66288bc6bd1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8de6913085c24f98d8305f622f5cbec31aa2a79c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058971"
---
# <a name="running-upgrade-advisor-command-prompt"></a>Запуск помощника по обновлению (командная строка)
  Используйте служебную программу **UpgradeAdvisorWizardCmd** для запуска помощника по обновлению из командной строки. Можно задать вывод результата в формате XML или в файле формата CSV (с разделителями-запятыми).  
  
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
  
 **-ConfigFile** _имя файла_  
 — Это путь и имя файла XML, содержащего параметры, используемые при запуске служебной программы **UpgradeAdvisorWizardCmd** .  
  
 *<server_info>*  
 Задает анализируемый компьютер и экземпляр. Используйте эти параметры, если не применяется файл конфигурации.  
  
 *<server_info>* может быть любым сочетанием следующих четырех аргументов:  
  
 **-Server** _server_name_  
 Задает имя компьютера для проведения анализа. Это может быть локальный компьютер (значение по умолчанию) или удаленный компьютер.  
  
 **-Instance** _instance_name_  
 Задает имя анализируемого экземпляра. Значение по умолчанию отсутствует. Если этот параметр не указан, то компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] просматриваться не будет. Значением для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию является MSSQLSERVER. Для именованного экземпляра укажите имя экземпляра.  
  
 **-Асинстанце**  _AS_instance_name_  
 Задает имя экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для анализа. Значение по умолчанию отсутствует. Если это значение не указано, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] просматриваться не будут. Значением для экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] по умолчанию является MSSQLServerOLAPService. Для именованного экземпляра укажите имя экземпляра.  
  
 **-Рсинстанце**  _RS_instance_name_  
 Задает имя экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для анализа. Значение по умолчанию отсутствует. Если это значение не указано, то службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] просматриваться не будут. Значением для экземпляра по умолчанию служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] является ReportServer. Для именованного экземпляра укажите имя экземпляра.  
  
 **-SqlUser** _login_ID_  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это значение является именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которое помощник по обновлению использует для соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если имя входа не указано, для соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется проверка подлинности Windows.  
  
 **-SqlPassword** _пароль_  
 Если используется аргумент **-SqlUser** , используйте этот аргумент, чтобы указать пароль для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа.  
  
 **-CSV**  
 Укажите этот аргумент, чтобы сформировать результат в виде CSV-файла с разделителями-запятыми дополнительно к стандартному представлению результатов в виде XML. Результаты записываются в папку "Мои документы" \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Advisor\110\Reports Upgrade.  
  
## <a name="return-values"></a>Возвращаемые значения  
 В следующей таблице показаны значения, возвращаемые **UpgradeAdvisorWizardCmd** .  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Анализ успешно завершен, проблем с обновлением не обнаружено.|  
|положительное целое число|Анализ успешно завершен, обнаружены проблемы с обновлением.|  
|отрицательное целое число|Анализ не выполнен.|  
  
## <a name="remarks"></a>Remarks  
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
|Значение `Databases` для элемента `SQLServer`|Содержит список анализируемых баз данных.|Необязательный один раз для каждого `SQLServer` элемента. Если этот элемент отсутствует, выполняется анализ всех баз данных на экземпляре.|  
|Значение `Database` для элемента `SQLServer`|Задает имя базы данных для анализа.|Должен присутствовать не менее одного раза, если присутствует элемент `Databases`. Если элемент `Database` содержит значение «*», будут проанализированы все базы данных в экземпляре. Значение по умолчанию отсутствует.|  
|`TraceFiles`|Содержит список анализируемых файлов трассировки.|Необязательный один раз для каждого `SQLServer` элемента.|  
|`TraceFile`|Задает путь и имя анализируемого файла трассировки.|Должен присутствовать не менее одного раза, если присутствует элемент `TraceFiles`. Значение по умолчанию отсутствует.|  
|`BatchFiles`|Содержит список анализируемых пакетных файлов.|Необязательный один раз для каждого `SQLServer` элемента.|  
|`BatchFile`|Задает анализируемый пакетный файл. Может быть указан несколько раз.|Должен присутствовать не менее одного раза, если присутствует элемент `BatchFiles`. Значение по умолчанию отсутствует.|  
|`BatchSeparator`|Задает разделитель пакетов, используемый в пакетных файлах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Необязательный один раз для каждого `SQLServer` элемента. Значение по умолчанию — GO.|  
|`AnalysisServices`|Содержит параметры анализа для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|Может присутствовать один раз в каждом файле конфигурации. Если не задан, базы данных компонента служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не анализируются.|  
|`ASInstance`|Задает имя экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|Требуется один раз на каждый элемент `AnalysisServices`. Значение по умолчанию отсутствует.|  
|Значение `Databases` для элемента `Analysis Services`|Содержит список анализируемых баз данных.|Необязательный один раз для каждого `AnalysisServices` элемента. Если этот элемент отсутствует, выполняется анализ всех баз данных на экземпляре.|  
|Значение `Database` для элемента `AnalysisServices`|Задает имя базы данных для анализа.|Должен присутствовать не менее одного раза, если присутствует элемент `Databases`. Если элемент `Database` содержит значение «*», будут проанализированы все базы данных в экземпляре. Значение по умолчанию отсутствует.|  
|`ReportingServices`|Указывает, что будет запущен анализ служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|Может присутствовать один раз в каждом файле конфигурации. Если не указан, анализ служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не выполняется.|  
|`RSInstance`|Задает имя экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|Требуется один раз на каждый элемент `ReportingServices`. Значение по умолчанию отсутствует.|  
|`IntegrationServices`|Содержит параметры анализа для служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|Может присутствовать один раз в каждом файле конфигурации. Если не указан, анализ служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не выполняется.|  
|`PackagePath`|Задает путь к набору пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|Необязательный один раз для каждого `IntegrationServices` элемента. Если этот элемент отсутствует, будет выполнен анализ экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а пакеты, хранящиеся вне экземпляра, анализироваться не будут. Значение по умолчанию отсутствует.|  
  
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
  
### <a name="c-run-upgrade-advisor-using-ssnoversion-authentication"></a>В. Запуск помощника по обновлению с помощью проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 В следующем примере показано, как запустить помощник по обновлению из командной строки с использованием файла конфигурации. В примере указывается имя пользователя и пароль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"   
    -SqlUser "MyUserName" -SqlPassword "QweRTy-55"  
```  
  
## <a name="see-also"></a>См. также:  
 [Устранение проблем с обновлением](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Работа с советником по переходу](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Запуск помощника по обновлению &#40;пользовательского интерфейса&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)  
  
  
