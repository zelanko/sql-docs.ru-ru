---
title: Обновление компонентов Python и R
description: Обновите R и Python в Службах машинного обучения SQL Server или SQL Server R Services, используя sqlbindr.exe для привязки к Machine Learning Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 04/03/2020
ms.topic: how-to
author: cawrites
ms.author: chadam
monikerRange: =sql-server-2016||=sql-server-2017||=sqlallproducts-allversions
ms.openlocfilehash: 918ab8c2b1e643196e99cd11ff92c07c3978e078
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85900078"
---
# <a name="upgrade-machine-learning-python-and-r-components-in-sql-server-instances"></a>Обновление компонентов машинного обучения (R и Python) в экземплярах SQL Server
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

Интеграция R и Python в SQL Server включает в себя пакеты с открытым кодом и собственные пакеты Майкрософт.
                                                                               
Стандартное обслуживание SQL Server предусматривает следующее:
                                                                               
- Пакеты обновляются в соответствии с циклом выпуска SQL Server.
- Исправления ошибок применяются к существующим пакетам в текущей версии.
- Обновление основных версий не производится.

Вы можете получать [более новые версии Python и R](#version-map) путем *привязки* к **Microsoft Machine Learning Server**. Версия применяется как к Службам машинного обучения SQL Server (в базе данных), так и к SQL Server R Services (в базе данных).

Возможность получения новых пакетов предпочтительна, если вы работаете с данными, например специалистом по обработке и анализу данных.

## <a name="what-is-binding"></a>Что такое привязка?

Привязка — это процесс установки, который меняет содержимое папок R_SERVICES и PYTHON_SERVICES на более новые исполняемые файлы, библиотеки и инструменты с [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index).

Передаваемые компоненты в составе модели обслуживания изменились.

Обновления службы выполняются по [графику поддержки Microsoft R Server и Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support) согласно [политике современного жизненного цикла](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

Привязка не изменяет основные принципы установки, за исключением версий компонентов и служебных обновлений:

- Интеграция Python и R по-прежнему является частью экземпляра ядра СУБД.
- Лицензирование остается неизменным (привязка не влечет никаких дополнительных затрат).
- Политики поддержки SQL Server сохраняются для ядра СУБД. 

В оставшейся части этой статьи объясняется механизм привязки и принципы его работы для каждой версии SQL Server.

> [!NOTE]
> Привязка применяется только к экземплярам (в базе данных), связанным с экземплярами SQL Server. В этом случае для установки (автономной) не требуется привязка.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
**Рекомендации по привязке для SQL Server 2016**

Для клиентов служб SQL Server 2016 R привязка предоставляет такие преимущества:

- Обновленные пакеты R.
- Новые пакеты не входят в исходную установку ([Microsoft ML](https://  docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)).
- Предварительно обученные [модели машинного обучения](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) для анализа тональности и обнаружения изображений.

Все привязки могут быть дополнительно обновлены при выходе нового главного и второстепенного выпуска [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index).
::: moniker-end

## <a name="version-map"></a>Схема версий

Таблицы ниже являются схемами версий. В каждой схеме показаны версии пакетов для разных выпусков. Вы можете просмотреть пути обновления при привязке к Microsoft Machine Learning Server (ранее известному как R Server до добавления поддержки Python в Machine Learning Server 9.2.1).

Привязка не гарантирует использование самой последней версии R или Anaconda. При привязке к Microsoft Machine Learning Server вы получаете версию R или Python, установленную с помощью программы установки, которая может быть не последней версии, доступной в Интернете.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
[**SQL Server 2016 R Services**](../install/sql-r-services-windows-install.md)

Компонент |Начальный выпуск | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [Machine Learning Server 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [Machine Learning Server 9.3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) и R | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| н.д. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[предварительно обученные модели](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| н.д. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| н.д. | 1.0 |  1.0 |  1.0 |  1.0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | н.д. | 1.0 |  1.0 |  1.0 |  1.0 |
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
[**Службы машинного обучения SQL Server 2017**](../install/sql-machine-learning-services-windows-install.md)

Компонент |Начальный выпуск | Machine Learning Server 9.3 | | | |
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

Библиотеки R и Python и исполняемые файлы обновляются при привязке существующей установки R и Python к Machine Learning Server.

Привязка выполняется [установщиком Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) при запуске программы установки на существующем экземпляре ядра СУБД SQL Server с интеграцией R или Python. 

Программа установки обнаружит существующие компоненты и предложит выполнить повторную привязку к Machine Learning Server.

Во время привязки содержимое `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES` и `\PYTHON_SERVICES` перезаписывается новыми исполняемыми файлами и библиотеками `C:\Program Files\Microsoft\ML Server\R_SERVER` и `\PYTHON_SERVER`.

Привязка применяется только к компонентам R и Python. В состав пакетов с открытым исходным кодом для Python и R входят:

- Anaconda
- Microsoft R Open
- собственные пакеты RevoScaleR
- Revoscalepy

Привязка не изменяет модель поддержки для экземпляра ядра СУБД или версию SQL Server.

Привязка обратима. Можно вернуться к обслуживанию SQL Server, [отменив привязку экземпляра](#bkmk_Unbind) и повторно подключив экземпляр ядра СУБД SQL Server.

<a name="bkmk_BindWizard"></a>

## <a name="bind-to-machine-learning-server-using-setup"></a>Привязка к Machine Learning Server с помощью программы установки

Выполните следующие действия, чтобы привязать SQL Server к Microsoft Machine Learning Server с помощью программы установки. 

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

1. В разделе **Настроить установку** проверьте компоненты для обновления и просмотрите список совместимых экземпляров.

1. На странице **лицензионное соглашение** выберите **Я принимаю эти условия**, чтобы принять условия лицензирования для Machine Learning Server. 

1. На последующих страницах предоставьте согласие на дополнительные условия лицензирования для всех выбранных компонентов с открытым кодом, например Microsoft R Open или Python Anaconda.

1. На странице **Почти готово** запишите папку установки. Папка по умолчанию: \Program Files\Microsoft\ML Server.

    Если вы хотите изменить папку установки, нажмите кнопку **Дополнительно**, чтобы вернуться на первую страницу мастера. Однако необходимо заново ввести все параметры.

Если обновление завершается сбоем, проверьте [коды ошибок SqlBindR](#sqlbindr-error-codes) для получения дополнительных сведений.

## <a name="offline-binding-no-internet-access"></a>Автономная привязка (без доступа к Интернету)

Для систем без подключения к Интернету можно загрузить установщик и CAB-файлы на компьютер, подключенный к Интернету, а затем перенести файлы на изолированный сервер.

Установщик (ServerSetup.exe) включает пакеты Microsoft (RevoScaleR, MicrosoftML, olapR, sqlRUtils). CAB-файлы предоставляют другие основные компоненты. Например, CAB-файл SRO предоставляет R Open, распространяемый корпорацией Майкрософт R с открытым кодом.

Приведенные ниже инструкции описывают, как разместить файлы для автономной установки.

1. Скачайте установщик MLSWIN93. Он загружается как один сжатый ZIP-файл. Мы рекомендуем [последнюю версию](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer), но можно также установить [более ранние версии](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components).

1. Загрузите CAB-файлы. Ниже приведены ссылки на выпуск 9.3. Если требуются более ранние версии, дополнительные ссылки можно найти в [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components). Вспомним, что Python/Anaconda можно добавить только в экземпляр Служб машинного обучения SQL Server. Предварительно обученные модели существуют как для R, так и для Python. В CAB-файле предоставляются модели на языках, которые вы используете.

    | Компонент | Скачивание |
    |---------|----------|
    | R       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | Предварительно обученная модель | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. Переместите ZIP- и CAB-файлы на целевой сервер.

1. На сервере введите `%temp%` в поле выполнения команд, чтобы получить физическое расположение временного каталога. Физический путь зависит от компьютера, но обычно это `C:\Users\<your-user-name>\AppData\Local\Temp`.

1. Поместите CAB-файлы в папку %temp%.

1. Распакуйте установщик.

1. Запустите ServerSetup.exe, следуя инструкциям на экране, чтобы завершить установку.

## <a name="command-line-operations"></a><a name="bkmk_BindCmd"></a>Операции командной строки


> [!TIP]
> Не удается найти SqlBindR? Возможно, вы не запустили программу установки.
> SqlBindR доступен только после запуска программы установки Machine Learning Server.

1. Откройте командную строку от имени администратора и перейдите в папку, содержащую sqlbindr.exe. Путь по умолчанию: C:\Program Files\Microsoft\MLServer\Setup

2. Выполните следующую команду, чтобы просмотреть список доступных экземпляров: `SqlBindR.exe /list`.
  
   Запишите полное имя экземпляра. Например, имя экземпляра может быть MSSQL14.MSSQLSERVER для экземпляра по умолчанию или что-то вроде SERVERNAME.МОЙ_ИМЕНОВАННЫЙ_ЭКЗЕМПЛЯР.

3. Выполните команду **SqlBindR.exe** с аргументом */bind*. Укажите имя обновляемого экземпляра, используя имя экземпляра, возвращенное на предыдущем шаге.

   Например, чтобы обновить экземпляр по умолчанию, введите следующую команду: `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. После завершения обновления перезапустите службу панели запуска, связанную с любым измененным экземпляром.

## <a name="revert-or-unbind-an-instance"></a><a name="bkmk_Unbind"></a>Отмена привязки экземпляра

Вы можете восстановить привязанный экземпляр до первоначальной установки компонентов R и Python, выполненной программой установки SQL Server. Возврат к обслуживанию на SQL Server выполняется в три этапа.

+ [Шаг 1. Удаление привязки к Microsoft Machine Learning Server](#step-1-unbind)
+ [Шаг 2. Восстановление исходного состояния экземпляра](#step-2-restore)
+ [Шаг 3. Переустановка пакетов, добавленных в установку](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Шаг 1. Unbind

Существует два варианта отката привязки: повторно запустите программу установки или используйте служебную программу командной строки SqlBindR.

#### <a name="unbind-using-setup"></a><a name="bkmk_wizunbind"></a> Отмена привязки с помощью программы установки

1. Найдите установщик для Machine Learning Server. Если установщик удален, загрузите его снова или скопируйте с другого компьютера.
2. Запустите установщик на компьютере с экземпляром, для которого нужно отменить привязку.
2. Установщик определяет локальные экземпляры, которые являются кандидатами для отмены привязки.
3. Снимите флажок рядом с экземпляром, который вы хотите вернуть в исходную конфигурацию.
4. Примите все лицензионные соглашения.
5. Нажмите кнопку **Готово**. Процесс займет некоторое время.

#### <a name="unbind-using-the-command-line"></a><a name="bkmk_cmdunbind"></a> Отмена привязки с помощью командной строки

1. Откройте командную строку и перейдите в папку, содержащую **sqlbindr.exe**, как описано в предыдущем разделе.

2. Выполните команду **SqlBindR.exe** с аргументом */unbind* и укажите экземпляр.

   Например, следующая команда отменяет привязку экземпляра по умолчанию:
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Шаг 2. Восстановление экземпляра SQL Server

Запустите программу установки SQL Server, чтобы восстановить экземпляр ядра СУБД с компонентами R и Python. Существовавшие ранее обновления сохраняются. Следующий шаг следует применять, если пропущено обновление для обслуживания пакетов Python и R.

Альтернативное решение: можно полностью удалить и переустановить экземпляр ядра СУБД, а затем применить все служебные обновления.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Шаг 3. Добавление сторонних пакетов

Вы могли добавить в библиотеку пакетов другие пакеты с открытым кодом или сторонние пакеты. Отмена привязки меняет расположение библиотеки пакетов по умолчанию, поэтому необходимо переустановить пакеты в библиотеку, которую теперь используют R и Python. Дополнительные сведения см. в статьях [Сведения о пакете R](../package-management/r-package-information.md) и [Установка пакета R](../package-management/install-additional-r-packages-on-sql-server.md) и [Сведения о пакете Python](../package-management/python-package-information.md) и [Установка пакета Python](../package-management/install-additional-python-packages-on-sql-server.md).

## <a name="sqlbindrexe-command-syntax"></a>Синтаксис команды SqlBindR.exe

### <a name="usage"></a>Использование

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Параметры

|Имя|Описание|
|------|------|
|*list*| Выводит список идентификаторов всех экземпляров SQL Server на текущем компьютере.|
|*bind*| Обновляет указанный экземпляр SQL Server до последней версии R Server и обеспечивает автоматическое получение экземпляром будущих обновлений для R Server.|
|*unbind*|Удаляет последнюю версию R Server из указанного экземпляра SQL Server и блокирует применение будущих обновлений R Server к экземпляру.|

<a name="sqlbindr-error-codes"><a/>

## <a name="binding-errors"></a>Ошибки привязки

Установщик Machine Learning Server и SqlBindR возвращают следующие коды ошибок и сообщения об ошибках:

|Код ошибки  | Сообщение           | Сведения               |
|------------|-------------------|-----------------------|
|Ошибка привязки 0 | Ok (успешно) | Привязка прошла без ошибок. |
|Ошибка привязки 1 | Недопустимые аргументы | Синтаксическая ошибка. |
|Ошибка привязки 2 | Недопустимое действие | Синтаксическая ошибка. |
|Ошибка привязки 3 | Недопустимый экземпляр | Экземпляр существует, но не является допустимым для привязки. |
|Ошибка привязки 4 | Не подлежит привязке | |
|Ошибка привязки 5 | Уже привязан | Вы выполнили команду *bind* , но указанный экземпляр уже привязан. |
|Ошибка привязки 6 | Сбой привязки | При отмене привязки экземпляра произошла ошибка. Эта ошибка может возникать, если запустить установщик Machine Learning Server без выбора компонентов. Для привязки необходимо выбрать экземпляр Microsoft SQL Server, а также R и Python, если это экземпляр SQL Server 2017. Эта ошибка также возникает, если SqlBindR не удалось выполнить запись в папку Program Files. Открытые сеансы или дескрипторы SQL Server приведут к этой ошибке. При возникновении этой ошибки перезагрузите компьютер и повторите действия привязки, прежде чем запускать новые сеансы.|
|Ошибка привязки 7 | Нет привязки | В экземпляре ядра СУБД имеются службы R Services или Службы машинного обучения SQL Server. Экземпляр не привязан к Microsoft Machine Learning Server. |
|Ошибка привязки 8 | Не удалось отменить привязку | При отмене привязки экземпляра произошла ошибка. |
|Ошибка привязки 9 | Экземпляры не найдены. | На этом компьютере не найдены экземпляры ядра СУБД. |

## <a name="known-issues"></a>Известные проблемы

В этом разделе перечислены известные проблемы, связанные с использованием служебной программы SqlBindR.exe, а также обновлениями Machine Learning Server, которые могут повлиять на экземпляры SQL Server.

### <a name="restoring-packages-that-were-previously-installed"></a>Восстановление ранее установленных пакетов

Если вы выполнили обновление до Microsoft R Server 9.0.1, SqlBindR.exe для этой версии не удастся полностью восстановить первоначальные пакеты или компоненты R. Следует восстановить SQL Server на экземпляре и применить все служебные выпуски. Перезапустите экземпляр.

Более поздняя версия SqlBindR автоматически восстанавливает первоначальные компоненты R, устраняя необходимость в их переустановке или повторном исправлении сервера. Однако необходимо установить все обновления пакетов R, которые могли быть добавлены после первоначальной установки.

Используйте команды R для синхронизации установленных пакетов с файловой системой с помощью записей в базе данных. Дополнительные сведения см. в разделе [Управление пакетами R для SQL Server](https://docs.microsoft.com/sql/machine-learning/package-management/install-additional-r-packages-on-sql-server).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Проблемы с несколькими обновлениями от SQL Server

Сценарий: экземпляр служб SQL Server 2016 R Services ранее обновлен до версии 9.0.1. Выполнен новый установщик для Microsoft R Server 9.1.0. Установщик показывает список всех допустимых экземпляров.
По умолчанию установщик выбирает ранее привязанные экземпляры. Если продолжить, для ранее привязанных экземпляров будет отменена привязка. В результате предыдущая установка 9.0.1 удаляется, в том числе все связанные пакеты, но новая версия Microsoft R Server (9.1.0) не устанавливается.

В качестве обходного решения можно изменить имеющуюся установку R Server следующим образом:
1. На панели управления и откройте элемент **Установка и удаление программ**.
2. Найдите Microsoft R Server и щелкните **Изменить**.
3. При запуске установщика выберите экземпляры, которые необходимо привязать к 9.1.0.

Microsoft Machine Learning Server 9.2.1 и 9.3 не имеют этой проблемы.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>Привязка или отмена привязки оставляет несколько временных папок

Удалите временные папки после завершения установки.

> [!NOTE]
> Не забудьте дождаться завершения установки. Удаление библиотек R, связанных с одной версией, и добавление новых библиотек R может занять много времени. По завершении операции временные папки удаляются.

## <a name="see-also"></a>См. также раздел

+ [Установка Machine Learning Server для Windows (с подключением к Интернету)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Установка Machine Learning Server для Windows (в автономном режиме)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Известные проблемы в Службах машинного обучения](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Объявления о компонентах из предыдущего выпуска R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Устаревшие, неподдерживаемые и измененные возможности в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
