---
title: Командная строка установки компонентов R и Python — машинного обучения SQL Server
description: Запустите программу установки командной строки SQL Server, добавляемый экземпляр ядра СУБД SQL Server поддерживает язык R и Python интеграции.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/21/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8e3c101eae8e02446a9e47b17255e2ca2b501774
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645530"
---
# <a name="install-sql-server-machine-learning-r-and-python-components-from-the-command-line"></a>Установка SQL Server в машинном обучении компоненты R и Python из командной строки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья содержит инструкции по intalling SQL Server в машинном обучении компонентов из командной строки:

+ [Новые функции в базе данных экземпляра](#indb)
+ [Добавить к существующему экземпляру ядра базы данных](#add-existing)
+ [Автоматическая установка](#silent)
+ [Новый изолированный сервер](#shared-feature)

Вы можете указать автоматической, базовое или полное взаимодействие с пользовательским интерфейсом программы установки. В этой статье дополняет [Установка SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md), охватывающий параметры, уникальные для R и Python компонентов машинного обучения.

## <a name="pre-install-checklist"></a>Контрольный список перед установкой

+ Выполнение команд из командной строки с повышенными правами. 

+ Экземпляр ядра СУБД является обязательным для установки в базе данных. Не удается установить только компоненты R или Python, несмотря на то, что вы можете [постепенно добавить их к существующему экземпляру](#add-existing). Если требуется просто R и Python без ядра СУБД установить [изолированный сервер](#shared-feature).

+ Не устанавливайте в отказоустойчивом кластере. Механизм безопасности, используемый для изолирования процессов R и Python не совместим с среде отказоустойчивого кластера Windows Server.

+ Не следует устанавливать на контроллере домена. Службы машинного обучения часть установки завершится ошибкой.

+ Избегайте установки "Автономный" и в базе данных экземпляров на одном компьютере. Автономный сервер будут конкурировать за те же ресурсы, ставя под угрозу производительность обеих установок.


## <a name="command-line-arguments"></a>Аргументы командной строки

Аргумент функции является обязательным, как лицензировании термин. 

При установке из командной строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает полностью тихий режим (включается параметром /Q) и простой тихий режим (включается параметром /QS). При указании параметра /QS показывается только ход выполнения, не запрашивается ввод данных и не выводятся сообщения об обнаруженных ошибках. Параметр /QS поддерживается только в случае, когда указан режим /Action=install.

| Аргументы | Описание |
|-----------|-------------|
| / ФУНКЦИИ = AdvancedAnalytics | Устанавливает версию в базе данных: Службы машинного обучения из состава SQL Server 2017 (в базе данных) или SQL Server 2016 R Services (в базе данных).  |
| / ФУНКЦИИ = SQL_INST_MR | Применимо к SQL Server 2017 только. Для сопоставления с AdvancedAnalytics. Устанавливает компонент (в базе данных) R, включая Microsoft R Open и собственные пакеты R. Компонент SQL Server 2016 R Services R только, поэтому параметр для этого выпуска не существует.|
| / ФУНКЦИИ = SQL_INST_MPY | Применимо к SQL Server 2017 только. Для сопоставления с AdvancedAnalytics. Устанавливает функцию Python (в базе данных), в том числе Anaconda и частные пакеты Python. |
| / ФУНКЦИИ = SQL_SHARED_MR | Устанавливает службы R для автономной версии: Сервер SQL Server 2017 машинного обучения (автономный) или SQL Server 2016 R Server (изолированный). Изолированный сервер — это «общий компонент» не привязан к экземпляру ядра базы данных.|
| / ФУНКЦИИ = SQL_SHARED_MPY | Применимо к SQL Server 2017 только. Устанавливает компонент Python для автономной версии: SQL Server 2017 Machine Learning Server (изолированную версию). Изолированный сервер — это «общий компонент» не привязан к экземпляру ядра базы данных.|
| /IACCEPTROPENLICENSETERMS  | Указывает, что вы приняли условия лицензионного соглашения по использованию компонентов R с открытым исходным. |
| /IACCEPTPYTHONLICENSETERMS | Указывает, что вы приняли условия лицензионного соглашения по использованию компонентов Python. |
| /IACCEPTSQLSERVERLICENSETERMS | Указывает, что вы приняли условия лицензионного соглашения по использованию SQL Server.|
| / MRCACHEDIRECTORY | Для установки в автономном режиме устанавливается в папку, содержащую CAB-файлы компонентов R. |
| / MPYCACHEDIRECTORY | Для установки в автономном режиме устанавливается в папку, содержащую CAB-файлы компонентов Python. |


## <a name="indb"></a> Установку экземпляра базы данных

Аналитика в базе данных доступны для экземпляров компонента database engine, необходимые для добавления **AdvancedAnalytics** компонент для установки. Расширенные средства аналитики, можно установить экземпляр ядра СУБД или [добавляется к существующему экземпляру](#add-existing). 

На экране для просмотра сведений о ходе выполнения без интерактивных запросов, используйте аргумент/qs.

> [!IMPORTANT]
> После установки остаются два дополнительных действий по настройке. Интеграция остается незавершенной, пока эти задачи выполняются. См. в разделе [послеустановочных задач](#post-install) инструкции.

### <a name="sql-server-2017-database-engine-advanced-analytics-with-python-and-r"></a>SQL Server 2017: ядро СУБД, расширенная аналитика с помощью Python и R

Для параллельной установки экземпляра ядра СУБД укажите имя экземпляра и учетная запись администратора (Windows). Включить функции для установки основных компонентов языка, а также принятие всех условий лицензирования.

```cmd
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

Этот же команду, с учетом имени входа SQL Server для ядра базы данных с помощью смешанного проверки подлинности.

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<sql-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

Данный пример является Python, показывающий, можно добавить один язык, опустив компонент.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTPYTHONLICENSETERMS
```

### <a name="sql-server-2016-database-engine-and-advanced-analytics-with-r"></a>SQL Server 2016: компонент database engine и расширенной аналитики с помощью R

Эта команда идентична SQL Server 2017, но без элементов, Python, которые доступны не в программе установки SQL Server 2016.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS 
```

## <a name="post-install"></a> После установки конфигурации (обязательно)

Применяется для установки только в базе данных.

По завершении установки у вас есть экземпляр ядра СУБД с помощью пакетов R и Python, Microsoft R и Python, Microsoft R Open, Anaconda, средства, примеры и сценарии, которые являются частью распределение. 

Для завершения установки требуются две дополнительные задачи:

1. Перезапустите службы компонента database engine.

1. Включите внешние скрипты, прежде чем можно будет использовать функцию. Следуйте инструкциям в [установить SQL Server 2017 служб машинного обучения (в базе данных)](sql-machine-learning-services-windows-install.md) следующим шагом. 

Для SQL Server 2016, воспользуйтесь этой статьей, вместо этого [установить SQL Server 2016 R Services (в базе данных)](sql-r-services-windows-install.md).

## <a name="add-existing"></a> Добавление расширенной аналитики в существующий экземпляр ядра базы данных

При добавлении расширенной аналитики в базе данных в существующий экземпляр ядра базы данных, введите имя экземпляра. Например если вы ранее установили ядро СУБД SQL Server 2017 и Python, можно использовать эту команду для добавления R.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQL_INST_MR /INSTANCENAME=MSSQLSERVER 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTROPENLICENSETERMS
```



## <a name="silent"></a> Автоматическая установка

Автоматическая установка подавляет поиск расположения файлов .cab. По этой причине необходимо указать расположение, куда должны быть распакованы CAB-файлы. Для этого можно временный каталог.
 
```cmd  
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS 
/MRCACHEDIRECTORY=%temp% /MPYCACHEDIRECTORY=%temp%
```

## <a name="shared-feature"></a> Установок отдельного сервера

Изолированный сервер — это «общий компонент» не привязан к экземпляру ядра базы данных. Ниже приведены примеры синтаксиса для обоих выпусков.

SQL Server 2017 поддерживает Python и R на изолированном сервере:

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR,SQL_SHARED_MPY  
/IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

SQL Server 2016 — только для R:

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR 
/IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

По завершении установки у вас есть сервер, пакеты Microsoft, распределение открытым исходным кодом R и Python, средства, примеры и сценарии, которые являются частью распределение. 

Чтобы открыть окно консоли R, \R_SERVER\bin\x64 go \Program files\Microsoft SQL server\140; (или 130) и дважды щелкните **RGui.exe**. Не знакомы с R? Пройти обучение: [Основные команды R и функциях RevoScaleR: 25 наиболее распространенные](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler).

Чтобы открыть команду Python, перейдите к \Program files\Microsoft SQL Server\140\PYTHON_SERVER\bin\x64 и дважды щелкните **python.exe**.

## <a name="get-help"></a>Получить справку

Нужна помощь с установку или обновление? Ответы на часто задаваемые вопросы и известные проблемы обратитесь к следующей статье:

* [Обновление и установка часто задаваемые вопросы – службы машинного обучения](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Чтобы проверить состояние установки экземпляра и исправлять распространенные проблемы, используйте эти пользовательские отчеты.

* [Пользовательские отчеты для служб R SQL Server](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Следующие шаги

Разработчики R можно приступить к работе с простыми примерами и ознакомиться с основами как R работает с SQL Server. Следующий шаг см. следующие ссылки:

+ [Учебник. Запуск R в T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Учебник. Аналитика в базе данных для разработчиков R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Разработчики Python рассказывается, как использовать Python с SQL Server с помощью этих учебных материалов:

+ [Учебник. Запустите Python в T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Учебник. Аналитика в базе данных для разработчиков Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Чтобы просмотреть примеры машинного обучения, которые основаны на реальных сценариев, см. в разделе [машинного обучения учебники](../tutorials/machine-learning-services-tutorials.md).