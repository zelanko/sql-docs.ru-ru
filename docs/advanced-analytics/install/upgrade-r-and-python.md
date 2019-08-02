---
title: Обновление компонентов R и Python
description: Обновите R и Python в SQL Server Службы машинного обучения или SQL Server R Services с помощью sqlbindr. exe для привязки к Machine Learning Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 948ce20bf32aaa2051c4a805a3ca2f131a7c0c8f
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715216"
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>Обновление компонентов машинного обучения (R и Python) в SQL Server экземплярах
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Интеграция R и Python в SQL Server включает в себя пакеты с открытым исходным кодом и собственными пакетами Майкрософт. В рамках стандартного обслуживания SQL Server пакеты обновляются в соответствии с циклом выпуска SQL Server, с исправлениями ошибок в существующих пакетах в текущей версии, но без обновления основных версий. 

Однако многие специалисты по обработке и анализу данных привыкли работать с новыми пакетами по мере их появления. Для SQL Server Службы машинного обучения (в базе данных) и SQL Server R Services (в базе данных) можно получить [более новые версии R и Python](#version-map) путем *привязки* к **Microsoft Machine Learning Server**. 

## <a name="what-is-binding"></a>Что такое привязка?

Привязка — это процесс установки, который заменяет содержимое папок R_SERVICES и PYTHON_SERVICES новыми исполняемыми файлами, библиотеками и инструментами из [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index).

Наряду с обновленными компонентами в моделях обслуживания входит переключатель. Вместо [SQL Server жизненного цикла продукта](https://support.microsoft.com/lifecycle/search?alpha=SQL%20Server%202017)с [SQL Server накопительными обновлениями](https://support.microsoft.com/help/4047329/sql-server-2017-build-versions)служба теперь будет соответствовать [временной шкале поддержки для Microsoft R Server & Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support) в [современном жизненном цикле](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

Привязка не изменяет основные принципы установки, за исключением версий компонентов и обновлений служб. Интеграция R и Python по-прежнему является частью экземпляра ядра СУБД, лицензирование не изменяется (дополнительные затраты не связаны с привязкой), а SQL Server политики поддержки по-прежнему хранятся в ядре СУБД. В оставшейся части этой статьи объясняется механизм привязки и принципы его работы для каждой версии SQL Server.

> [!NOTE]
> Привязка применяется только к экземплярам (в базе данных), привязанным к экземплярам SQL Server. Привязка не относится к (автономной) установке.

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
**Рекомендации по привязке SQL Server 2017**

Для SQL Server Службы машинного обучения можно использовать привязку только в том случае, если Microsoft Machine Learning Server начинает предлагать дополнительные пакеты или более новые версии по сравнению с тем, что у вас уже есть.
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
**Рекомендации по привязке SQL Server 2016**

Для клиентов служб R SQL Server 2016, привязка предоставляет обновленные пакеты R, новые пакеты, не входящие в исходную установку ([MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)), и предварительно обученные [модели](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models), все из которых можно обновить в каждом новом основном и дополнительном выпуске. [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index). Привязка не предоставляет поддержку Python, которая является компонентом SQL Server 2017.
::: moniker-end

<a name="version-map"></a>

## <a name="version-map"></a>Схема версии

В следующей таблице приведена схема версий, в которой показаны версии пакетов между серверами выпусков, чтобы можно было определить потенциальные варианты обновления при привязке к Microsoft Machine Learning Server (ранее известной как R Server, прежде чем добавление поддержки Python будет начато. в MLS 9.2.1). 

Обратите внимание, что привязка не гарантирует самую последнюю версию R или Anaconda. При привязке к Microsoft Machine Learning Server (MLS) вы получаете версию R или Python, установленную с помощью программы установки, которая может быть не последней версии, доступной в Интернете.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
[**Службы SQL Server 2016 R**](../install/sql-r-services-windows-install.md)

Компонент |Первоначальный выпуск | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9,1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [MLS 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [MLS 9,3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) по R | 3\.2.2 R     | 3\.3.2 R   |3\.3.3 R   | 3\.4.1 R  | 3\.4.3 R |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9,1 |  9.2.1 |  9,3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| н.а. | 9.0.1 |  9,1 |  9.2.1 |  9,3 |
[предварительно обученные модели](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| н.а. | 9.0.1 |  9,1 |  9.2.1 |  9,3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| н.а. | 1.0 |  1.0 |  1.0 |  1.0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | н.а. | 1.0 |  1.0 |  1.0 |  1.0 |
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
[**SQL Server Службы машинного обучения**](../install/sql-machine-learning-services-windows-install.md)

Компонент |Первоначальный выпуск | MLS 9,3 | | | |
----------|----------------|---------|-|-|-|-|
Microsoft R Open (MRO) по R | 3\.3.3 R | 3\.4.3 R | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9,2 |  9,3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9,2  | 9,3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1.0 |  1.0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1.0 |  1.0 | | | |
Anaconda 4,2 через Python 3,5  | 4.2 и 3.5.2 | 4.2 и 3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9,2  | 9,3| | | |
[microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9,2  | 9,3| | | |
[предварительно обученные модели](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9,2 | 9,3| | | |
::: moniker-end

## <a name="how-component-upgrade-works"></a>Как работает обновление компонента 

Библиотеки r и Python и исполняемые файлы обновляются при привязке существующей установки R и Python к Machine Learning Server. Привязка выполняется [установщиком Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) при запуске программы установки на существующем SQL Server экземпляре ядра СУБД с интеграцией R или Python. Программа установки обнаружит существующие компоненты и предложит выполнить повторную привязку к Machine Learning Server. 

Во время привязки `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES` содержимое и `\PYTHON_SERVICES` перезаписывается новыми `C:\Program Files\Microsoft\ML Server\R_SERVER` исполняемыми файлами и библиотеками и `\PYTHON_SERVER`.

В то же время модель обслуживания также перемещается с SQL Server механизмов обновления на более частый основной и дополнительный циклы выхода Microsoft Machine Learning Server. Переключение политик поддержки является привлекательным вариантом для команд обработки и анализа данных, которым требуются модули R и Python нового поколения для своих решений. 

+ Без привязки пакеты R и Python исправлены для исправлений ошибок при установке пакета обновления SQL Server или накопительного обновления (CU). 
+ С помощью привязки к экземпляру можно применить более новые версии пакетов независимо от расписания выпуска CU в рамках [современной политики жизненного цикла](https://support.microsoft.com/help/30881/modern-lifecycle-policy) и выпусков Microsoft Machine Learning Server. Современная политика поддержки жизненного цикла предлагает более частые обновления в течение короткого периода в течение одного года. После привязки вы продолжите использовать установщик MLS для будущих обновлений R и Python, так как они станут доступны на веб-узлах загрузки Майкрософт.

Привязка применяется только к функциям R и Python. А именно, пакеты с открытым исходным кодом для функций R и Python (Microsoft R Open, Anaconda), а также собственные пакеты RevoScaleR, revoscalepy и т. д. Привязка не изменяет модель поддержки для экземпляра ядра СУБД и не изменяет версию SQL Server.

Привязка обратима. Вы можете вернуться к SQL Server обслуживания, отменив [привязку экземпляра](#bkmk_Unbind) и репаринг свой экземпляр ядра СУБД SQL Server.

В суммировании приведены шаги для привязки.

+ Начните с существующей, настроенной установки SQL Server R Services или SQL Server Службы машинного обучения.
+ Определите, какая версия Microsoft Machine Learning Server содержит обновленные компоненты, которые вы хотите использовать.
+ Скачайте и запустите программу установки для этой версии. Программа установки обнаруживает существующий экземпляр, добавляет параметр привязки и возвращает список совместимых экземпляров.
+ Выберите экземпляр, который необходимо привязать, а затем завершите установку, чтобы выполнить привязку.

С точки зрения взаимодействия с пользователем технология и принципы работы с ней не меняются. Единственное отличие заключается в наличии пакетов с более поздней версией и, возможно, дополнительных пакетов, которые изначально не доступны через SQL Server.

## <a name="bkmk_BindWizard"></a>Привязка к MLS с помощью программы установки

Программа установки Microsoft Машинное обучение обнаруживает существующие компоненты и SQL Server версию и вызывает служебную программу с именем SqlBindR. exe для изменения привязки. На внутреннем уровне SqlBindR передается в цепочку на установку и используется косвенно. Позже можно вызвать SqlBindR непосредственно из командной строки, чтобы применить определенные параметры.

1. В SSMS выполните команду `SELECT @@version` , чтобы проверить соответствие сервера минимальным требованиям к сборке. 

   Для служб SQL Server 2016 R Services минимальное значение — [пакет обновления 1](https://www.microsoft.com/download/details.aspx?id=54276) (SP1) и [CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1).

1. Проверьте версию R Base и пакеты RevoScaleR, чтобы убедиться, что существующие версии ниже, чем вы планируете заменить. 

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

1. Скачайте Microsoft Machine Learning Server на компьютер, где находится экземпляр, который требуется обновить. Мы рекомендуем использовать [последнюю версию](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer).

1. Распакуйте папку и запустите Серверсетуп. exe, расположенную в разделе MLSWIN93.

   ![Мастер установки Microsoft Machine Learning Server](media/mls-921-installer-start.PNG)

1. На странице **Настройка установки**Проверьте компоненты, которые необходимо обновить, и проверьте список совместимых экземпляров. 

   Этот шаг очень важен.

   В левой части экрана выберите все компоненты, которые необходимо оставить или обновить. Вы не можете обновить некоторые компоненты, а не другие. Пустой флажок удаляет эту функцию, если она установлена в настоящий момент. На снимке экрана выбран экземпляр служб SQL Server 2016 R Services (MSSQL13), R и версия R предварительно обученных моделей. Эта конфигурация является допустимой, так как SQL Server 2016 поддерживает R, но не Python.

   Если вы обновляете компоненты в службах SQL Server 2016 R, не выбирайте компонент Python. Вы не можете добавить Python в службы SQL Server 2016 R.

   Справа установите флажок рядом с именем экземпляра. Если в списке нет ни одного экземпляра, используется несовместимое сочетание. Если экземпляр не выбран, создается новая автономная установка Machine Learning Server и библиотеки SQL Server не изменяются. Если вы не можете выбрать экземпляр, возможно, он не находится в [CU3 с пакетом обновления 1 (SP1)](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1). 

    ![Настройка шага установки](media/mls-931-installer-mssql13.png)

1. На странице **лицензионное соглашение** выберите **я принимаю эти условия** , чтобы принять условия лицензионного соглашения для Machine Learning Server. 

1. На последующих страницах предоставьте согласие на дополнительные условия лицензирования для всех выбранных компонентов с открытым кодом, например Microsoft R Open или Anacondaного распространения Python.

1. На странице **почти здесь** запишите папку установки. Папка по умолчанию — \Program Филес\микрософт\мл Server.

    Если вы хотите изменить папку установки, нажмите кнопку **Дополнительно** , чтобы вернуться на первую страницу мастера. Однако необходимо повторить все предыдущие элементы.

В процессе установки все библиотеки R или Python, используемые SQL Server, заменяются, а панель запуска обновляется для использования новых компонентов. В результате, если экземпляр ранее использовал библиотеки в папке R_SERVICES по умолчанию, после обновления эти библиотеки будут удалены, а свойства для службы панели запуска будут изменены для использования библиотек в новом расположении.

Привязка влияет на содержимое этих папок: C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library заменяется содержимым C:\Program Филес\микрософт\мл Server\R_SERVER. Вторая папка и ее содержимое создаются с помощью Microsoft Machine Learning Server установки. 

Если обновление завершается сбоем, проверьте [коды ошибок SqlBindR](#sqlbindr-error-codes) для получения дополнительных сведений.

## <a name="confirm-binding"></a>Подтвердить привязку

Проверьте версию R и RevoScaleR, чтобы убедиться в наличии более новых версий. Для получения сведений о пакете используйте консоль R, распределенную с пакетами R в экземпляре ядра СУБД.

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

Для SQL Server 2016 служб R, привязанных к Machine Learning Server 9,3, базовый пакет R должен быть 3.4.3, RevoScaleR должен быть 9,3, а также должен быть MicrosoftML 9,3. 

Если вы добавили предварительно обученные модели, модели внедряются в библиотеку MicrosoftML и их можно вызывать с помощью функций MicrosoftML. Дополнительные сведения см. в статье [примеры R для MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml).

## <a name="offline-binding-no-internet-access"></a>Автономная привязка (без доступа к Интернету)

Для систем без подключения к Интернету можно загрузить установщик и CAB-файлы на компьютер, подключенный к Интернету, а затем переносить файлы на изолированный сервер. 

Установщик (Серверсетуп. exe) включает пакеты Microsoft (RevoScaleR, MicrosoftML, OLAP, sqlRUtils). CAB-файлы предоставляют другие основные компоненты. Например, CAB-файл «СРО» предоставляет R Open, распространяемый корпорацией Майкрософт код R с открытым кодом.

Приведенные ниже инструкции описывают, как разместить файлы для автономной установки.

1. Скачайте установщик MLS. Загружается как один сжатый ZIP-файл. Мы рекомендуем использовать [последнюю версию](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer), но вы также можете установить [более ранние версии](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components).

1. Скачайте CAB-файлы. Ниже приведены ссылки на выпуск 9,3. Если требуются более ранние версии, дополнительные ссылки можно найти в [R Server 9,1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components). Вспомним, что Python/Anaconda можно добавить только в экземпляр SQL Server Службы машинного обучения. Предварительно обученные модели существуют как для R, так и для Python; CAB предоставляет модели на языках, которые вы используете.

    | Компонент | Загрузить |
    |---------|----------|
    | R       | [SRO_ 3.4.3.0 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_ 9.3.0.0 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | Предварительно обученная модель | [MLM_ 9.3.0.0 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. Переместите ZIP-и CAB-файлы на целевой сервер.

1. На сервере введите `%temp%` команду Run, чтобы получить физическое расположение временного каталога. Физический путь зависит от компьютера, но обычно `C:\Users\<your-user-name>\AppData\Local\Temp`это.

1. Поместите CAB-файлы в папку% Temp%.

1. Распакуйте установщик.

1. Запустите Серверсетуп. exe и следуйте инструкциям на экране, чтобы завершить установку.

## <a name="bkmk_BindCmd"></a>Операции командной строки

После запуска Microsoft Machine Learning Server будет доступна служебная программа командной строки с именем SqlBindR. exe, которую можно использовать для дальнейших операций привязки. Например, если вы решили отменить привязку, можно либо повторно запустить программу установки, либо использовать программу командной строки. Кроме того, это средство можно использовать для проверки совместимости и доступности экземпляра.

> [!TIP]
> Не удается найти SqlBindR? Возможно, вы не запустили программу установки. SqlBindR доступен только после запуска программы установки Machine Learning Server.

1. Откройте командную строку от имени администратора и перейдите в папку, содержащую sqlbindr.exe. Расположение по умолчанию — C:\Program Филес\микрософт\млсервер\сетуп

2. Выполните следующую команду, чтобы просмотреть список доступных экземпляров: `SqlBindR.exe /list`.
  
   Запишите полное имя экземпляра. Например, имя экземпляра может быть MSSQL14. MSSQLSERVER для экземпляра по умолчанию или что-то вроде SERVERNAME. МойИменованныйЭкземпляр.

3. Выполните команду **SqlBindR. exe** с аргументом */BIND* и укажите имя экземпляра для обновления, используя имя экземпляра, которое было возвращено на предыдущем шаге.

   Например, чтобы обновить экземпляр по умолчанию, введите:`SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. После завершения обновления перезапустите службу панели запуска, связанную с любым измененным экземпляром.

## <a name="bkmk_Unbind"></a>Возврат или Отмена привязки экземпляра

Можно восстановить привязанный экземпляр до первоначальной установки компонентов R и Python, установленных SQL Server установки. Возврат к SQL Serverному обслуживанию состоит из трех частей.

+ [Шаг 1. Отменить привязку к Microsoft Machine Learning Server](#step-1-unbind)
+ [Шаг 2. Восстановить исходное состояние экземпляра](#step-2-restore)
+ [Шаг 3. Переустановите все пакеты, добавленные в установку](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Шаг 1. Отменить привязку

Существует два варианта отката привязки: повторно запустите программу установки или используйте служебную программу командной строки SqlBindR.

#### <a name="bkmk_wizunbind"></a>Отменить привязку с помощью программы установки

1. Поиск установщика для Machine Learning Server. Если установщик был удален, может потребоваться его загрузка или копирование с другого компьютера.
2. Не забудьте запустить установщик на компьютере, на котором находится экземпляр, для которого требуется отменить привязку.
2. Установщик определяет локальные экземпляры, которые являются кандидатами для отмены привязки.
3. Снимите флажок рядом с экземпляром, к которому нужно вернуться исходную конфигурацию.
4. Примите условия лицензионного соглашения. Необходимо указать согласие на принятие условий лицензионного соглашения даже при установке.
5. Нажмите кнопку **Готово**. Процесс займет некоторое время.

#### <a name="bkmk_cmdunbind"></a>Отмена привязки с помощью командной строки

1. Откройте командную строку и перейдите в папку, содержащую **sqlbindr.exe**, как описано в предыдущем разделе.

2. Выполните команду **SqlBindR.exe** с аргументом */unbind* и укажите экземпляр.

   Например, следующая команда возвращает экземпляр по умолчанию:
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Шаг 2. Восстановление экземпляра SQL Server

Запустите программу установки SQL Server, чтобы восстановить экземпляр ядра СУБД с функциями R и Python. Существующие обновления сохраняются, но если вы пропустили SQL Server обслуживания обновлений для пакетов R и Python, эти исправления будут применены.

Кроме того, это больше работы, но вы также можете полностью удалить и переустановить экземпляр ядра СУБД, а затем применить все обновления службы.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Шаг 3. Добавление пакетов сторонних разработчиков

Возможно, вы добавили в библиотеку пакетов другие пакеты с открытым кодом или сторонними разработчиками. Так как обратная привязка переключается на расположение библиотеки пакетов по умолчанию, необходимо переустановить пакеты в библиотеку, которую теперь используют R и Python. Дополнительные сведения см. в статьях [пакеты по умолчанию](../package-management/default-packages.md), [Установка новых пакетов R](../r/install-additional-r-packages-on-sql-server.md)и [Установка новых пакетов Python](../python/install-additional-python-packages-on-sql-server.md).

## <a name="sqlbindrexe-command-syntax"></a>Синтаксис команды SqlBindR. exe

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

|Код ошибки  | `Message`           | Сведения               |
|------------|-------------------|-----------------------|
|Ошибка привязки 0 | ОК (успешное завершение) | Привязка передается без ошибок. |
|Ошибка привязки 1 | Недопустимые аргументы | Синтаксическая ошибка. |
|Ошибка привязки 2 | Недопустимое действие | Синтаксическая ошибка. |
|Ошибка привязки 3 | Недопустимый экземпляр | Экземпляр существует, но не является допустимым для привязки. |
|Ошибка привязки 4 | Не привязано | |
|Ошибка привязки 5 | Уже привязано | Вы выполнили команду *bind* , но указанный экземпляр уже привязан. |
|Ошибка привязки 6 | Сбой привязки | Произошла ошибка при отмене привязки экземпляра. Эта ошибка может возникать, если запустить установщик MLS без выбора каких бы то ни было функций. Для привязки необходимо выбрать экземпляр MSSQL и R и Python, предполагая, что экземпляр SQL Server 2017. Эта ошибка также возникает, если SqlBindR не удалось выполнить запись в папку Program Files. Открытые сеансы или дескрипторы SQL Server приведут к возникновению этой ошибки. При возникновении этой ошибки перезагрузите компьютер и повторите действия привязки, прежде чем запускать новые сеансы.|
|Ошибка привязки 7 | Не привязано | В экземпляре ядра СУБД имеются службы R или SQL Server Службы машинного обучения. Экземпляр не привязан к Microsoft Machine Learning Server. |
|Ошибка привязки 8 | Не удалось отменить привязку | Произошла ошибка при отмене привязки экземпляра. |
|Ошибка привязки 9 | Экземпляры не найдены. | На этом компьютере не найдены экземпляры ядра СУБД. |

## <a name="known-issues"></a>Известные проблемы

В этом разделе перечислены известные проблемы, связанные с использованием служебной программы SqlBindR. exe, а также обновления Machine Learning Server, которые могут повлиять на экземпляры SQL Server.

### <a name="restoring-packages-that-were-previously-installed"></a>Восстановление ранее установленных пакетов

Если вы обновили до Microsoft R Server 9.0.1, то версии SqlBindR. exe для этой версии не удалось полностью восстановить исходные пакеты или компоненты R, что требует запуска SQL Server восстановления на экземпляре, применения всех выпусков служб и перезапуска. экземпляр.

Более поздняя версия SqlBindR автоматически восстанавливает первоначальные компоненты R, устраняя необходимость в переустановке компонентов R или повторном исправлении сервера. Однако необходимо установить все обновления пакетов R, которые могли быть добавлены после первоначальной установки.

Если вы использовали роли управления пакетами для установки и совместного использования пакета, эта задача гораздо проще: можно использовать команды R для синхронизации установленных пакетов с файловой системой с помощью записей в базе данных и наоборот. Дополнительные сведения см. в статье [Управление пакетами R для SQL Server](../r/install-additional-r-packages-on-sql-server.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Проблемы с несколькими обновлениями от SQL Server

Если ранее экземпляр служб SQL Server 2016 R был обновлен до 9.0.1, при запуске нового установщика для Microsoft R Server 9.1.0 отображается список всех допустимых экземпляров, а затем по умолчанию выбираются ранее привязанные экземпляры. Если продолжить, ранее привязанные экземпляры не будут привязаны. В результате Предыдущая установка 9.0.1 удаляется, включая все связанные пакеты, но новая версия Microsoft R Server (9.1.0) не устанавливается.

В качестве обходного решения можно изменить имеющуюся установку R Server следующим образом:
1. На панели управления откройте окно **Установка и удаление программ**.
2. Перейдите на Microsoft R Server и нажмите кнопку **изменить/изменить**.
3. При запуске программы установки выберите экземпляры, которые необходимо привязать к 9.1.0.

Microsoft Machine Learning Server 9.2.1 и 9,3 не имеют этой проблемы.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>Привязка или Отмена привязки оставляет несколько временных папок

Иногда операции привязки и отмены привязки не позволяют очищать временные папки.
Если вы найдете папки с таким именем, вы можете удалить ее после завершения установки: R_SERVICES_<guid>

> [!NOTE]
> Не забудьте дождаться завершения установки. Удаление библиотек R, связанных с одной версией, и добавление новых библиотек R может занять много времени. По завершении операции временные папки удаляются.

## <a name="see-also"></a>См. также

+ [Установка Machine Learning Server для Windows (с подключением к Интернету)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Установка Machine Learning Server для Windows (автономная)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Известные проблемы в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Объявления о функциях из предыдущего выпуска R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Нерекомендуемые, неподдерживаемые или измененные функции](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
