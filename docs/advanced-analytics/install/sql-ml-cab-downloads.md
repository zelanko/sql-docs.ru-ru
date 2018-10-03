---
title: Загружаемые файлы CAB-файла для накопительные пакеты обновления SQL Server | Документация Майкрософт
description: Загрузки CAB-файла для службы машинного обучения SQL Server 2017 и SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/01/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 25568dc5a76283b18affd10ef0419f83515f6403
ms.sourcegitcommit: 615f8b5063aed679495d92a04ffbe00451d34a11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232608"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>CAB-файлов загрузки для накопительные пакеты обновления анализа в базе данных SQL Server экземпляры

Экземпляры SQL Server, настроенных для аналитики в базе данных включают функции R и Python. Эти компоненты поставляются в CAB-файлы, установки и обслуживания через программу установки SQL Server. На устройствах, подключенных к Интернету CAB обычно обновлений через Центр обновления Windows. На серверах с отключенной CAB-файлов, необходимо загрузить и применить вручную. 

В этой статье ссылки загрузки на CAB-файлы для каждого накопительного пакета обновления. Ссылки будут предоставляться для как SQL Server 2017 служб машинного обучения (R и Python), так и SQL Server 2016 R Services. Дополнительные сведения об автономных установок, см. в разделе [Установка SQL Server в машинном обучении компоненты без доступа к Интернету](sql-ml-component-install-without-internet-access.md#apply-cu).

## <a name="prerequisites"></a>предварительные требования

Начните с установки базовых показателей.

+ В SQL Server 2017 служб машинного обучения первоначальным выпуском является базовой установки. 
+ В SQL Server 2016 R Services можно начать с первоначального выпуска, SP1 или SP2. 

Можно также применить накопительные пакеты обновления на изолированном сервере.

## <a name="sql-server-2017-cabs"></a>SQL Server 2017 CABs

CAB-файлы, перечислены в обратном хронологическом порядке. При загрузке CAB-файлы и передают их на конечном компьютере, поместить их в папке например **загружает** или папке % temp % пользователя программы установки.

Выпуск  |Ссылка на скачивание  | Проблемы | 
---------|---------------|-------|
**[SQL Server 2017 CU10](https://support.microsoft.com/help/4342123)-[CU11](https://support.microsoft.com/help/4462262)** |  |  |
Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Не отличается от предыдущих версий. |
R Server      |[SRS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006287&clcid=1033)| Небольшие исправления.|
Откройте Microsoft Python     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Не отличается от предыдущих версий. |
Сервер Python    |[SPS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006805&clcid=1033)| Python rx_data_step теряет порядок строк при удалять дубликаты. <br/>SPEE сбоя определения типа данных в кластеризованном индексе columnstore. <br/>Возвращает пустую таблицу, когда столбцы содержат все значения null. |
**[SQL Server 2017 CU8](https://support.microsoft.com/help/4338363)-[CU9](https://support.microsoft.com/help/4341265)** |  |  |
Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Не отличается от предыдущих версий. |
R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
Откройте Microsoft Python     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Не отличается от предыдущих версий. |
Сервер Python    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)|
**[SQL Server 2017 CU6](https://support.microsoft.com/help/4101464)-[накопительным пакетом обновления 7](https://support.microsoft.com/help/4229789)** |  |  |
Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Не отличается от предыдущих версий. |
R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
Откройте Microsoft Python     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Не отличается от предыдущих версий. |
Сервер Python    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)| Типы данных даты и времени в запросе SPEES.<br/>улучшены сообщения об ошибках в microsoftml, если предварительно обученные модели отсутствуют.<br/> Исправления для revoscalepy преобразования, функции и переменные.|
**[SQL Server 2017 CU5](https://support.microsoft.com/help/4092643)** |  |  |
Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Не отличается от предыдущих версий. |
R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)| Длинные пути ошибки в rxInstallPackages.<br/>Подключений в замыканием на себя для RxExec.
Откройте Microsoft Python    | Не отличается от предыдущих версий. |
Сервер Python    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)| <br/>Соединения в замыканием на себя для rx_exec.
**[Накопительным пакетом обновления 4 для SQL Server 2017](https://support.microsoft.com/help/4056498)** |  |   |
Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Не отличается от предыдущих версий. |
R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
Откройте Microsoft Python     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Не отличается от предыдущих версий. |
 Сервер Python    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
**[SQL Server 2017 CU3](https://support.microsoft.com/help/4052987)** |  |  |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Откройте Microsoft Python     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Не отличается от предыдущих версий. |
Сервер Python    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)| Сериализация в revoscalepy, модель на Python с помощью [rx_serialize_model функция](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model).<br/>[Собственная Оценка](../sql-native-scoring.md) поддержки, а также усовершенствования [оценки в реальном времени](../real-time-scoring.md). 
**SQL Server 2017 [CU1](https://support.microsoft.com/help/4038634)-[накопительным пакетом обновления 2](https://support.microsoft.com/help/4052574)** |  |  |
Microsoft R Open     | [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)| Не отличается от предыдущих версий. |
R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Откройте Microsoft Python     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Не отличается от предыдущих версий. | 
Сервер Python    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) | Добавляет rx_create_col_info для возвращения сведений о схеме. <br/>Усовершенствования [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) для поддержки параллельных сценарии с использованием `RxLocalParallel` контекста вычислений.|
**Первоначальный выпуск** |  |  |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Откройте Microsoft Python     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Сервер Python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |


<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>SQL Server 2016 CABs

Для служб R SQL Server 2016 становятся выпуски базовых показателей, RTM-версии или версии пакета обновления.

Выпуск  |Ссылка на скачивание  |
---------|---------------|
**SQL Server 2016 с пакетом обновления 2 CU1 — накопительное обновление 2**     |
Microsoft R Open     |[SRO_3.2.2.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039)|
Microsoft R Server    |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
**SQL Server 2016 SP1 CU4-CU10**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)
**SQL Server 2016 SP1 CU1-CU3**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
**SQL Server 2016 с пакетом обновления 1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)
**SQL Server 2016 CU4-CU9**     |
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
**SQL Server 2016 CU2-CU3**     |
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)
**SQL Server 2016 CU1**     |
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)
**SQL Server 2016 RTM**     |
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)

> [!NOTE]
> 
> При автономной установке SQL Server 2016 SP1 CU4 или CU5 с пакетом обновления 1, скачайте SRO_3.2.2.16000_1033.cab. Если вы загрузили SRO_3.2.2.13000_1033.cab из FWLINK 831785, как указано в диалоговом окне программы установки, переименуйте файл в качестве SRO_3.2.2.16000_1033.cab перед установкой накопительного пакета обновления.

Если вы хотите просмотреть исходный код для Microsoft R, он доступен для загрузки как архив в формате .tar: [установщики скачать R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

## <a name="see-also"></a>См. также

[Применить накопительные обновления на компьютерах без доступа к Интернету](sql-ml-component-install-without-internet-access.md#apply-cu)

[Применить накопительные обновления на компьютерах, имеющих подключение к Интернету](sql-ml-component-install-without-internet-access.md#apply-cu)

[Применить накопительные обновления к отдельному серверу](sql-machine-learning-standalone-windows-install.md#apply-cu)
