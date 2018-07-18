---
title: Командной строки для установки компонентов обучения машины SQL Server | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 814e0f8172e02d9b02be95888c8dab286429e533
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707962"
---
# <a name="install-sql-server-machine-learning-components-from-the-command-line"></a>Компоненты SQL Server машины обучения из командной строки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья содержит инструкции для машины SQL Server intalling обучения компонентов из командной строки:

+ [Новое в базе данных экземпляра](#indb)
+ [Добавить к существующему экземпляру ядра базы данных](#add-existing)
+ [Автоматическая установка](#silent)
+ [Новый изолированный сервер](#shared-feature)

Можно выбрать автоматическое, базовое или полное взаимодействие с пользовательским интерфейсом программы установки. В этой статье дополняет [Установка SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md), охватывающие параметры, уникальные для компонентов обучения машины R и Python.

## <a name="pre-install-checklist"></a>Контрольный список действий перед установкой

+ Выполнение команд из командной строки с повышенными привилегиями. 

+ Экземпляр ядра СУБД необходим для установки в базе данных. Не удается установить только функции R или Python, несмотря на то, что вы можете [постепенно добавить их к существующему экземпляру](#add-existing). Если требуется просто R и Python без ядра СУБД установить [изолированный сервер](#shared-feature).

+ Не устанавливайте на отказоустойчивом кластере. Механизм безопасности, используемый для изоляции процессов R и Python не совместим с среде отказоустойчивого кластера Windows Server.

+ Не устанавливайте на контроллере домена. Службы обучения машины часть установки завершится ошибкой.

+ Следует Избегайте установки автономных приложений и экземпляров в базе данных на том же компьютере. Изолированный сервер будут конкурировать за те же ресурсы, нарушая работу производительность обеих установок.


## <a name="command-line-arguments"></a>Аргументы командной строки

Аргумент функции является обязательным, как лицензионные соглашения термин. 

При установке из командной строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает полностью тихий режим (включается параметром /Q) и простой тихий режим (включается параметром /QS). При указании параметра /QS показывается только ход выполнения, не запрашивается ввод данных и не выводятся сообщения об обнаруженных ошибках. Параметр /QS поддерживается только в случае, когда указан режим /Action=install.

| Аргументы | Описание |
|-----------|-------------|
| / FEATURES = AdvancedAnalytics | Устанавливает версию в базе данных: обучения машины службы (в базе данных) для SQL Server 2017 г. или служб SQL Server 2016 R (в базе данных).  |
| / FEATURES = SQL_INST_MR | Применяется к только SQL Server 2017 г. Для сопоставления с AdvancedAnalytics. Устанавливает компонент (в базе данных) R, включая Microsoft R Open и собственные пакеты R. Компонент служб SQL Server 2016 R R только, поэтому нет параметра для этого выпуска.|
| / FEATURES = SQL_INST_MPY | Применяется к только SQL Server 2017 г. Для сопоставления с AdvancedAnalytics. Устанавливает компонент Python (в базе данных), включая Anaconda и собственные пакеты Python. |
| / FEATURES = SQL_SHARED_MR | Устанавливает функцию R для автономной версии: обучения машины 2017 г сервера SQL Server (автономный) или SQL Server 2016 R Server (автономный). Изолированный сервер функция «общий» не привязан к экземпляру ядра базы данных.|
| / FEATURES = SQL_SHARED_MPY | Применяется к только SQL Server 2017 г. Устанавливает функцию Python для автономной версии: обучения машины 2017 г сервера SQL Server (автономный). Изолированный сервер функция «общий» не привязан к экземпляру ядра базы данных.|
| /IACCEPTROPENLICENSETERMS  | Указывает, что вы приняли условия лицензионного соглашения по использованию компонентов R открытым исходным кодом. |
| / IACCEPTPYTHONLICENSETERMS | Указывает, что вы приняли условия лицензионного соглашения по использованию компонентов Python. |
| /IACCEPTSQLSERVERLICENSETERMS | Указывает, что вы приняли условия лицензии для использования SQL Server.|
| / MRCACHEDIRECTORY | Для автономной установки устанавливает папку, содержащую CAB-файлов компонентов R. |
| / MPYCACHEDIRECTORY | Для автономной установки устанавливает папку, содержащую CAB-файлов компонентов Python. |


## <a name="indb"></a> Установку экземпляра базы данных

Аналитика в базе данных доступны для экземпляров компонента database engine, необходимые для добавления **AdvancedAnalytics** компонент для установки. Можно установить экземпляр ядра СУБД с расширенной аналитики или [добавьте его к существующему экземпляру](#add-existing). 

На экране для просмотра сведений о ходе выполнения без интерактивный запрос, используйте аргумент/qs.

> [!IMPORTANT]
> После установки остаются две дополнительные действия по настройке. Интеграция не будет завершена до выполнения этих задач. В разделе [действия после установки](#post-install) инструкции.

### <a name="sql-server-2017-database-engine-advanced-analytics-with-python-and-r"></a>SQL Server 2017 г: СУБД, расширенной аналитики Python и R

Для параллельной установки экземпляра компонента database engine укажите имя экземпляра и имя входа администратора (Windows). Включить функции для установки основных компонентов и языковых компонентов, а также все условиями лицензирования.

```  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

Этот же команды, но с имени входа SQL Server для ядра базы данных с помощью смешанный проверки подлинности.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<sql-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

Данный пример является Python, отображение, можно добавить один язык, опустив компонент.

```  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTPYTHONLICENSETERMS
```

### <a name="sql-server-2016-database-engine-and-advanced-analytics-with-r"></a>SQL Server 2016: компонент database engine и расширенной аналитики с помощью R

Эта команда идентична 2017 г. SQL Server, но без элементов, Python, которые недоступны в программе установки SQL Server 2016.

```  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS 
```

## <a name="post-install"></a> После установки конфигурации (обязательно)

Применяется для установки только в базе данных.

По завершении установки имеется экземпляр ядра СУБД с пакетов R и Python, Microsoft R и Python, Microsoft R Open, Anaconda, средства, образцы и скрипты, которые входят в состав распределения. 

Для завершения установки необходимо выполнить две дополнительные задачи.

1. Перезапустите службы компонента database engine.

1. Включите внешние скрипты, прежде чем использовать функцию. Следуйте инструкциям в [установки служб SQL Server 2017 г машины обучения (в базе данных)](sql-machine-learning-services-windows-install.md) следующим шагом. 

Для SQL Server 2016 в этой статье вместо этого используйте [установки служб SQL Server 2016 R (в базе данных)](sql-r-services-windows-install.md).

## <a name="add-existing"></a> Добавление дополнительных возможностей анализа к существующему экземпляру ядра базы данных

При добавлении дополнительных возможностей анализа в базе данных в существующий экземпляр ядра базы данных, введите имя экземпляра. Например если вы ранее установили 2017 г. SQL Server database engine и Python, можно использовать эту команду для добавления R.

```  
Setup.exe /qs /ACTION=Install /FEATURES=SQL_INST_MR /INSTANCENAME=MSSQLSERVER 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTROPENLICENSETERMS
```



## <a name="silent"></a> Автоматическая установка

Автоматическая установка запрещает проверку для расположения файлов .cab. По этой причине необходимо указать расположение, куда должны быть распакованы CAB-файлов. Для этого можно использовать во временный каталог.
 
```  
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS 
/MRCACHEDIRECTORY=%temp% /MPYCACHEDIRECTORY=%temp%
```

## <a name="shared-feature"></a> Установок отдельного сервера

Изолированный сервер функция «общий» не привязан к экземпляру ядра базы данных. В следующих примерах допустимый синтаксис для обеих версий.

2017 г. SQL Server поддерживает Python и R на изолированном сервере:

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR,SQL_SHARED_MPY  
/IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

SQL Server 2016 — только для R:

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR 
/IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

По завершении установки имеется сервер, пакеты Microsoft, для распределения открытым исходным кодом R и Python, средства, примеры и сценарии, которые входят в состав распределения. 

Чтобы открыть окно консоли R \R_SERVER\bin\x64 go \Program files\Microsoft SQL Server\140 (или 130) и дважды щелкните **RGui.exe**. Не знакомы с R? Повторите этот учебник: [R основные команды и функции RevoScaleR: 25 наиболее распространенные](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler).

Чтобы открыть команды Python, перейдите в \Program files\Microsoft SQL Server\140\PYTHON_SERVER\bin\x64 и дважды **python.exe**.

## <a name="get-help"></a>Получить справку

Нужна помощь с установку или обновление? Ответы на часто задаваемые вопросы и известные проблемы см. в следующей статье:

* [Обновление и установка часто задаваемые вопросы — Machine Services обучения](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Чтобы проверить состояние установки экземпляра и устранить распространенные проблемы, попробуйте следующие пользовательские отчеты.

* [Пользовательские отчеты для служб SQL Server R](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Следующие шаги

Разработчики R можно начать работу с несколько простых примеров и основные сведения о работе с SQL Server R. Следующий шаг см. по следующим ссылкам:

+ [Учебник: Запускать в T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Учебник: Анализ в базе данных для разработчиков R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Разработчиков Python можно освоить использование Python с SQL Server, выполнив следующие учебники:

+ [Учебник: Запустите Python в T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Учебник: Анализ в базе данных для разработчиков Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Чтобы просмотреть примеры машинного обучения, основанные на реальных сценариев, в разделе [машинного обучения учебники](../tutorials/machine-learning-services-tutorials.md).