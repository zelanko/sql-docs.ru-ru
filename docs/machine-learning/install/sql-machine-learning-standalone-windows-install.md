---
title: Установка Machine Learning Server (изолированный)
description: Настройте изолированный сервер машинного обучения для Python и R. Изолированный сервер, устанавливаемый программой установки SQL Server, функционально эквивалентен версиям Microsoft Machine Learning Server без привязки к языку SQL.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 01/03/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016'
ms.openlocfilehash: d446416076160642f86c035082481d318479d594
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97471185"
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone-using-sql-server-setup"></a>Установите R Server или сервер машинного обучения (изолированный) с помощью программы установки SQL Server
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

::: moniker range=">=sql-server-2017"
Программа установки SQL Server поддерживает вариант установки автономного сервера машинного обучения **как общего компонента**, то есть за пределами SQL Server. Он называется **сервер машинного обучения (изолированный)** и включает Python и R. 
::: moniker-end
::: moniker range="=sql-server-2016"
Программа установки SQL Server поддерживает вариант установки автономного сервера машинного обучения **как общего компонента**, то есть за пределами SQL Server. В SQL Server 2016 эта функция называется **R Server (изолированный)** .  
::: moniker-end

Изолированный сервер, установленный программой установки SQL Server, функционально эквивалентен версиям [сервера машинного обучения](/machine-learning-server/what-is-machine-learning-server), не зависящим от языка SQL, и поддерживает те же сценарии и ситуации использования, в том числе:

+ Удаленное выполнение, переключение между локальными и удаленными сеансами в одной консоли
+ Эксплуатация с помощью веб-узлов и вычислений на узлах
+ Развертывание веб-службы: возможность упаковать скрипты R и Python в веб-службы
+ Полный набор библиотек функций R и Python

В качестве независимого сервера, отделенного от SQL Server, среда R и Python настраивается, защищена и доступна с помощью базовой операционной системы и средств, предоставляемых на отдельном сервере, не являющимся SQL Server.

Как дополнение SQL Server автономный сервер полезен, если необходимо разработать высокопроизводительные решения машинного обучения, которые могут использовать удаленные контексты вычислений на всех поддерживаемых платформах данных. Вы можете переместить выполнение с локального сервера на удаленный Machine Learning Server в кластере Spark или на другом экземпляре SQL Server.

<a name="bkmk_prereqs"> </a>

## <a name="pre-install-checklist"></a>Контрольный список перед установкой

Если вы установили предыдущую версию, например SQL Server 2016 R Server (изолированная версия) или Microsoft R Server, удалите существующую установку, прежде чем продолжить.

В качестве общего правила рекомендуется рассматривать установки изолированного сервера и ядра СУБД, поддерживающего экземпляры как взаимоисключающие, чтобы избежать конфликтов ресурсов, но если у вас достаточно ресурсов, нет запрета на установку этих экземпляров в тот же физический компьютер.

На компьютере может быть только один изолированный сервер: либо SQL Server Machine Learning Server (изолированный), либо SQL ServerR Server (изолированный). Перед добавлением новой версии обязательно удалите одну из них.

::: moniker range="=sql-server-2016"
<a name="bkmk_ga_instalpatch"></a> 

 ###  <a name="install-patch-requirement"></a>Требование для установки исправления 

Только для SQL Server 2016: Корпорация Майкрософт выявила проблему с определенной версией двоичных файлов среды выполнения Microsoft VC++ 2013, которые SQL Server устанавливает в качестве необходимого компонента. Если это обновление двоичных файлов среды выполнения VC не установлено, в SQL Server могут возникать проблемы с надежностью в определенных сценариях. Перед установкой SQL Server выполните инструкции, приведенные в [заметках о выпуске SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch), чтобы узнать, требуется ли на вашем компьютере исправление для двоичных файлов среды выполнения VC.  
::: moniker-end

## <a name="get-the-installation-media"></a>Получение установочного носителя

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

::: moniker range=">=sql-server-2017"
## <a name="run-setup"></a>Запуск программы установки

