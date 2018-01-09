---
title: "Установка компонентов обучения компьютер без доступа к Интернету | Документы Microsoft"
ms.custom: 
ms.date: 01/08/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: "30"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: b84c15fba4b363eee589b6ff1d2a19d142100c32
ms.sourcegitcommit: 60d0c9415630094a49d4ca9e4e18c3faa694f034
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="installing-machine-learning-components-without-internet-access"></a>Установка компонентов обучения компьютер без доступа к Интернету

Поскольку компоненты R и Python, предоставляемых с SQL Server 2016 и 2017 г. SQL Server открытым исходным кодом, корпорация Майкрософт не устанавливает компоненты R или Python по умолчанию. Вместо этого мы предоставляют связанные установщики и объединенными пакетов для удобства в центре загрузки Майкрософт и других надежных сайтов. Должен дать согласие соответствующая лицензия, и затем программу установки SQL Server устанавливает компоненты R или Python.

В этом разделе предоставляются места загрузки для программы установки и сведения о процессе установки в автономном режиме.

## <a name="overview-of-the-offline-installation-process"></a>Общие сведения о процессе установки в автономном режиме

Как правило программа установки компонентов компьютера, используемого в SQL Server 2016 и 2017 г. SQL Server требуется подключение к Интернету. При запуске программы установки SQL Server, если выбран машинного обучения параметров, программа установки проверяет наличие Python или R установщики, как хорошо, как и любые другие необходимые компоненты.

+ **Если компьютер подключен к Интернету**

    SQL Server находит и загружает компоненты для вас и затем устанавливает их во время установки. Примите условия лицензии отдельно для каждого открытого компонента (R или Python), которые установки.

