---
title: Обновление компонентов R и Python
description: Обновите R и Python в Службах машинного обучения SQL Server или SQL Server R Services с помощью sqlbindr.exe для привязки к Machine Learning Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: abc14f78a969abd4adbbb2dcf12b4ee316614d23
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69634551"
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>Обновление компонентов машинного обучения (R и Python) в экземплярах SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Интеграция R и Python в SQL Server включает в себя пакеты с открытым кодом и собственные пакеты Майкрософт. В рамках стандартного обслуживания SQL Server пакеты обновляются в соответствии с циклом выпуска SQL Server с исправлениями ошибок в существующих пакетах в текущей версии, но без обновления основных версий. 

Однако многие специалисты по обработке и анализу данных привыкли работать с новыми пакетами по мере их появления. Для Служб машинного обучения SQL Server (в базе данных) и SQL Server R Services (в базе данных) можно получать [более новые версии R и Python](#version-map), *выполнив привязку* к **Microsoft Machine Learning Server**. 

## <a name="what-is-binding"></a>Что такое привязка?

Привязка — это процесс установки, который меняет содержимое папок R_SERVICES и PYTHON_SERVICES на более новые исполняемые файлы, библиотеки и инструменты с [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index).

Наряду с обновленными компонентами меняются модели обслуживания. Вместо [жизненного цикла продукта SQL Server](https://support.microsoft.com/lifecycle/search?alpha=SQL%20Server%202017) с [накопительными обновлениями SQL Server](https://support.microsoft.com/help/4047329/sql-server-2017-build-versions) служебные обновления теперь соответствуют [графику поддержки Microsoft R Server и Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support) в [современном жизненном цикле](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

Привязка не изменяет основные принципы установки, за исключением версий компонентов и служебных обновлений: Интеграция R и Python по-прежнему является частью экземпляра ядра СУБД, лицензирование не изменяется (привязка не требует дополнительных затрат), а политики поддержки SQL Server по-прежнему сохраняются для ядра СУБД. В оставшейся части этой статьи объясняется механизм привязки и принципы его работы для каждой версии SQL Server.

> [!NOTE]
> Привязка применяется только к экземплярам (в базе данных), привязанным к экземплярам SQL Server. Привязка не относится к (автономной) установке.

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
**Рекомендации по привязке для SQL Server 2017**

Для Служб машинного обучения SQL Server можно использовать привязку только в том случае, если Microsoft Machine Learning Server начинает предлагать дополнительные пакеты или более новые версии по сравнению с уже установленными.
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
**Рекомендации по привязке для SQL Server 2016**

Для клиентов R SQL Server 2016 Services привязка предоставляет обновленные пакеты R, новые пакеты, не входящие в исходную установку ([MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)), и [предварительно обученные модели](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models). Их можно обновлять в дальнейшем в каждом новом основном и дополнительном выпуске [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index). Привязка не предоставляет поддержку Python, которая является компонентом SQL Server 2017.
::: moniker-end

<a name="version-map"></a>

## <a name="version-map"></a>Схема версий

В следующей таблице приведена схема версий, в которой показаны версии пакетов в выпусках, чтобы можно было определить потенциальные варианты обновления при привязке к Microsoft Machine Learning Server (ранее известного как R Server, до добавления поддержки Python с MLS 9.2.1). 

Обратите внимание, что привязка не гарантирует самую последнюю версию R или Anaconda. При привязке к Microsoft Machine Learning Server (MLS) вы получаете версию R или Python, установленную с помощью программы установки, которая может быть не последней версии, доступной в Интернете.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
[**SQL Server 2016 R Services**](../install/sql-r-services-windows-install.md)

Компонент |Начальный выпуск | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [MLS 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [MLS 9.3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) и R | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| н.д. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[предварительно обученные модели](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| н.д. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| н.д. | 1.0 |  1.0 |  1.0 |  1.0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | н.д. | 1.0 |  1.0 |  1.0 |  1.0 |
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
[**Службы машинного обучения SQL Server**](../install/sql-machine-learning-services-windows-install.md)

Компонент |Начальный выпуск | MLS 9.3 | | | |
----------|----------------|---------|-|-|-|-|
Microsoft R Open (MRO) и R | R 3.3.3 | R 3.4.3 | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9.2 |  9.3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1.0 |  1.0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1.0 |  1.0 | | | |
Anaconda 4.2 и Python 3.5  | 4.2/3.5.2 | 4.2/3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2  | 9.3| | | |
[microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[предварительно обученные модели](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9.2 | 9.3| | | |
::: moniker-end

## <a name="how-component-upgrade-works"></a>Как работает обновление компонентов 

Библиотеки R и Python и исполняемые файлы обновляются при привязке существующей установки R и Python к Machine Learning Server. Привязка выполняется [установщиком Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) при запуске программы установки на существующем экземпляре ядра СУБД SQL Server с интеграцией R или Python. Программа установки обнаружит существующие компоненты и предложит выполнить повторную привязку к Machine Learning Server. 

Во время привязки содержимое `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES` и `\PYTHON_SERVICES` перезаписывается новыми исполняемыми файлами и библиотеками `C:\Program Files\Microsoft\ML Server\R_SERVER` и `\PYTHON_SERVER`.

В то же время модель обслуживания меняется с механизмов обновления SQL Server на более частый цикл выпуска основных и дополнительных версий Microsoft Machine Learning Server. Переключение политик поддержки является привлекательным вариантом для команд обработки и анализа данных, которым требуются модули R и Python нового поколения для своих решений. 

+ Без привязки пакеты R и Python получают исправления ошибок при установке пакета обновления SQL Server или накопительного обновления (CU). 
+ С привязкой к экземпляру можно применить новые версии пакетов независимо от расписания выпусков CU в рамках [современной политики жизненного цикла](https://support.microsoft.com/help/30881/modern-lifecycle-policy) и выпусков Microsoft Machine Learning Server. Современная политика поддержки жизненного цикла предлагает более частые обновления в течение короткого периода за один год. После привязки вы продолжите использовать установщик MLS для будущих обновлений R и Python, так как они станут доступны на веб-узлах загрузки Майкрософт.

Привязка применяется только к компонентам R и Python. А именно: пакетам с открытым кодом для компонентов R и Python (Microsoft R Open, Anaconda), а также собственным пакетам RevoScaleR, revoscalepy и т. д. Привязка не изменяет модель поддержки для экземпляра ядра СУБД и не изменяет версию SQL Server.

Привязка обратима. Можно вернуться к обслуживанию SQL Server, [отменив привязку экземпляра](#bkmk_Unbind) и повторно подключив экземпляр ядра СУБД SQL Server.

Общие инструкции по привязке:

+ Начните с существующей настроенной установки SQL Server R Services или Служб машинного обучения SQL Server.
+ Определите, какая версия Microsoft Machine Learning Server содержит обновленные компоненты, которые вы хотите использовать.
+ Загрузите и запустите программу установки для этой версии. Программа установки обнаруживает существующий экземпляр, добавляет параметр привязки и возвращает список совместимых экземпляров.
+ Выберите экземпляр, который необходимо привязать, а затем завершите установку, чтобы выполнить привязку.

С точки зрения взаимодействия с пользователем технология и принципы работы остаются прежними. Единственное отличие заключается в наличии пакетов с более поздней версией и, возможно, дополнительных пакетов, которые изначально не доступны через SQL Server.

## <a name="bkmk_BindWizard"></a>Привязка к MLS с помощью программы установки

Программа установки Служб машинного обучения Microsoft обнаруживает существующие компоненты и версию SQL Server и вызывает служебную программу SqlBindR.exe для изменения привязки. На внутреннем уровне SqlBindR привязан к программе установки и используется косвенно. Позже можно вызвать SqlBindR непосредственно из командной строки, чтобы применить определенные параметры.

1. В SSMS запустите `SELECT @@version`, чтобы убедиться, что сервер соответствует минимальным требованиям к сборке. 

   Для SQL Server 2016 R Services минимумом является [пакет обновления 1 (SP1)](https://www.microsoft.com/download/details.aspx?id=54276) и [CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1).

1. Проверьте версию базы R и пакетов RevoScaleR, чтобы убедиться, что существующие версии ниже тех, которыми вы планируете их заменить. 

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

1. Закройте среду SSMS и другие средства с открытым подключением к SQL Server. Привязка перезаписывает программные файлы. Если SQL Server имеет открытые сеансы, привязка завершится с кодом ошибки привязки 6.

1. Загрузите Microsoft Machine Learning Server на компьютер с экземпляром, который нужно обновить. Мы рекомендуем [последнюю версию](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer).

1. Распакуйте папку и запустите файл ServerSetup.exe, расположенный в разделе MLSWIN93.

   ![Мастер настройки Microsoft Machine Learning Server](media/mls-921-installer-start.PNG)

1. В разделе **Настроить установку** проверьте компоненты для обновления и просмотрите список совместимых экземпляров. 

   Это очень важный шаг.

   В левой части экрана выберите все компоненты, которые необходимо оставить или обновить. Вы не можете обновить некоторые компоненты. Пустой флажок удаляет компонент, если он установлен. На снимке экрана выбран экземпляр служб SQL Server 2016 R Services (MSSQL13), R и версия R предварительно обученных моделей. Эта конфигурация является допустимой, так как SQL Server 2016 поддерживает R, но не Python.

   Если вы обновляете компоненты в службах SQL Server 2016 R Services, не выбирайте компонент Python. Вы не можете добавить Python в SQL Server 2016 R Services.

   Справа установите флажок рядом с именем экземпляра. Если в списке нет ни одного экземпляра, используется несовместимое сочетание. Если экземпляр не выбран, создается новая автономная установка Machine Learning Server и библиотеки SQL Server не изменяются. Если вы не можете выбрать экземпляр, возможно, он не имеет версию [SP1 CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1). 

    ![Этап настройки установки](media/mls-931-installer-mssql13.png)

1. На странице **лицензионное соглашение** выберите **Я принимаю эти условия**, чтобы принять условия лицензирования для Machine Learning Server. 

1. На последующих страницах предоставьте согласие на дополнительные условия лицензирования для всех выбранных компонентов с открытым кодом, например Microsoft R Open или Python Anaconda.

1. На странице **Почти готово** запишите папку установки. Папка по умолчанию: \Program Files\Microsoft\ML Server.

    Если вы хотите изменить папку установки, нажмите кнопку **Дополнительно**, чтобы вернуться на первую страницу мастера. Однако необходимо заново ввести все параметры.

В процессе установки все библиотеки R или Python, используемые SQL Server, заменяются, а панель запуска обновляется для использования новых компонентов. В результате, если экземпляр ранее использовал библиотеки в папке R_SERVICES по умолчанию, после обновления эти библиотеки удаляются, и свойства службы панели запуска изменяются для использования библиотек в новом расположении.

Привязка влияет на содержимое этих папок: Содержимое папки C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library заменяется содержимым папки C:\Program Files\Microsoft\ML Server\R_SERVER. Вторая папка и ее содержимое создаются с помощью программы установки Microsoft Machine Learning Server. 

Если обновление завершается сбоем, проверьте [коды ошибок SqlBindR](#sqlbindr-error-codes) для получения дополнительных сведений.

## <a name="confirm-binding"></a>Подтверждение привязки

Проверьте версию R и RevoScaleR, чтобы убедиться в наличии более новых версий. Для получения сведений о пакете используйте консоль R, поставляемую с пакетами R, в экземпляре ядра СУБД:

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

Для служб SQL Server 2016 R Services, привязанных к Machine Learning Server 9.3, базовый пакет R должен иметь версию 3.4.3, RevoScaleR должен иметь версию 9.3, и у вас должен быть MicrosoftML 9.3. 

Если вы добавили предварительно обученные модели, модели внедряются в библиотеку MicrosoftML, и их можно вызывать с помощью функций MicrosoftML. Дополнительные сведения см. в статье [Примеры R для MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml).

## <a name="offline-binding-no-internet-access"></a>Автономная привязка (без доступа к Интернету)

Для систем без подключения к Интернету можно загрузить установщик и CAB-файлы на компьютер, подключенный к Интернету, а затем перенести файлы на изолированный сервер. 

Установщик (ServerSetup.exe) включает пакеты Microsoft (RevoScaleR, MicrosoftML, olapR, sqlRUtils). CAB-файлы предоставляют другие основные компоненты. Например, CAB-файл SRO предоставляет R Open, распространяемый корпорацией Майкрософт R с открытым кодом.

Приведенные ниже инструкции описывают, как разместить файлы для автономной установки.

1. Загрузите установщик MLS. Он загружается как один сжатый ZIP-файл. Мы рекомендуем [последнюю версию](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer), но можно также установить [более ранние версии](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components).

1. Загрузите CAB-файлы. Ниже приведены ссылки на выпуск 9.3. Если требуются более ранние версии, дополнительные ссылки можно найти в [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components). Вспомним, что Python/Anaconda можно добавить только в экземпляр Служб машинного обучения SQL Server. Предварительно обученные модели существуют как для R, так и для Python; CAB-файл предоставляет модели на языках, которые вы используете.

    | Компонент | Загрузить |
    |---------|----------|
    | Чтение       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | Предварительно обученная модель | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. Переместите ZIP- и CAB-файлы на целевой сервер.

1. На сервере введите `%temp%` в поле выполнения команд, чтобы получить физическое расположение временного каталога. Физический путь зависит от компьютера, но обычно это `C:\Users\<your-user-name>\AppData\Local\Temp`.

1. Поместите CAB-файлы в папку %temp%.

1. Распакуйте установщик.

1. Запустите ServerSetup.exe, следуя инструкциям на экране, чтобы завершить установку.

## <a name="bkmk_BindCmd"></a>Операции командной строки

После запуска Microsoft Machine Learning Server будет доступна служебная программа командной строки SqlBindR.exe, которую можно использовать для дальнейших операций привязки. Например, если вы решили отменить привязку, можно повторно запустить программу установки или использовать программу командной строки. Кроме того, это средство можно использовать для проверки совместимости и доступности экземпляра.

> [!TIP]
> Не удается найти SqlBindR? Возможно, вы не запустили программу установки. SqlBindR доступен только после запуска программы установки Machine Learning Server.

1. Откройте командную строку от имени администратора и перейдите в папку, содержащую sqlbindr.exe. Путь по умолчанию: C:\Program Files\Microsoft\MLServer\Setup

2. Выполните следующую команду, чтобы просмотреть список доступных экземпляров: `SqlBindR.exe /list`.
  
   Запишите полное имя экземпляра. Например, имя экземпляра может быть MSSQL14.MSSQLSERVER для экземпляра по умолчанию или что-то вроде SERVERNAME.МОЙ_ИМЕНОВАННЫЙ_ЭКЗЕМПЛЯР.

3. Выполните команду **SqlBindR.exe** с аргументом */bind* и укажите имя обновляемого экземпляра, указав имя экземпляра, возвращенное на предыдущем шаге.

   Например, чтобы обновить экземпляр по умолчанию, введите следующую команду: `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. После завершения обновления перезапустите службу панели запуска, связанную с любым измененным экземпляром.

## <a name="bkmk_Unbind"></a>Отмена привязки экземпляра

Вы можете восстановить привязанный экземпляр до первоначальной установки компонентов R и Python, выполненной программой установки SQL Server. Возврат к обслуживанию на SQL Server выполняется в три этапа.

+ [Шаг 1. Удаление привязки к Microsoft Machine Learning Server](#step-1-unbind)
+ [Шаг 2. Восстановление исходного состояния экземпляра](#step-2-restore)
+ [Шаг 3. Переустановка пакетов, добавленных в установку](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Шаг 1. Отменить привязку

Существует два варианта отката привязки: повторно запустите программу установки или используйте служебную программу командной строки SqlBindR.

#### <a name="bkmk_wizunbind"></a> Отмена привязки с помощью программы установки

1. Найдите установщик для Machine Learning Server. Если установщик был удален, загрузите его снова или скопируйте с другого компьютера.
2. Запустите установщик на компьютере с экземпляром, для которого нужно отменить привязку.
2. Установщик определяет локальные экземпляры, которые являются кандидатами для отмены привязки.
3. Снимите флажок рядом с экземпляром, который вы хотите вернуть в исходную конфигурацию.
4. Примите лицензионное соглашение. Необходимо принять условия лицензионного соглашения даже при установке.
5. Нажмите кнопку **Готово**. Процесс займет некоторое время.

#### <a name="bkmk_cmdunbind"></a> Отмена привязки с помощью командной строки

1. Откройте командную строку и перейдите в папку, содержащую **sqlbindr.exe**, как описано в предыдущем разделе.

2. Выполните команду **SqlBindR.exe** с аргументом */unbind* и укажите экземпляр.

   Например, следующая команда отменяет привязку экземпляра по умолчанию:
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Шаг 2. Восстановление экземпляра SQL Server

Запустите программу установки SQL Server, чтобы восстановить экземпляр ядра СУБД с компонентами R и Python. Существующие обновления сохраняются, но если вы пропустили служебные обновления SQL Server для пакетов R и Python, эти исправления будут применены.

Кроме того, это потребует больше работы, но вы также можете полностью удалить и переустановить экземпляр ядра СУБД, а затем применить все служебные обновления.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Шаг 3. Добавление сторонних пакетов

Вы могли добавить в библиотеку пакетов другие пакеты с открытым кодом или сторонние пакеты. Так как отмена привязки меняет расположение библиотеки пакетов по умолчанию, необходимо переустановить пакеты в библиотеку, которую теперь используют R и Python. Дополнительные сведения см. в статьях [Сведения о пакете R](../package-management/r-package-information.md) и [Установка пакета R](../package-management/install-additional-r-packages-on-sql-server.md) и [Сведения о пакете Python](../package-management/python-package-information.md) и [Установка пакета Python](../package-management/install-additional-python-packages-on-sql-server.md).

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

## <a name="binding-errors"></a>Ошибки привязки

Установщик MLS и SqlBindR возвращают следующие коды ошибок и сообщения об ошибках.

|Код ошибки  | Сообщение           | Сведения               |
|------------|-------------------|-----------------------|
|Ошибка привязки 0 | Ok (успешно) | Привязка прошла без ошибок. |
|Ошибка привязки 1 | Недопустимые аргументы | Синтаксическая ошибка. |
|Ошибка привязки 2 | Недопустимое действие | Синтаксическая ошибка. |
|Ошибка привязки 3 | Недопустимый экземпляр | Экземпляр существует, но не является допустимым для привязки. |
|Ошибка привязки 4 | Не подлежит привязке | |
|Ошибка привязки 5 | Уже привязан | Вы выполнили команду *bind* , но указанный экземпляр уже привязан. |
|Ошибка привязки 6 | Сбой привязки | При отмене привязки экземпляра произошла ошибка. Эта ошибка может возникать, если запустить установщик MLS без выбора компонентов. Для привязки необходимо выбрать экземпляр MSSQL и R и Python, если это экземпляр SQL Server 2017. Эта ошибка также возникает, если SqlBindR не удалось выполнить запись в папку Program Files. Открытые сеансы или дескрипторы SQL Server приведут к этой ошибке. При возникновении этой ошибки перезагрузите компьютер и повторите действия привязки, прежде чем запускать новые сеансы.|
|Ошибка привязки 7 | Нет привязки | В экземпляре ядра СУБД имеются службы R Services или Службы машинного обучения SQL Server. Экземпляр не привязан к Microsoft Machine Learning Server. |
|Ошибка привязки 8 | Не удалось отменить привязку | При отмене привязки экземпляра произошла ошибка. |
|Ошибка привязки 9 | Экземпляры не найдены. | На этом компьютере не найдены экземпляры ядра СУБД. |

## <a name="known-issues"></a>Известные проблемы

В этом разделе перечислены известные проблемы, связанные с использованием служебной программы SqlBindR.exe, а также обновлениями Machine Learning Server, которые могут повлиять на экземпляры SQL Server.

### <a name="restoring-packages-that-were-previously-installed"></a>Восстановление ранее установленных пакетов

Если вы выполнили обновление до Microsoft R Server 9.0.1, версии SqlBindR.exe для этой версии не удалось полностью восстановить исходные пакеты или компоненты R, поэтому пользователь должен выполнить восстановление SQL Server на экземпляре, применить всех служебные выпуски, а затем перезапустить экземпляр.

Более поздняя версия SqlBindR автоматически восстанавливает первоначальные компоненты R, устраняя необходимость в переустановке компонентов R или повторном исправлении сервера. Однако необходимо установить все обновления пакетов R, которые могли быть добавлены после первоначальной установки.

Если вы использовали роли управления пакетами для установки и совместного использования пакета, эту задачу будет гораздо проще выполнить: можно использовать команды R для синхронизации установленных пакетов с файловой системой с помощью записей в базе данных и наоборот. Дополнительные сведения см. в разделе [Управление пакетами R для SQL Server](../r/install-additional-r-packages-on-sql-server.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Проблемы с несколькими обновлениями от SQL Server

Если ранее экземпляр SQL Server 2016 R Services был обновлен до 9.0.1, при запуске нового установщика для Microsoft R Server 9.1.0 отображается список всех допустимых экземпляров, а затем по умолчанию выбираются ранее привязанные экземпляры. Если продолжить, для ранее привязанных экземпляров будет отменена привязка. В результате предыдущая установка 9.0.1 удаляется, включая все связанные пакеты, но новая версия Microsoft R Server (9.1.0) не устанавливается.

В качестве обходного решения можно изменить имеющуюся установку R Server следующим образом:
1. На панели управления и откройте элемент **Установка и удаление программ**.
2. Найдите Microsoft R Server и щелкните **Изменить**.
3. При запуске установщика выберите экземпляры, которые необходимо привязать к 9.1.0.

Microsoft Machine Learning Server 9.2.1 и 9.3 не имеют этой проблемы.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>Привязка или отмена привязки оставляет несколько временных папок

Иногда операции привязки и отмены привязки не позволяют очищать временные папки.
Если вы найдете папки с таким именем, вы можете удалить их после завершения установки: R_SERVICES_<guid>

> [!NOTE]
> Не забудьте дождаться завершения установки. Удаление библиотек R, связанных с одной версией, и добавление новых библиотек R может занять много времени. По завершении операции временные папки удаляются.

## <a name="see-also"></a>См. также раздел

+ [Установка Machine Learning Server для Windows (с подключением к Интернету)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Установка Machine Learning Server для Windows (в автономном режиме)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Известные проблемы в Службах машинного обучения](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Объявления о компонентах из предыдущего выпуска R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Нерекомендуемые, неподдерживаемые или измененные функции](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
