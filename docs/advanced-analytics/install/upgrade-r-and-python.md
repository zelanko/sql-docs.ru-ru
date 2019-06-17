---
title: Обновление компонентов R и Python — службы машинного обучения SQL Server
description: Обновите R и Python в SQL Server 2016 служб или служб SQL Server 2017 машинного обучения с с помощью sqlbindr.exe для привязки к Machine Learning Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 93384c8152109b01720ae7e861731638316d4966
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141433"
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>Обновление компонентов машинного обучения (R и Python) в экземплярах SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Интеграция R и Python в SQL Server содержит пакеты с открытым исходным кодом и корпорации Майкрософт. В разделе Стандартная обслуживания SQL Server, пакеты обновляются в соответствии со цикла выпуска SQL Server, с помощью исправления для существующих пакетов в текущей версии, но без обновления основного номера версии. 

Тем не менее многие специалисты по анализу данных привыкли работать с более новые пакеты, как только они станут доступны. Для служб SQL Server 2017 машинного обучения (в базе данных) и SQL Server 2016 R Services (в базе данных), вы можете получить [более новых версиях R и Python](#version-map) по *привязки* для **Microsoft Сервер машинного обучения**. 

## <a name="what-is-binding"></a>Что такое привязывание?

Привязки — это процесс установки, которое меняет местами содержимое папок R_SERVICES и PYTHON_SERVICES с новой исполняемые файлы, библиотеки и средства из [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index).

Вместе с обновленные компоненты поставляется коммутатора в модели обслуживания. Вместо [жизненного цикла продукта SQL Server](https://support.microsoft.com/lifecycle/search?alpha=SQL%20Server%202017), с помощью [накопительные пакеты обновления SQL Server](https://support.microsoft.com/help/4047329/sql-server-2017-build-versions), обновления службы теперь соответствуют [сроки предоставления поддержки для Microsoft R Server & компьютере Learning Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support) на [современного жизненного цикла](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

За исключением версии компонентов и обновления службы привязки не приводит к изменению основные принципы установки: Интеграция R и Python по-прежнему является частью экземпляр ядра СУБД, лицензирования, не изменяется (не дополнительные затраты, связанные с привязкой), а также политики поддержки SQL Server по-прежнему содержат для компонента database engine. В оставшейся части этой статьи объясняется механизм привязки и принципах ее работы для каждой версии SQL Server.

> [!NOTE]
> Привязка применяется к экземплярам (в базе данных), которые привязаны к экземплярам SQL Server. Привязка не относится к установке (изолированная версия).

**Рекомендации по SQL Server 2017 привязки**

Для SQL Server 2017 служб машинного обучения привязки считает только в том случае, когда начинается сервер машинного обучения Майкрософт предлагает дополнительные пакеты или более новых версий над теми, которые уже есть.

**Рекомендации по SQL Server 2016 привязки**

Для клиентов, SQL Server 2016 R Services, привязка предоставляет обновленные пакеты R, новые пакеты не является частью исходной установки ([MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)), и [обученная моделей](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models), каждый из которых может быть дополнительно в каждый новый основной и дополнительный выпуск обновить [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index). Привязки не предоставляет поддержку Python, который является компонентом SQL Server 2017. 

<a name="version-map"></a>

## <a name="version-map"></a>Сопоставление версий

В следующей таблице приведен версии карта, версии пакетов через транспортных средств выпуска, чтобы потенциальные пути обновления можно получить при привязке к Microsoft Machine Learning Server (ранее известный как R Server, перед добавлением поддержки Python начиная в MLS 9.2.1). 

Обратите внимание на то, что привязка не гарантирует очень последнюю версию R, Anaconda. При привязке к Microsoft Machine Learning Server (MLS), вы получите версии R или Python, устанавливаются с помощью программы установки, который не является последней версии, доступной в Интернете.

[**SQL Server 2016 R Services**](../install/sql-r-services-windows-install.md)

Компонент |Первоначальный выпуск | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [MLS 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [MLS 9.3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) через R | R 3.2.2     | R 3.3.2   |3\.3.3 R   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[предварительно обученных моделей](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| n.a. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| n.a. | 1.0 |  1.0 |  1.0 |  1.0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a. | 1.0 |  1.0 |  1.0 |  1.0 |


[**SQL Server 2017 службы машинного обучения**](../install/sql-machine-learning-services-windows-install.md)

Компонент |Первоначальный выпуск | MLS 9.3 | | | |
----------|----------------|---------|-|-|-|-|
Microsoft R Open (MRO) через R | 3\.3.3 R | R 3.4.3 | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9.2 |  9.3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1.0 |  1.0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1.0 |  1.0 | | | |
Anaconda 4.2 по Python 3.5  | 4.2/3.5.2 | 4.2/3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2  | 9.3| | | |
 [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[предварительно обученных моделей](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9.2 | 9.3| | | |

## <a name="how-component-upgrade-works"></a>Как работает обновление компонента 

R и Python библиотек и исполняемых файлов будут обновлены при привязке к Machine Learning Server существующую установку R и Python. Выполняется привязка [установщика Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) при запуске программы установки на существующий экземпляр SQL Server database engine, 2016 или 2017, наличие интеграции R или Python. Программа установки обнаруживает существующие функции и предложит выполнить повторную привязку к Machine Learning Server. 

Во время привязки, содержимое C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES и \PYTHON_SERVICES перезаписывается новые исполняемые файлы и библиотеки C:\Program Files\Microsoft\ML Server\R_SERVER и \PYTHON_SERVER.

В то же время модель обслуживания также зеркально из механизмов обновления SQL Server, более частые цикла выпуска основной и дополнительный сервер машинного обучения Майкрософт. Переключение политики поддержки является привлекательным вариантом для групп обработки и анализа данных, которым требуется новое поколение R и модули Python для своих решений. 

+ Без привязки, пакетов R и Python установлены исправления для исправления ошибок, при установке пакета обновления SQL Server или накопительный пакет обновления (CU). 
+ С помощью привязки, более новые версии пакетов могут применяться к экземпляру, независимо от расписания накопительное обновление выпуска, в разделе [политика современного жизненного цикла](https://support.microsoft.com/help/30881/modern-lifecycle-policy) и версиях сервера машинного обучения Майкрософт. Политика современного жизненного цикла поддержки предлагает более частые обновления поверх существования короче, один год. После привязки, будет продолжать использовать установщик MLS для будущих обновлений R и Python, как только они станут доступны на сайтах загрузки корпорации Microsoft.

Привязка применяется только для функций R и Python. А именно пакеты с открытым исходным кодом для функций R и Python (Microsoft R Open, Anaconda) и частные пакеты RevoScaleR, revoscalepy и т. д. Привязка не изменяет модель поддержки для экземпляра компонента database engine и не меняется версия SQL Server.

Привязка является необратимой. Вы можете вернуться к SQL Server, обслуживание с помощью [отмене привязки экземпляра](#bkmk_Unbind) и reparing ваш экземпляр ядра СУБД SQL Server.

Суммирование, для привязки порядок действий таков:

+ Начните с существующего, настроенного установленную версию SQL Server 2016 R Services (или служб машинного обучения SQL Server 2017).
+ Определите, какая версия Microsoft Machine Learning Server обновленные компоненты, которые вы хотите использовать.
+ Скачайте и запустите программу установки для этой версии. Программа установки обнаружит существующий экземпляр, добавлен параметр привязки и возвращает список совместимых экземпляров.
+ Выберите экземпляр, который вы хотите привязать и завершите работу программы установки для выполнения привязки.

С точки зрения взаимодействия с пользователем технологии и работы с ним не изменяется. Единственным различием является наличие более новые версии пакетов и возможно, дополнительных пакетов, изначально доступна через SQL Server (например, MicrosoftML для клиентов SQL Server 2016 R Services).

## <a name="bkmk_BindWizard"></a>Привязка к MLS, с помощью программы установки

Установка Microsoft Machine Learning обнаруживает существующие функции и версии SQL Server и вызывает служебная программа SqlBindR.exe изменение привязки. На внутреннем уровне SqlBindR связанных с настройкой использоваться и косвенно. Позже можно вызвать SqlBindR непосредственно из командной строки для выполнения определенных параметров.

1. В SSMS выполните `SELECT @@version` для проверки сервера сборки минимальным требованиям. 

   Для SQL Server 2016 R Services, минимальное значение — [с пакетом обновления 1](https://www.microsoft.com/download/details.aspx?id=54276) и [CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1).

1. Проверка версии R базовый и пакетов RevoScaleR, чтобы убедиться, что ниже, чем вы планируете заменить их с существующими версиями. Для SQL Server 2016 R Services пакет R Base — 3.2.2 и RevoScaleR является 8.0.3.

    ```sql
    EXECUTE sp_execute_external_script
    @language=N'R'
    ,@script = N'str(OutputDataSet);
    packagematrix <- installed.packages();
    Name <- packagematrix[,1];
    Version <- packagematrix[,3];
    OutputDataSet <- data.frame(Name, Version);'
    , @input_data_1 = N''
    WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
    ```

1. Закройте SSMS и любые другие средства, наличие открытое соединение с SQL Server. Привязка перезаписывает файлы программы. Если SQL Server содержит открытые сеансы, привязка завершится ошибкой с кодом ошибки привязки 6.

1. Скачайте Microsoft Machine Learning Server на компьютер, который имеет экземпляр, который требуется обновить. Мы рекомендуем [последней версии](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer).

1. Распакуйте папку и запустить ServerSetup.exe, расположенный в MLSWIN93.

   ![Мастер установки сервера машинного обучения Майкрософт](media/mls-921-installer-start.PNG)

1. На **настройте установку**проверьте компоненты для обновления и просмотрите список совместимых экземпляров. 

   Этот шаг очень важен.

   В левой части выберите все возможности, которые вы хотите сохранить или обновить. Не удается обновить некоторые компоненты и нельзя использовать с другими. Пустой флажок удаляет эти компоненты, при условии, что он уже установлен. На снимке экрана, заданный экземпляр SQL Server 2016 R Services (MSSQL13) выбраны R и R версии предварительно обученных моделей. Эта конфигурация является допустимым, поскольку SQL Server 2016 поддерживает R, но не Python.

   Если вы выполняете обновление компонентов SQL Server 2016 R Services, не выбирайте компонент Python. Невозможно добавить Python в SQL Server 2016 R Services.

   В правой части установите флажок рядом с именем экземпляра. Если в списке нет экземпляров, у вас есть несовместимым сочетанием. Если экземпляр не выбран, создается новый автономной установки сервера машинного обучения и библиотек SQL Server ничем не отличаются. Если не удается выбрать экземпляр, он может оказаться в [SP1 CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1). 

    ![Настройка шага установки](media/mls-931-installer-mssql13.png)

1. На **лицензионное соглашение** выберите **я принимаю эти условия** принять условия лицензирования для сервера машинного обучения. 

1. На последующих страницах предоставить согласие для дополнительных условий лицензирования для любой компонентов с открытым кодом, который вы выбрали, например Microsoft R Open или дистрибутив Python Anaconda.

1. На **почти Готово** странице, запомните или запишите в папку установки. Папка по умолчанию — \Program Files\Microsoft\ML сервера.

    Если вы хотите изменить папку установки, нажмите кнопку **Дополнительно** для возврата к первой странице мастера. Тем не менее необходимо повторить все выбранные ранее параметры.

Во время установки заменяются все библиотеки R или Python, используемый сервером SQL Server и панель запуска обновляется для использования новых компонентов. Таким образом Если экземпляр уже использовали библиотеки R_SERVICES папку по умолчанию, после обновления этих библиотек, удаляются и изменяются свойства для службы панели запуска, чтобы использовать библиотеки в новом расположении.

Привязка влияет на содержимое этих папок: C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library заменяется содержимым C:\Program Files\Microsoft\ML Server\R_SERVER. Вторая папка и ее содержимое, создаваемые Установка Microsoft Machine Learning Server. 

Если обновление завершилось ошибкой, проверьте [коды ошибок SqlBindR](#sqlbindr-error-codes) Дополнительные сведения.

## <a name="confirm-binding"></a>Подтвердите привязку

Повторная проверка версии R и RevoScaleR, чтобы убедиться, что у вас есть более новых версий. Чтобы получить сведения о пакете с помощью консоли R, в состав пакетов R в экземпляре ядра базы данных:

```sql
EXECUTE sp_execute_external_script
@language=N'R'
,@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
Name <- packagematrix[,1];
Version <- packagematrix[,3];
OutputDataSet <- data.frame(Name, Version);'
, @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Для SQL Server 2016 R Services привязан к Machine Learning Server 9.3 R Base пакету, должен быть 3.4.3 и RevoScaleR должно быть 9.3 вы также должны MicrosoftML 9.3. 

Если вы добавили предварительно обученных моделей, внедренных моделей в библиотеке MicrosoftML и их можно вызывать с помощью функции MicrosoftML. Дополнительные сведения см. в разделе [R Примеры для MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml).

## <a name="offline-binding-no-internet-access"></a>Привязка (нет доступа к Интернету)

Для систем без подключения к Интернету можно загрузить установщик и CAB-файлы на компьютер, подключенный к Интернету и затем передачи файлов на изолированном сервере. 

Установщик (ServerSetup.exe) включает в себя пакеты Microsoft (RevoScaleR, MicrosoftML, olapR, sqlRUtils). CAB-файлы предоставляют другие основные компоненты. Например «SRO» cab предоставляет R Open, распространяемого корпорацией Майкрософт открытым исходным кодом R.

Ниже описано, как разместить файлы для автономной установки.

1. Скачайте установщик MLS. Он загружает в виде одного ZIP-файла. Мы рекомендуем [последней версии](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer), но вы также можете установить [более ранних версий](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components).

1. Загрузите CAB-файлы. Ниже приведены ссылки для версии 9.3. Если требуется более ранних версий, можно найти дополнительные ссылки в [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components). Помните, что Python и Anaconda могут добавляться только к экземпляру службы машинного обучения SQL Server 2017. Существует предварительно обученных моделей R и Python; CAB-файл предоставляет модели в языки, которые вы используете.

    | Компонент | Загрузить |
    |---------|----------|
    | Чтение       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | Предварительно обученная модель | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. Передача ZIP-файл и CAB-файлы на целевой сервер.

1. На сервере, введите `%temp%` в команду запуска, чтобы получить физическое расположение временного каталога. Физический путь зависит от компьютера, но обычно `C:\Users\<your-user-name>\AppData\Local\Temp`.

1. Поместите CAB-файлы в папке % temp %.

1. Распакуйте установщик.

1. Запустите ServerSetup.exe и следуйте инструкциям на экране для завершения установки.

## <a name="bkmk_BindCmd"></a>Операций из командной строки

После запуска Microsoft Machine Learning Server командной строки служебная программа SqlBindR.exe становится доступным, можно использовать для дальнейшей операций привязки. Например если вы решите отменить привязку, можно либо повторно запустите программу установки или программы командной строки. Кроме того это средство можно использовать для проверки для экземпляра, совместимости и доступности.

> [!TIP]
> Не удается найти SqlBindR? Возможно, вы не выполнения программы установки. SqlBindR доступна только после запуска программы установки Server машины обучения.

1. Откройте командную строку от имени администратора и перейдите в папку, содержащую sqlbindr.exe. Расположение по умолчанию — C:\Program Files\Microsoft\MLServer\Setup

2. Выполните следующую команду, чтобы просмотреть список доступных экземпляров: `SqlBindR.exe /list`.
  
   Запишите полное имя экземпляра. Например имя экземпляра может быть MSSQL14. MSSQLSERVER для экземпляра по умолчанию, или что-нибудь вроде SERVERNAME. МОЙИМЕНОВАННЫЙЭКЗЕМПЛЯР.

3. Запустите **SqlBindR.exe** с */bind* аргумента и укажите имя экземпляра для обновления, используя имя экземпляра, который был возвращен в предыдущем шаге.

   Например чтобы обновить экземпляр по умолчанию, введите следующую команду:  `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. После завершения обновления перезапустите службу панели запуска, связанную с любой экземпляр, который был изменен.

## <a name="bkmk_Unbind"></a>Отменить или отменить привязку экземпляра

Вы можете восстановить привязанный экземпляр для первоначальной установки компонентов R и Python, программой установки SQL Server. Существует три части возвращение обратно к обслуживания SQL Server.

+ [Шаг 1. Отменить привязку к Microsoft Machine Learning Server](#step-1-unbind)
+ [Шаг 2. Восстановление в исходное состояние экземпляра](#step-2-restore)
+ [Шаг 3. Переустановите все пакеты, которые добавляются к установке](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Шаг 1. Отменить привязку

У вас есть два параметры для отката привязки: повторно запустите программу установки, или воспользуйтесь служебной программой командной строки SqlBindR.

#### <a name="bkmk_wizunbind"></a> Отменить привязку с помощью программы установки

1. Найдите установщик для сервера машинного обучения. Если вы удалили установщик, может потребоваться загрузить его снова, или скопируйте его с другого компьютера.
2. Не забудьте запустить установщик на компьютере с экземпляром, который вы хотите отменить привязку.
2. Установщик определяет локальные экземпляры, которые являются кандидатами для отмены привязки.
3. Снимите флажок рядом с экземпляр, который вы хотите вернуться к исходной конфигурации.
4. Примите лицензионное соглашение. Необходимо указать свое согласие с условиями лицензионного соглашения даже при установке.
5. Нажмите кнопку **Готово**. Этот процесс занимает некоторое время.

#### <a name="bkmk_cmdunbind"></a> Отменить привязку с помощью командной строки

1. Откройте командную строку и перейдите в папку, содержащую **sqlbindr.exe**, как описано в предыдущем разделе.

2. Выполните команду **SqlBindR.exe** с аргументом */unbind* и укажите экземпляр.

   Например следующая команда восстанавливает экземпляр по умолчанию:
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Шаг 2. Выполните исправление экземпляра SQL Server

Запустите программу установки SQL Server для восстановления экземпляра компонента database engine наличие таких функций R и Python. Обновления будут сохранены, а если вы пропустили все обновления для пакетов R и Python для обслуживания SQL Server, этот шаг применяется те исправления.

Кроме того это больше работы, но может также полностью удалить и переустановить экземпляра компонента database engine, а затем применить все обновления службы.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Шаг 3. Добавить все сторонние пакеты

Возможно, вы добавили другие пакеты с открытым исходным кодом или сторонние в библиотеку пакета. Так как отмена привязки переключается расположение библиотеки пакета по умолчанию, необходимо переустановить пакеты в библиотеку, теперь используют R и Python. Дополнительные сведения см. в разделе [по умолчанию пакеты](../package-management/default-packages.md), [Установка новых пакетов R](../r/install-additional-r-packages-on-sql-server.md), и [Установка новых пакетов Python](../python/install-additional-python-packages-on-sql-server.md).

## <a name="sqlbindrexe-command-syntax"></a>Синтаксис команды SqlBindR.exe

### <a name="usage"></a>Использование

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Параметры

|Имя|Описание|
|------|------|
|*list*| Выводит список идентификаторов всех экземпляров баз данных SQL на текущем компьютере.|
|*bind*| Обновляет указанный экземпляр базы данных SQL до последней версии R Server и обеспечивает автоматическое получение экземпляром будущих обновлений для R Server.|
|*unbind*|Удаляет последнюю версию R Server из указанного экземпляра базы данных SQL и блокирует применение будущих обновлений R Server к экземпляру.|

<a name="sqlbindr-error-codes"><a/>

## <a name="binding-errors"></a>Ошибок привязки

MLS установщика, так и с помощью SqlBindR возвращают следующие коды ошибок и сообщений.

|Код ошибки  | `Message`           | Сведения               |
|------------|-------------------|-----------------------|
|Привязка — ошибка 0 | ОК (успешное завершение) | Привязка передан без ошибок. |
|Привязка — ошибка 1 | Недопустимые аргументы | Синтаксическая ошибка. |
|Привязка — ошибка 2 | Недопустимое действие | Синтаксическая ошибка. |
|Привязка — ошибка 3 | Недопустимый экземпляр | Экземпляр существует, но не является допустимым для привязки. |
|Привязка — ошибка 4 | Не привязки | |
|Привязка — ошибка 5 | Уже привязан | Вы выполнили команду *bind* , но указанный экземпляр уже привязан. |
|Привязка — ошибка 6 | Произошел сбой привязки | При отмене привязки экземпляра произошла ошибка. Эта ошибка может возникать при запуске установщика MLS не выбирая какие-либо функции. Привязки необходимо, выберите экземпляр MSSQL и R и Python, при условии, что экземпляр SQL Server 2017. Эта ошибка также возникает, если SqlBindR не удалось выполнить запись в папку Program Files. Эта ошибка возникает вызовет открытых сеансов или дескриптора SQL Server. Если вы получаете эту ошибку, перезагрузите компьютер и повторить действия привязки перед началом любых новых сеансов.|
|Привязка — ошибка 7 | Не привязан | Экземпляр ядра СУБД имеет служб R или службы машинного обучения SQL Server. Экземпляр не привязан к Microsoft Machine Learning Server. |
|Привязка — ошибка 8 | Отмена привязки не удалось | При отмене привязки экземпляра произошла ошибка. |
|Привязка — ошибка 9 | Экземпляры не найдены. | Нет экземпляров компонента database engine не найдены на этом компьютере. |

## <a name="known-issues"></a>Известные проблемы

В этом разделе перечислены известные проблемы, характерные для использования служебной программы SqlBindR.exe или к обновлению версии сервера машинного обучения, которые могут повлиять на экземплярах SQL Server.

### <a name="restoring-packages-that-were-previously-installed"></a>Восстановление пакетов, которые были установлены

После обновления до Microsoft R Server 9.0.1, версия SqlBindR.exe для этой версии не удалось восстановить исходные пакеты или компоненты R полностью, использования пользователь восстановления SQL Server на экземпляре, примените все выпуски служб, а затем перезапустите экземпляр.

Более позднюю версию SqlBindR автоматически восстановить исходные признаки R, устраняя необходимость в повторной установки компонентов R или повторно обновлять сервер. Тем не менее необходимо установить все обновления пакета R, которые могли быть добавлены после первоначальной установки.

При использовании роли пакетов управления для установки и совместное использование пакета, эту задачу гораздо проще: команды R можно использовать для синхронизации установленные пакеты в файловую систему, с помощью записей в базе данных и наоборот. Дополнительные сведения см. в разделе [управление пакетами R для SQL Server](../r/install-additional-r-packages-on-sql-server.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Проблемы с несколько обновлений из SQL Server

Если экземпляр SQL Server 2016 R Services ранее был обновлен до версии 9.0.1, при запуске нового установщика для Microsoft R Server 9.1.0, он отображает список всех допустимых экземпляров, а затем по умолчанию выбирает ранее привязанного экземпляров. Если вы продолжите, ранее привязанного экземпляров свободной. Как следствие, более ранней версии 9.0.1 удаляется установки, включая все связанные пакеты, но не устанавливается новая версия Microsoft R Server (9.1.0).

Чтобы избежать этого можно изменить существующую установку R Server следующим образом:
1. В панели управления откройте **Установка и удаление программ**.
2. Найдите Microsoft R Server и нажмите кнопку **изменение**.
3. При запуске установщика выберите экземпляры, которые вы хотите выполнить привязку к 9.1.0.

Microsoft Machine Learning Server 9.2.1 или 9.3, но нет этой проблемы.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>Привязки или отмены привязки оставляет несколько временные папки

Иногда привязка и Отмена привязки операции не удалось очистить временные папки.
Если вы нашли папки с именем следующим образом, можно удалить после завершения установки: R_SERVICES_<guid>

> [!NOTE]
> Необходимо дождаться завершения установки. Может занять много времени для удаления библиотеки R, связанные с одной версии, а затем добавьте новые библиотеки R. По завершении операции удаляются временные папки.

## <a name="see-also"></a>См. также

+ [Установите Machine Learning Server для Windows (подключения к Интернету)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Установите Machine Learning Server для Windows (автономный)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Известные проблемы в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Функция объявлений из предыдущего выпуска сервера R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Не рекомендуется, снятых с производства и измененные компоненты](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