+ **Если компьютер не имеет доступа к Интернету**

    Перед продолжением установки необходимо загрузить дополнительные установщиков. Как минимум Загрузите R или Python установщики, которые поддерживаются для используемой версии SQL Server, который вы устанавливаете.

    В зависимости от конфигурации сервера могут понадобиться дополнительные компоненты.  В разделе [дополнительных компонентов](#bkmk_OtherComponents) подробные сведения.

    После загрузки установщики, они используются при установке компонента в ходе установки SQL Server.

### <a name="step-1-obtain-additional-installers"></a>Шаг 1. Получение дополнительных установщиков

**Для R**

Язык R поддерживается в SQL Server 2016 и 2017 г. SQL Server. Открытым исходным кодом и собственных компонентов требуются два разных установщика. Мастер установки SQL Server гарантирует, что они установлены в правильном порядке.

+ Установщики с **SRO** в имени содержатся компоненты открытым исходным кодом.
+ Установщики с **SRS** в имени содержат компоненты, предоставляемые корпорацией Майкрософт, включая те, для интеграции базы данных.

**Для Python**

Язык Python поддерживается только в 2017 г. SQL Server. Также существуют два отдельных установщика, которые необходимо загрузить.

+ Установщики с **SPO** в имени для Microsoft Python Open и предоставляют компоненты открытым исходным кодом.
+ Установщики с **SPS** в имени для сервера Microsoft Python и содержать компоненты, предоставляемые корпорацией Майкрософт, включая те, для интеграции базы данных.

**Сведения о загрузке**

1. Загрузите установщиков из [сайтов Центра загрузки Майкрософт](#installerlocs) на компьютер с доступом в Интернет и сохраните установщик, а не его выполнение.
2. Скопируйте файлы программы установки (CAB) на компьютере, где вы собираетесь установить компоненты машины обучения.
3. В SQL Server 2016 мастер установки по умолчанию установлен английский. Для установки с помощью другого языка необходимы изменения имени файла установщика, как описано здесь: [необходимые изменения для разных языковых стандартов](#modslocales).
    Для SQL Server 2017 г нужный язык определяется на основе языкового экземпляра.
4. Загрузите дополнительные компоненты, которые требуются, такие как MPI или .NET Core.
5. При необходимости можно загрузить архивированного исходного кода для компонентов открытым исходным кодом, но это не является обязательным для установки SQL Server и можно выполнить в любое время. Дополнительные сведения см. в разделе [R Server для Windows](https://docs.microsoft.com/r-server/install/r-server-install-windows).

Пошаговое руководство по процессу установки в автономном режиме для служб R в SQL Server 2016, мы рекомендуем статьи по [SQL Server группа консультантов по](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/). статья включает снимки экрана и также рассматриваются сценарии установки исправлений и интегрированной установки.

### <a name="step-2-run-offline-setup-using-the-sql-server-setup-wizard"></a>Шаг 2. Запустите программу установки вне сети, с помощью мастера установки SQL Server

1. Запустите мастер установки SQL Server.
2. После установки мастера лицензирования страница отображается, нажмите кнопку **Accept**.
3. Откроется диалоговое окно, запрашивающее **путь установки** необходимые пакеты.
4. Нажмите кнопку **Обзор** чтобы найти папку, содержащую файлы установщика, скопированное ранее.
5. Если нужные файлы найдены, вы можете щелкнуть **Далее**, что означает, что компоненты доступны.
10. Завершите работу мастера установки SQL Server.
11. Выполните необходимые действия после установки, чтобы убедитесь, что служба включена.

## <a name="installerlocs"></a>Где можно загрузить компонентов машины обучения

> [!NOTE]
> Убедитесь, что для получения файлов, которые соответствуют версии SQL Server при установке.
> 
> Начиная с SQL Server 2017 г CTP 2.0 обеспечивают поддержку Python. Более ранние версии, включая SQL Server 2016, не поддерживают Python.

+ [Для получения компонентов R для SQL Server 2016](#bkmk_2016Installers)

+ [Для получения компонентов R или Python для SQL Server 2017 г.](#bkmk_2017Installers)

### <a name="bkmk_2017Installers"></a>Загружаемые файлы для SQL Server 2017 г.

Выпуск  |Ссылка на скачивание  |
---------|---------|
**2017 г. SQL Server CTP 1**     |
Microsoft R Open     |[SRO_3.3.0.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)
Microsoft R Server     |[SRS_9.0.0.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)
**SQL Server CTP 2017 г 1.1** |
Microsoft R Open     |[SRO_3.3.2.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=834568)
Microsoft R Server     |[SRS_9.0.1.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=834567)
**SQL Server CTP 2017 г. 1.4** |
Microsoft R Open     |[SRO_3.3.2.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842483)
Microsoft R Server     |[SRS_9.0.2.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842482)
**2017 г. SQL Server CTP 2.0** |
Microsoft R Open     |[SRO_3.3.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842800)
Microsoft R Server     |[SRS_9.1.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842799)
Откройте Microsoft Python     |[SPO_9.1.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842828)
Сервер Microsoft Python    |[SPS_9.1.0.0__1033.cab](https://go.microsoft.com/fwlink/?LinkId=842848)
**SQL Server 2017 г., RC1** |
Microsoft R Open     |[SRO_3.3.3.22_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851503)|
Microsoft R Server     |[SRS_9.2.0.22_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851498)|
Откройте Microsoft Python     |[SPO_9.2.0.22_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851499)|
Сервер Microsoft Python    |[SPS_9.2.0.22_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851504)|
**SQL Server 2017 г. версия-Кандидат 2** |
Microsoft R Open     |[SRO_3.3.3.23_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851493)|
Microsoft R Server     |[SRS_9.2.0.23_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851505)|
Откройте Microsoft Python     |[SPO_9.2.0.23_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851506)|
Сервер Microsoft Python    |[SPS_9.2.0.23_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851497)|
**SQL Server RTM 2017 г.** |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Откройте Microsoft Python     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Сервер Microsoft Python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |
**SQL Server 2017 г. CU1** |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Откройте Microsoft Python     |без изменений; использовать предыдущее |
Сервер Microsoft Python    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) |
**SQL Server 2017 г. с накопительным обновлением 2** |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server      |без изменений; использовать предыдущее|
Откройте Microsoft Python     |без изменений; использовать предыдущее|
Сервер Microsoft Python    |без изменений; использовать предыдущее|
**CU3 SQL Server 2017 г.** |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Откройте Microsoft Python     |без изменений; использовать предыдущее|
Сервер Microsoft Python    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)|

### <a name="bkmk_2016Installers"></a>Загружаемые файлы для SQL Server 2016

> [!IMPORTANT]
> 
> При установке SQL Server 2016 SP1 CU4 или SP1 CU5 вне сети, загрузите SRO_3.2.2.16000_1033.cab. Если вы загрузили SRO_3.2.2.13000_1033.cab из FWLINK 831785, как указано в диалоговом окне программы установки, переименуйте файл как SRO_3.2.2.16000_1033.cab перед установкой накопительного пакета обновления.

Выпуск  |Ссылка на скачивание  |
---------|---------|
**SQL Server 2016 RTM**     |
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)
**SQL Server 2016 с накопительным пакетом обновления 1**     |
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)
**SQL Server 2016 с накопительным пакетом обновления 2**     |
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)
**SQL Server 2016 с накопительным пакетом обновления 3**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server     | без изменений; использовать предыдущее |
**SQL Server 2016 накопительным пакетом обновления 4**     |
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
**SQL Server 2016 накопительным пакетом обновления 5**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server     |без изменений; использовать предыдущее|
**SQL Server 2016 накопительным пакетом обновления 6**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server     |[SRS_8.0.3.14000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850316)  |
**SQL Server 2016 накопительным пакетом обновления 7**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server     |без изменений; использовать предыдущее |
**SQL Server 2016 с пакетом обновления 1 (SP1)**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)
**SQL Server 2016 с пакетом обновления 1 CU1**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server     |без изменений; использовать предыдущее|
**SQL Server 2016 с пакетом обновления 1 с накопительным обновлением 2**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
**SQL Server 2016 с пакетом обновления 1 CU3**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server     |без изменений; использовать предыдущее|
**SQL Server 2016 с пакетом обновления 1 CU4 и GDR**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)
**CU5 SQL Server 2016 с пакетом обновления 1**     |
Microsoft R Open     |без изменений; использовать предыдущее|
Microsoft R Server    |без изменений; использовать предыдущее |

