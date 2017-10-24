---
title: "Автоматически устанавливать службы обучения машины Python (в базе данных) | Документы Microsoft"
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b9156a3dc9dec21187eec8dc0b5a44059fb5e31
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="unattended-installation-of-python-machine-learning-services-in-database"></a>Автоматически устанавливать службы обучения машины Python (в базе данных)

В этом разделе описывается использование аргументы командной строки в программе установки SQL Server 2017 г. Установка SQL Server database engine с использованием службы обучения машины и Python, в автоматическом режиме.

> [!NOTE]
> Не забудьте указать аргументы командной строки для соглашений о лицензировании, один для Python и один для SQL Server.

## <a name="prerequisites"></a>Предварительные требования

Прежде чем запустить процесс установки, выполните следующие требования:

+ Независимо от 2017 г. SQL Server database engine не может быть установлена служба Python. Необходимо включить компонент ядра базы данных SQL.
+ При выполнении автономной установки, необходимо заранее загрузить необходимые компоненты Python и скопируйте их в локальную папку. Расположения загрузки. в разделе [Установка компонентов обучения компьютер без доступа к Интернету](../../advanced-analytics/r-services/installing-ml-components-without-internet-access.md).
+ Новый параметр */IACCEPTPYTHONLICENSETERMS*, которое указывает, что вы приняли условия лицензионного соглашения по использованию компонентов Python, предоставляемые компания Continuum Analytics. Если этот параметр не включен в командную строку, установка завершится сбоем.
+ Для завершения установки без необходимости отвечать на запросы, убедитесь, что вы определили все обязательные аргументы, включая те, для Python и лицензирования SQL Server, а также для других компонентов, которые можно установить.
+  В некоторых предварительных версиях SQL Server 2016 требовалось смешанный режим проверки подлинности. Он больше не требуется, хотя может быть полезно в сценариях, где специалисты по анализу данных разработки и тестирования решения удаленно с помощью имен входа SQL Server.

## <a name="perform-an-unattended-installation-of-python-machine-learning-services-in-database"></a>Выполнение автоматической установки Python машины обучения служб (в базе данных)

В следующем примере показан **минимальные** необходимые компоненты для указания в командной строке при выполнении автоматическую установку Python и компонент database engine на экземпляре по умолчанию.

> [!NOTE]
> Этот компонент требует 2017 г. SQL Server. Python не поддерживается в более ранних версиях SQL Server.

1. Откройте командную строку с повышенными привилегиями и выполните следующую команду:

    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONLICENSETERMS
    ```

    > [!NOTE]
    > 
    > Нет новых опции установки для Python: `SQL_INST_MPY` и`IACCEPTPYTHONLICENSETERMS`

2. Перезапустите сервер, как указано.
3. Выполните действия по настройке после установки, как описано в [в этом разделе](#bkmk_PostInstall). Потребуется другой перезапуск службы SQL Server.

## <a name = "bkmk_PostInstall"></a>Действия после установки

1.  После завершения установки откройте новый **запроса** окна в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], и выполните следующую команду, чтобы включить эту функцию.

    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
    > [!NOTE]
    >  Необходимо явно включить компонент и reconfigure; в противном случае он будет невозможно для вызова внешних скриптов, даже если был установлен компонент.
  
3.  Перезапустите службу SQL Server для экземпляра изменена конфигурация. При этом будет автоматически перезапущена связанный [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] также службы.

3. Если вы используете пользовательскую конфигурацию безопасности или планируете использовать SQL Server для поддержки удаленных контекстов вычислений, могут потребоваться дополнительные действия. Дополнительные сведения см. в разделе [Устранение неполадок при установке обучения машины](../machine-learning-troubleshooting-faq.md).