Для локальных установок необходимо запускать программу установки с правами администратора. При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из удаленной общей папки необходимо использовать учетную запись домена с разрешениями на чтение и выполнение для удаленной общей папки.

1. Запустите мастер установки.

2. Перейдите на вкладку **Установка** и выберите **Установка сервера машинного обучения (изолированного)** .
    
   ::: moniker-end
   ::: moniker range="=sql-server-2017"
   ![Установка изолированного сервера машинного обучения](media/2017setup-installation-page-mlsvr.png "Начните установку сервера машинного обучения (изолированного)")
   ::: moniker-end
   ::: moniker range="=sql-server-ver15"
   ![Установка изолированного сервера машинного обучения](media/2019setup-installation-page-mlsvr.png "Начните установку сервера машинного обучения (изолированного)")
   ::: moniker-end
   ::: moniker range=">=sql-server-2017"

3. После завершения проверки правил примите условия лицензионного соглашения SQL Server и выберите новую установку.

4. На странице **Выбор компонентов** уже должен быть выбран следующий параметр:

    - **Сервер машинного обучения Microsoft (изолированный)**

    - **R** и **Python** выбраны по умолчанию. Можно снять выделение с любого языка, но рекомендуется установить хотя бы один из поддерживаемых языков.

   ::: moniker-end
   ::: moniker range="=sql-server-2017"
   ![Выбор компонентов R или Python](media/2017setup-features-page-mlsvr-rpy.png "Начните установку сервера машинного обучения (изолированного)")
   ::: moniker-end
   ::: moniker range="=sql-server-ver15"
   ![Выбор компонентов R или Python](media/2019setup-features-page-mlsvr-rpy.png "Начните установку сервера машинного обучения (изолированного)")
   ::: moniker-end
   ::: moniker range=">=sql-server-2017"
    
   Все прочие параметры нужно игнорировать. 
    
   > [!NOTE]
   > Старайтесь не устанавливать **общие компоненты**, если на компьютере уже установлены Службы машинного обучения для аналитики SQL Server в базе данных. При этом создаются дубликаты библиотек.
   > 
   > Кроме того, в то время как сценарии R или Python, выполняемые в SQL Server, управляются SQL Server и поэтому не конфликтуют с памятью, используемой другими службами ядра СУБД, изолированный сервер машинного обучения не имеет таких ограничений и может конфликтовать с другими операциями базы данных. Наконец, удаленный доступ через сеанс RDP, который часто используется для операционной работы, обычно блокируется администраторами базы данных.
   > 
   > По этим причинам рекомендуется устанавливать сервер машинного обучения (изолированный) на отдельном компьютере из Служб машинного обучения SQL Server.

5. Примите условия лицензии, чтобы скачать и установить базовые дистрибутивы языков. Когда кнопка **Принять** станет недоступна, можно нажать кнопку **Далее**. 

6. На странице **Все готово для установки** проверьте выбранные параметры и нажмите кнопку **Установить**.
::: moniker-end

::: moniker range="=sql-server-2016"
## <a name="run-setup"></a>Запуск программы установки

Для локальных установок необходимо запускать программу установки с правами администратора. При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из удаленной общей папки необходимо использовать учетную запись домена с разрешениями на чтение и выполнение для удаленной общей папки.

1. Запустите мастер установки.

2. На вкладке **Установка** щелкните **New R Server (Standalone) installation** (Установка нового изолированного сервера R).
    
   ![Запустите установку изолированного R Server](media/2016-setup-installation-rsvr.png "Запустите установку изолированного R Server")

3. После завершения проверки правил примите условия лицензионного соглашения SQL Server и выберите новую установку.

