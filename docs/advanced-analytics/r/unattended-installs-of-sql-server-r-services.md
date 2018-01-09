---
title: "Автоматической установки службы обучения машины | Документы Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 801a29c07d55b9388d5be0edab33690399f2dde9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="unattended-installation-of-machine-learning-services-in-database"></a>Автоматически устанавливать службы обучения машины (в базе данных)

В этой статье описывается использование аргументы командной строки программы установки SQL Server для установки машинного обучения компонентов.

По автоматической установке мы означает, что вы не используйте интерактивные возможности мастера установки и вместо этого указать все аргументы, необходимые для завершения установки, включая лицензионные соглашения для SQL Server и для компонентов машины обучения на Командная строка или как часть скрипта, обычно в тихом режиме.

+ [SQL Server 2016 R Services](#bkmk_OldInstall)
+ [Машины SQL Server 2017 г., изучение служб](#bkmk_NewInstall) с R или Python
+ [Microsoft R Server или сервера Machine обучения](../r/install-microsoft-r-server-from-the-command-line.md)

**Применяется к: SQL Server 2017 г. службы машинного обучения (в базе данных), SQL Server 2016 R Services**

## <a name="prerequisites"></a>предварительные требования

+ На каждом экземпляре, где используется машинное обучение, необходимо установить компонент database engine.

+ Если компьютер не имеет доступа к Интернету, необходимо загрузить установщики для машинного обучения компоненты заранее. В разделе [Установка компонентов обучения компьютер без доступа к Интернету](../r/installing-ml-components-without-internet-access.md).

+ Существуют отдельные лицензирования параметров для каждого из компонентов открытым исходным кодом R и Python. SQL Server 2016 поддерживает только R; 2017 г. SQL Server поддерживает R и Python. Необходимо принять условия лицензионного соглашения для каждого языка, который вы устанавливаете. Не удается, если этот параметр не указан в командной строке.

+ Для завершения установки без необходимости отвечать на запросы, убедитесь, что вы определили все обязательные аргументы, включая те, для лицензирования и для других компонентов, которые можно установить.

+ **Mixed** режим безопасности, который поддерживает имена входа SQL была необходима в ранних выпусках. Несмотря на то, что больше не требуется, может потребоваться включение смешанного режима проверки подлинности для поддержки разработки решения по анализу данных, которые используют учетные данные SQL.

> [!IMPORTANT]
> 
> После завершения установки для включения функции требуются дополнительные шаги. Они включают изменения конфигурации и перезапуска экземпляра. Убедитесь, что для просмотра всех элементов в разделе [действий после установки] (#bkmk_PostInstall) для определения действий требуются после завершения установки.

## <a name="bkmk_NewInstall"></a>Установка из командной строки для SQL Server 2017 г.

Следующие примеры включают **минимальные** необходимые компоненты.

> [!IMPORTANT]
> Не забудьте выполнить все команды из командной строки с повышенными привилегиями.
> 
> После завершения установки требуются некоторые дополнительные шаги. В разделе [в этом разделе](#bkmk_PostInstall). 
> После завершения настройки потребуется другой перезапуск службы SQL Server.

### <a name="install-r-only"></a>Только установка R

В следующем примере показано, что аргументы, необходимые для выполнения автоматические, автоматической установки служб SQL Server 2017 г машины (в базе данных) с помощью языка r. добавлен.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
```

Обратите внимание, флаги, необходимые для R в SQL Server 2017 г.:

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MR`
+ `IACCEPTROPENLICENSETERMS`.

### <a name="install-python-only"></a>Только установка Python

В следующем примере показано, что аргументы, необходимые для выполнения автоматической автоматической установки служб SQL Server 2017 г машины (в базе данных) с помощью языка Python добавлен.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

Обратите внимание, флаги, необходимые для Python в SQL Server 2017 г.:

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MPY`
+ `IACCEPTPYTHONOPENLICENSETERMS`

### <a name="install-both-r-and-python-on-a-named-instance"></a>Установить в именованном экземпляре R и Python

В следующем примере показано, что аргументы, необходимые для выполнения автоматические, автоматической установки служб SQL Server 2017 г машины (в базе данных) на именованном экземпляре. Добавляются языков R и Python.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER.ServerName /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

## <a name="OldInstall"></a>Установка из командной строки для SQL Server 2016
 
В следующем примере показано, что аргументы, необходимые для выполнения автоматические, автоматической установки SQL Server 2016 с помощью языка r. добавлен.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL,ADVANCEDANALYTICS /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
```

Обратите внимание, флаги, необходимые для служб R 2016:

+ `ADVANCEDANALYTICS`
+ `IACCEPTROPENLICENSETERMS`

## <a name = "bkmk_PostInstall"></a>Дополнительные действия после установки

После завершения, независимо от того, какие версии программы установки SQL Server, необходимо выполнить следующие действия. функции обучения компьютера не включены по умолчанию и должно быть явно включено.

1.  После завершения установки откройте новый **запроса** окна в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], и выполните следующую команду, чтобы включить эту функцию.
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
    > [!NOTE]
    >  Необходимо явно включить компонент и reconfigure; в противном случае он будет невозможно для вызова внешних скриптов, даже если был установлен компонент.
  
2.  Перезапустите службу SQL Server для экземпляра изменена конфигурация. При этом будет автоматически перезапущена связанный [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] также службы.

> [!IMPORTANT]
> 
> Если имеется пользовательская конфигурация безопасности или если вы используете SQL Server в качестве контекста вычислений при выполнении кода R или Python с удаленного клиента, может потребоваться некоторые дополнительные действия. 
> 
> Дополнительные сведения см. в разделе [часто задаваемые вопросы по обновлению и установке](../../advanced-analytics/r/upgrade-and-installation-faq-sql-server-r-services.md).
