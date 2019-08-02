---
title: Установка компонентов R и Python из командной строки
description: Запустите программу установки SQL Server командной строки, чтобы добавить язык R и интеграцию Python в SQL Server экземпляре ядра СУБД.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3e1e74c9d14c93cf44a7da5db4795a1524d238be
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715271"
---
# <a name="install-sql-server-machine-learning-r-and-python-components-from-the-command-line"></a>Установка компонентов R и Python машинного обучения SQL Server из командной строки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье приводятся инструкции по установке SQL Server компонентов машинного обучения из командной строки.

+ [Новый экземпляр в базе данных](#indb)
+ [Добавить в существующий экземпляр ядра СУБД](#add-existing)
+ [Автоматическая установка](#silent)
+ [Новый изолированный сервер](#shared-feature)

Можно указать автоматическое, простое или полное взаимодействие с пользовательским интерфейсом программы установки. Эта статья дополняет [установку SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md), охватывающую параметры, уникальные для компонентов машинного обучения R и Python.

## <a name="pre-install-checklist"></a>Контрольный список перед установкой

+ Выполните команды из командной строки с повышенными привилегиями. 

+ Экземпляр ядра СУБД необходим для установки в базе данных. Вы не можете установить только функции R или Python, хотя [их можно добавить в существующий экземпляр постепенно](#add-existing). Если требуется только R и Python без ядра СУБД, установите [изолированный сервер](#shared-feature).

+ Не устанавливайте в отказоустойчивый кластер. Механизм безопасности, используемый для изоляции процессов R и Python, несовместим с средой отказоустойчивого кластера Windows Server.

+ Не устанавливайте на контроллере домена. Службы машинного обучения часть программы установки завершится ошибкой.

+ Не следует устанавливать автономные и экземпляры в базе данных на одном компьютере. Изолированный сервер будет конкурировать за одни и те же ресурсы, и производительность обеих установок может быть снижена.


## <a name="command-line-arguments"></a>Аргументы командной строки

Аргумент FEATUREs является обязательным, как и соглашения о условии лицензирования. 

При установке из командной строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает полностью тихий режим (включается параметром /Q) и простой тихий режим (включается параметром /QS). При указании параметра /QS показывается только ход выполнения, не запрашивается ввод данных и не выводятся сообщения об обнаруженных ошибках. Параметр /QS поддерживается только в случае, когда указан режим /Action=install.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
| Аргументы | Описание |
|-----------|-------------|
| /FEATURES = Адванцеданалитикс | Устанавливает версию в базе данных: SQL Server R Services (в базе данных).  |
| /FEATURES = SQL_SHARED_MR | Устанавливает компонент R для автономной версии: SQL Server R Server (изолированный). Изолированный сервер — это "общий компонент", не привязанный к экземпляру ядра СУБД.|
| /IACCEPTROPENLICENSETERMS  | Указывает, что вы приняли условия лицензионного соглашения на использование компонентов R с открытым исходным кодом. |
| /IACCEPTPYTHONLICENSETERMS | Указывает, что вы приняли условия лицензионного соглашения на использование компонентов Python. |
| /IACCEPTSQLSERVERLICENSETERMS | Указывает, что вы приняли условия лицензионного соглашения на использование SQL Server.|
| /МРКАЧЕДИРЕКТОРИ | Для автономной установки задает папку, содержащую CAB-файлы компонента R. |
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
| Аргументы | Описание |
|-----------|-------------|
| /FEATURES = Адванцеданалитикс | Устанавливает версию в базе данных: SQL Server Службы машинного обучения (в базе данных).  |
| /FEATURES = SQL_INST_MR | Свяжите это с Адванцеданалитикс. Устанавливает функцию R (в базе данных), включая Microsoft R Open и частные пакеты R. |
| /FEATURES = SQL_INST_MPY | Свяжите это с Адванцеданалитикс. Устанавливает компонент Python (в базе данных), включая Anaconda и частные пакеты Python. |
| /FEATURES = SQL_SHARED_MR | Устанавливает компонент R для автономной версии: SQL Server Machine Learning Server (автономный). Изолированный сервер — это "общий компонент", не привязанный к экземпляру ядра СУБД.|
| /FEATURES = SQL_SHARED_MPY | Устанавливает компонент Python для автономной версии: SQL Server Machine Learning Server (автономный). Изолированный сервер — это "общий компонент", не привязанный к экземпляру ядра СУБД.|
| /IACCEPTROPENLICENSETERMS  | Указывает, что вы приняли условия лицензионного соглашения на использование компонентов R с открытым исходным кодом. |
| /IACCEPTPYTHONLICENSETERMS | Указывает, что вы приняли условия лицензионного соглашения на использование компонентов Python. |
| /IACCEPTSQLSERVERLICENSETERMS | Указывает, что вы приняли условия лицензионного соглашения на использование SQL Server.|
| /МРКАЧЕДИРЕКТОРИ | Для автономной установки задает папку, содержащую CAB-файлы компонента R. |
| /МПИКАЧЕДИРЕКТОРИ | Зарезервировано для будущего использования. Используйте% TEMP% для хранения CAB-файлов компонента Python для установки на компьютерах без подключения к Интернету. |
::: moniker-end

## <a name="indb"></a>Установка экземпляра в базе данных

Аналитика в базе данных доступна для экземпляров ядра СУБД, необходимых для добавления компонента **адванцеданалитикс** в установку. Можно установить экземпляр ядра СУБД с расширенной аналитикой или [добавить его в существующий экземпляр](#add-existing). 

Чтобы просмотреть сведения о ходе выполнения без интерактивных запросов на экране, используйте аргумент/QS.

> [!IMPORTANT]
> После установки остаются два дополнительных этапа настройки. Интеграция не будет завершена до выполнения этих задач. Инструкции см. в разделе [задачи, выполняемые после установки](#post-install) .

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
### <a name="sql-server-machine-learning-services-database-engine-advanced-analytics-with-python-and-r"></a>SQL Server Службы машинного обучения: ядро СУБД, Расширенная аналитика с Python и R

Для параллельной установки экземпляра ядра СУБД укажите имя экземпляра и имя входа администратора (Windows). Включает функции для установки основных и языковых компонентов, а также принятие всех условий лицензирования.

```cmd
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

Это та же команда, но с SQL Server именем входа в ядре СУБД с использованием смешанной проверки подлинности.

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<sql-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

Этот пример только для Python, показывая, что можно добавить один язык, опустив функцию.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTPYTHONLICENSETERMS
```
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
### <a name="sql-server-r-services-database-engine-and-advanced-analytics-with-r"></a>SQL Server R Services: ядро СУБД и Расширенная аналитика с помощью R

Для параллельной установки экземпляра ядра СУБД укажите имя экземпляра и имя входа администратора (Windows). Включает функции для установки основных и языковых компонентов, а также принятие всех условий лицензирования.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS 
```
::: moniker-end

## <a name="post-install"></a>Настройка после установки (обязательно)

Применяется только к установкам в базе данных.

После завершения установки вы получите экземпляр ядра СУБД с R и Python, пакетами Microsoft R и Python, Microsoft R Open, Anaconda, инструментами, образцами и сценариями, которые являются частью дистрибутива. 

Для завершения установки требуются еще две задачи:


::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
1. Перезапустите службу ядра СУБД.

1. Службы машинного обучения SQL Server: Включите внешние скрипты, прежде чем можно будет использовать эту функцию. Следуйте инструкциям в статье [установка SQL Server службы машинного обучения (в базе данных)](sql-machine-learning-services-windows-install.md) в качестве следующего шага. 
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
1. Перезапустите службу ядра СУБД.

1. SQL Server R Services: Включите внешние скрипты, прежде чем можно будет использовать эту функцию. Следуйте инструкциям в статье [установка SQL Server R Services (в базе данных)](sql-r-services-windows-install.md) в качестве следующего шага. 
::: moniker-end

## <a name="add-existing"></a>Добавление расширенной аналитики к существующему экземпляру ядра СУБД

При добавлении расширенной аналитики в базе данных к существующему экземпляру ядра СУБД укажите имя экземпляра. Например, если ранее вы установили ядро СУБД SQL Server 2017 и Python, эту команду можно использовать для добавления R.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQL_INST_MR /INSTANCENAME=MSSQLSERVER 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTROPENLICENSETERMS
```

## <a name="silent"></a>Автоматическая установка

Автоматическая установка отключает проверку расположения CAB-файлов. По этой причине необходимо указать расположение, в котором будут распакованы CAB-файлы. Для Python CAB-файлы должны находиться в папке% TEMP *. Для R можно задать путь к папке, используя для этого каталог Temp.
 
```cmd  
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS 
/MRCACHEDIRECTORY=%temp% 
```

## <a name="shared-feature"></a>Установки изолированного сервера

Изолированный сервер — это "общий компонент", не привязанный к экземпляру ядра СУБД. В следующих примерах показан допустимый синтаксис для установки изолированного сервера.

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
SQL Server Machine Learning Server поддерживает Python и R на изолированном сервере:

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR,SQL_SHARED_MPY  
/IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
SQL Server R Server доступен только для R:

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR 
/IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```
::: moniker-end

После завершения установки вы получите сервер, пакеты Microsoft, дистрибутивы R и Python, средства, примеры и сценарии, которые являются частью дистрибутива. 

Чтобы открыть окно консоли R, перейдите в `\Program files\Microsoft SQL Server\150 (or 140/130)\R_SERVER\bin\x64` раздел и дважды щелкните **RGui. exe**. Не знакомы с R? Воспользуйтесь этим руководством: [Основные команды R и функции RevoScaleR: 25 распространенных примеров](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler).

Чтобы открыть команду Python, перейдите к `\Program files\Microsoft SQL Server\150 (or 140)\PYTHON_SERVER\bin\x64` **файлу Python. exe**и дважды щелкните его.

## <a name="get-help"></a>Получить справку

Нужна помощь с установкой или обновлением? Ответы на часто задаваемые вопросы и известные проблемы см. в следующей статье:

* [Вопросы и ответы по обновлению и установке — Службы машинного обучения](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Чтобы проверить состояние установки экземпляра и устранить распространенные проблемы, попробуйте использовать эти пользовательские отчеты.

* [Пользовательские отчеты для SQL Server](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Следующие шаги

Разработчики r могут приступить к работе с некоторыми простыми примерами и ознакомиться с основами работы R с SQL Server. Следующий шаг см. по следующим ссылкам:

+ [Учебник. Запуск R в T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Учебник. Аналитика в базе данных для разработчиков R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Разработчики Python могут узнать, как использовать Python с SQL Server, следуя этим учебникам:

+ [Учебник. Запуск Python в T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Учебник. Аналитика в базе данных для разработчиков Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Примеры машинного обучения, основанные на реальных сценариях, см. в разделе [учебники](../tutorials/machine-learning-services-tutorials.md)по машинному обучению.