4. На странице **Выбор компонентов** уже должен быть выбран следующий параметр:
    
   - **R Server (изолированный)**  
    
   ![Варианты выбора компонентов для изолированного сервера R Server](media/2016setup-rserver-features.png "Варианты выбора компонентов для изолированного сервера R Server")
    
   Все прочие параметры можно игнорировать. 
    
   > [!NOTE]
   > Старайтесь не устанавливать **общие компоненты** если вы запускаете установку на компьютере, где Службы R уже были установлены для аналитики SQL Server в базе данных. При этом создаются дубликаты библиотек.
   > 
   > Кроме того, в то время как сценарии R или Python, выполняемые в SQL Server, управляются SQL Server и поэтому не конфликтуют с памятью, используемой другими службами ядра СУБД, изолированный сервер R Server не имеет таких ограничений и может конфликтовать с другими операциями базы данных.
   > 
   > Обычно рекомендуется устанавливать сервер R Server (изолированный) на компьютере, отличном от того, где установлены Службы SQL Server R (в базе данных).

5. Примите условия лицензии, чтобы скачать и установить базовые дистрибутивы языков. Когда кнопка **Принять** станет недоступна, можно нажать кнопку **Далее**. 

6. На странице **Все готово для установки** проверьте выбранные параметры и нажмите кнопку **Установить**.
::: moniker-end

## <a name="set-environment-variables"></a>Настройка переменных среды

Только для интеграции с R присвойте переменной среды **MKL_CBWR** значение [ensure consistent output](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) из вычислений Intel Math Kernel Library (MKL).

1. На панели управления щелкните **Система и безопасность** > **Система** > **Расширенные параметры системы** > **Переменные среды**.

2. Создайте новую пользовательскую или системную переменную. 

  + Задайте имя переменной как `MKL_CBWR`.
  + Задайте значение переменной как `AUTO`.

3. Перезапустите сервер.

<a name="install-path"></a>

### <a name="default-installation-folders"></a>Папки установки по умолчанию

Для разработки на языке R и Python часто приходится иметь несколько версий на одном компьютере. При установке в рамках настройки SQL Server базовые дистрибутивы устанавливаются в папку, связанную с версией SQL Server, которую вы использовали для установки.

В следующей таблице перечислены пути для дистрибутивов R и Python, созданных установщиками Майкрософт. Для полноты таблица содержит пути, созданные программой установки SQL Server, а также автономный установщик для Сервера машинного обучения Microsoft.