Если вы хотите просмотреть исходный код для Microsoft R, его можно загрузить как архив в формате TAR или: [установщиков загрузки R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

### <a name = "bkmk_OtherComponents"></a>Предварительные условия

В зависимости от среды может потребоваться создать локальные копии установщиков для следующих необходимых компонентов.

Компонент  |Version
---------|---------
[Поставщик Microsoft AS OLE DB для SQL Server 2016](https://go.microsoft.com/fwlink/?linkid=834405)     |  13.0.1601.5
[Microsoft .NET Core](https://go.microsoft.com/fwlink/?linkid=834319)     | 1.0.1
[Microsoft MPI](https://go.microsoft.com/fwlink/?linkid=834316)     | 7.1.12437.25
[Распространяемый пакет Microsoft Visual C++ 2013](https://go.microsoft.com/fwlink/?linkid=799853)     | 12.0.30501.0
[Распространяемый компонент Microsoft Visual C++ 2015](https://go.microsoft.com/fwlink/?linkid=828641)     | 14.0.23026.0

## <a name="modslocales"></a>Установка для разных языковых стандартов

Если вы загрузите. CAB-файлы в процессе установки SQL Server на компьютере с доступом в Интернет, мастер установки обнаруживает местных языках и автоматически изменяет язык установщика.

Тем не менее в зависимости от установленной версии SQL Server, может потребоваться выполнить дополнительные действия, чтобы установить компоненты R, локализованные на компьютере без доступа к Интернету.

+ **Для SQL Server 2016**

   После загрузки установщики R к локальному общему ресурсу, может потребоваться вручную изменить имя для вставки идентификатор нужный язык для языка, на котором вы устанавливаете загруженные файлы.

    Например, чтобы установить японскую версию SQL Server, в имя файла нужно изменить из SRS_8.0.3.0_**1033**.cab для SRS_8.0.3.0_**1041**.cab.

    > [!IMPORTANT]
    > Эта проблема относится только к предыдущих версий и была устранена в последующих выпусках.
    > **Используйте этот способ только в том случае, если программа установки возвращает сообщение о том, что он не сможет установить нужный язык.**

+ **Для SQL Server 2017 г.**

    Загрузить. CAB-файл для компонентов R или Python.
    
    Язык определяется на основе языкового стандарта сервера. Автоматически устанавливается с помощью загруженного нужный языковой стандарт. CAB-файл.

## <a name="slipstream-upgrades"></a>Интегрированная установка обновлений

Интегрированная установка — это возможность применить исправление или обновление для экземпляра, установка которого завершилась сбоем, чтобы устранить существующие неполадки. Преимущество этого метода заключается в том, что SQL Server обновляется прямо во время выполнения установки, поэтому необходимость в последующей перезагрузке отсутствует.

+ Если у сервера нет доступа к Интернету, скачайте установщик SQL Server, а затем соответствующие версии установщиков компонентов R и **запустите** процесс обновления.  Компоненты R, которые не включаются по умолчанию вместе с SQL Server.

+ При наличии *добавление* этим компонентам *существующие* установки, использовать обновленную версию программы установки SQL Server, и соответствующим обновленным версии дополнительных компонентов. При указании функции R должна быть установлена программа установки ищет соответствующую версию установщики для машинного обучения компонентов.

## <a name="command-line-arguments-for-specifying-component-locations"></a>Аргументы командной строки для указания расположения компонентов

При выполнении автономной установки из командной строки, необходимо указать следующие аргументы командной строки для указания расположения компонентов, которые вы загрузили заранее. Тем не менее необходимо задать любые дополнительные флаги, чтобы установить необходимые дополнительные компоненты; по умолчанию автоматически устанавливаются необходимые компоненты, такие как .NET core.

**Расположение программы установки**

- `/UPDATESOURCE`Чтобы указать расположение локального файла, содержащего программу установки SQL Server
- `/MRCACHEDIRECTORY`Чтобы указать папку, содержащую CAB-файлов компонентов R
- `/MPYCACHEDIRECTORY`Чтобы указать папку, содержащую CAB-файлов компонентов Python

**Компоненты R в SQL Server 2016**

- `/ADVANCEDANALYTICS`Для получения поддержки ядра для внешних скриптов
- `/IACCEPTROPENLICENSETERMS="True"`Чтобы принять соглашение о лицензировании отдельных R

**Компоненты R в SQL Server 2017 г.**

- `/ADVANCEDANALYTICS`Для получения поддержки ядра для внешних скриптов
- `/SQL_INST_MR`для использования R
- `/IACCEPTROPENLICENSETERMS="True"`Чтобы принять соглашение о лицензировании отдельных R

**Компоненты Python в SQL Server 2017 г.**

- `/ADVANCEDANALYTICS`Для получения поддержки ядра для внешних скриптов
- `/SQL_INST_MPY`Чтобы использовать Python
- `/IACCEPTPYTHONLICENSETERMS="True"`Чтобы принять соглашение о лицензировании отдельных Python


> [!NOTE]
> Нельзя изменять учетную запись службы для запуска с помощью параметров в программе установки SQL Server. Рекомендуется установить с использованием учетных записей служб по умолчанию и затем изменить учетную запись службы, используя диспетчер конфигурации SQL Server. После этого убедитесь, что перезапуск службы панели запуска.

## <a name="see-also"></a>См. также раздел

[Установка Microsoft R Server](https://docs.microsoft.com/r-server/install/r-server-install-windows)

Группа поддержки служб R в этой статье показано, как выполнить автоматическую установку или обновление служб R в SQL Server 2016: [развертывание служб R на компьютерах без доступа к Интернету](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/).