|Версия| Метод установки | Папка по умолчанию|
|----|----|----|
|Сервер машинного обучения SQL Server 2019 (изолированный) |  Мастер установки SQL Server 2019 |`C:\Program Files\Microsoft SQL Server\150\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\150\PYTHON_SERVER`|
|Сервер машинного обучения SQL Server 2017 (изолированный) |  Мастер установки SQL Server 2017 |`C:\Program Files\Microsoft SQL Server\140\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Сервер машинного обучения Microsoft (изолированный) |  Автономный установщик Windows |`C:\Program Files\Microsoft\ML Server\R_SERVER`<br/>`C:\Program Files\Microsoft\ML Server\PYTHON_SERVER`|
|Службы машинного обучения SQL Server (в базе данных) |Мастер установки SQL Server 2019 с параметром языка R|`C:\Program Files\Microsoft SQL Server\MSSQL15.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL15.<instance_name>\PYTHON_SERVICES` |
|Службы машинного обучения SQL Server (в базе данных) |Мастер установки SQL Server 2017 с параметром языка R|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
|R Server (изолированный) в SQL Server 2016 |  Мастер установки SQL Server 2016 |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|Службы SQL Server 2016 R Services (в базе данных) |Мастер установки SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Применение обновлений

Мы рекомендуем применить последнее накопительное обновление к компонентам ядра СУБД и машинного обучения. Накопительные обновления устанавливаются с помощью программы установки. 

На устройствах, подключенных к Интернету, можно скачать самораспаковывающийся исполняемый файл. При применении обновления для ядра СУБД автоматически запрашиваются накопительные обновления для существующих функций R и Python. 

На отключенных серверах требуются дополнительные действия. Необходимо получить накопительный пакет обновления для ядра СУБД, а также CAB-файлы для функций машинного обучения. Все файлы должны быть переданы на изолированный сервер и применены вручную.

1. Начните с базового экземпляра. Накопительные обновления можно применять только к существующим установкам:

  + Сервер машинного обучения (изолированный) из начального выпуска SQL Server 2019
  + Сервер машинного обучения (изолированный) из начального выпуска SQL Server 2017
  + Сервер R Server (изолированный) из начального выпуска SQL Server 2016, SQL Server 2016 1 или SQL Server 2016 SP 2

2. Закройте все открытые сеансы R или Python и завершите все процессы, запущенные в системе.

3. Если вы включили возможность запуска в качестве веб-узлов и узлов вычислений для развертывания веб-служб, создайте резервную копию файла **AppSettings.json** в качестве меры предосторожности. Применение SQL Server 2017 CU13 или более поздней версии изменяет этот файл, поэтому для сохранения исходной версии может потребоваться резервная копия.

4. На компьютере с подключением к Интернету скачайте самый свежий накопительный пакет обновлений для используемой версии со страницы [Последние обновления для Microsoft SQL Server](../../database-engine/install-windows/latest-updates-for-microsoft-sql-server.md).

5. Загрузите последнее накопительное обновление. Это исполняемый файл.

6. На устройстве, подключенном к Интернету, дважды щелкните EXE-файл, чтобы запустить программу установки, и выполняйте шаги мастера, чтобы принять условия лицензионного соглашения, просмотреть затронутые функции и отслеживать ход выполнения до завершения.

7. На сервере без подключения к Интернету:

   + Получите соответствующие CAB-файлы для R и Python. Ссылки для загрузки см. в разделе [CAB-загрузки для накопительных обновлений в экземплярах SQL Server с аналитикой в базе данных](sql-ml-cab-downloads.md).

   + Перенесите все файлы, основные исполняемые и CAB-файлы в папку на автономном компьютере.

   + Дважды щелкните EXE-файл, чтобы запустить программу установки. При установке накопительного обновления на сервере без подключения к Интернету вам будет предложено выбрать расположение CAB-файлов для R и Python.

8. После установки войдите на сервер, для которого вы включили развертывание с веб-узлами и узлами вычислений, и отредактируйте файл **AppSettings.json**, добавив запись "MMLResourcePath" непосредственно под "MMLNativePath". Пример:

    ```json
    "ScorerParameters": {
        "MMLNativePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\",
        "MMLResourcePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\"
    }
    ```

9. [Запустите служебную программу CLI с правами администратора](/machine-learning-server/operationalize/configure-admin-cli-launch) для перезапуска веб-узлов и узлов вычислений. Инструкции и синтаксис см. в разделе [Отслеживание, запуск и остановка веб-узлов и узлов вычислений](/machine-learning-server/operationalize/configure-admin-cli-stop-start).

## <a name="development-tools"></a>Инструменты разработки

Интегрированная среда разработки не устанавливается программой установки. Дополнительные сведения о настройке среды разработки см. в статьях [Настройка средств R](../r/set-up-a-data-science-client.md) и [Настройка средств Python](../python/setup-python-client-tools-sql.md).

## <a name="next-steps"></a>Дальнейшие действия

Разработчики на языке R могут ознакомиться с простыми примерами, а также узнать, как код R работает с SQL Server. Дополнительные сведения см. в следующих статьях.

+ [Краткое руководство. Запуск R в T-SQL](../tutorials/quickstart-r-create-script.md)
+ [Руководство. Аналитические функции в базе данных для разработчиков R](../tutorials/r-taxi-classification-introduction.md)

::: moniker range=">=sql-server-2017"
Разработчики на языке Python могут узнать, как использовать Python с SQL Server, изучив следующие руководства.

+ [Учебник по Python. Прогнозирование проката лыж с помощью линейной регрессии в Службах машинного обучения SQL Server](../tutorials/python-ski-rental-linear-regression-deploy-model.md)
+ [Учебник по Python. Классификация клиентов на основе кластеризации методом k-средних с помощью служб машинного обучения SQL Server](../tutorials/python-clustering-model.md)
::: moniker-end