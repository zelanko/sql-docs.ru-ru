---
title: Скачивания CAB-файлов для SQL Server накопительных обновлений
description: Загрузка CAB-файлов r и Python и пакетов для служб SQL Server Службы машинного обучения и SQL Server 2016 R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7b77a1fd3a0d2575f0add7badb1c5bf632d29d70
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715834"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>Загружаемые файлы CAB для накопительных обновлений SQL Server экземпляров аналитики в базе данных

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server экземпляры, настроенные для аналитики в базе данных, включают функции R и Python. Эти функции поставляются в CAB-файлах, устанавливаются и обслуживаются с помощью программы установки SQL Server. На устройствах, подключенных к Интернету, обновления CAB обычно применяются с помощью Центр обновления Windows. На отключенных серверах файлы CAB должны быть скачаны и применены вручную. 

В этой статье содержатся ссылки для загрузки файлов CAB для каждого накопительного пакета обновления. Дополнительные сведения об автономных установках см. в [статье установка SQL Server компонентов машинного обучения без доступа к Интернету](sql-ml-component-install-without-internet-access.md#apply-cu).

## <a name="prerequisites"></a>Предварительные требования

Начните с базовой установки.

+ В SQL Server Службы машинного обучения первоначальной версией является базовая установка. 
+ В службах SQL Server 2016 R можно начать с первого выпуска, с пакетом обновления 1 (SP1) или с пакетом обновления 2 (SP2). 

Можно также применить накопительные обновления к отдельному серверу.

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"

## <a name="sql-server-2017-cabs"></a>SQL Server 2017 CAB

CAB-файлы перечислены в обратном хронологическом порядке. При скачивании CAB-файлов и их переносе на целевой компьютер поместите их в удобную папку, например в **файлы загрузки** или в папку% Temp% пользователя программы установки.

|Выпуск  |Компонент | Ссылка на скачивание  | Устраненные проблемы | 
|---------|----------|----------------|------------------|
|**[SQL Server 2017 CU14](https://support.microsoft.com/help/4484710/)-[CU15](https://support.microsoft.com/help/4498951/)** |  |  |  |
| | Microsoft R Open     | [SRO_ 3.3.3.1400 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=2073898&clcid=1033)| Двоичные файлы в пакете теперь подписаны. |
| | R Server      |[SRS_ 9.2.0.1400 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=2069739&clcid=1033)| Двоичные файлы в пакете теперь подписаны. |
| | Открытие Microsoft Python     | [SPO_ 9.2.0.1400 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=2073897&clcid=1033)| Двоичные файлы в пакете теперь подписаны. |
| | Сервер Python    |[SPS_ 9.2.0.1400 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=2071421&clcid=1033)| Двоичные файлы в пакете теперь подписаны.  |
|**[SQL Server 2017 CU13](https://support.microsoft.com/help/4466404)** |  |  |  |
| | Microsoft R Open     | [SRO_ 3.3.3.1300 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Нет изменений из предыдущих версий. |
| | R Server      |[SRS_ 9.2.0.1300 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=2038263&clcid=1033)| Содержит исправление для обновления работающего [изолированного сервера R Server](https://docs.microsoft.com/machine-learning-server/what-is-operationalization), установленного с помощью программы установки SQL Server. Используйте файлы CAB CU13 и следуйте [этим инструкциям](sql-machine-learning-standalone-windows-install.md#apply-cu) , чтобы применить обновление. |
| | Открытие Microsoft Python     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Нет изменений из предыдущих версий. |
| | Сервер Python    |[SPS_ 9.2.0.1300 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=2038197&clcid=1033)| Содержит исправление для обновления работающего [изолированного сервера Python](https://docs.microsoft.com/machine-learning-server/what-is-operationalization), установленного с помощью программы установки SQL Server. Используйте файлы CAB CU13 и следуйте [этим инструкциям](sql-machine-learning-standalone-windows-install.md#apply-cu) , чтобы применить обновление. |
|**[SQL Server 2017 CU10](https://support.microsoft.com/help/4342123)-[CU11](https://support.microsoft.com/help/4462262)-[CU12](https://support.microsoft.com/help/4464082)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Нет изменений из предыдущих версий. |
| | R Server      |[SRS_ 9.2.0.1000 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=2006287&clcid=1033)| Небольшие исправления.|
| | Открытие Microsoft Python     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Нет изменений из предыдущих версий. |
| | Сервер Python    |[SPS_ 9.2.0.1000 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=2006805&clcid=1033)| Rx_data_step Python теряет порядок строк при удалении дубликатов. <br/>Спи не удалось обнаружить тип данных в кластеризованном индексе columnstore. <br/>Возвращает пустую таблицу, если столбцы содержат все значения NULL. |
|**[SQL Server 2017 CU8](https://support.microsoft.com/help/4338363)-[CU9](https://support.microsoft.com/help/4341265)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Нет изменений из предыдущих версий. |
| | R Server      |[SRS_ 9.2.0.800 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
| | Открытие Microsoft Python     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Нет изменений из предыдущих версий. |
| | Сервер Python    |[SPS_ 9.2.0.800 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)|
|**[SQL Server 2017 CU6](https://support.microsoft.com/help/4101464)-[и накопительным](https://support.microsoft.com/help/4229789)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Нет изменений из предыдущих версий. |
| | R Server      |[SRS_ 9.2.0.600 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
| | Открытие Microsoft Python     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Нет изменений из предыдущих версий. |
| | Сервер Python    |[SPS_ 9.2.0.600 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)| Типы данных DateTime в СПИС запросе.<br/>Улучшены сообщения об ошибках в microsoftml, когда предварительно обученные модели отсутствуют.<br/> Исправления для функций и переменных преобразования revoscalepy.|
|**[SQL Server 2017 CU5](https://support.microsoft.com/help/4092643)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Нет изменений из предыдущих версий. |
| | R Server      |[SRS_ 9.2.0.500 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)| Длинные ошибки, связанные с путями, в Рксинсталлпаккажес.<br/>Подключения в обратном замыкании для RxExec.
| | Открытие Microsoft Python    | Нет изменений из предыдущих версий. |
| | Сервер Python    |[SPS_ 9.2.0.500 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)| <br/>Подключения в обратном замыкании для rx_exec.
|**[SQL Server 2017 CU4](https://support.microsoft.com/help/4056498)** |  |   |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Нет изменений из предыдущих версий. |
| | R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
| | Открытие Microsoft Python     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Нет изменений из предыдущих версий. |
| |  Сервер Python    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
|**[SQL Server 2017 CU3](https://support.microsoft.com/help/4052987)** |  |  |  |
| | Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
| | R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
| | Открытие Microsoft Python     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Нет изменений из предыдущих версий. |
| | Сервер Python    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)| Сериализация модели Python в revoscalepy с использованием [функции rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model).<br/>Поддержка [собственной оценки](../sql-native-scoring.md) , а также усовершенствования [оценки в реальном времени](../real-time-scoring.md). 
|**[SQL Server 2017 CU1](https://support.microsoft.com/help/4038634)-[Cu2](https://support.microsoft.com/help/4052574)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)| Нет изменений из предыдущих версий. |
| | R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
| | Открытие Microsoft Python     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Нет изменений из предыдущих версий. | 
| | Сервер Python    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) | Добавляет rx_create_col_info для возврата сведений о схеме. <br/>Усовершенствования в [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) для поддержки параллельных сценариев с использованием `RxLocalParallel` контекста вычислений.|
|**Первоначальный выпуск** |  |  |
| | Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
| | R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
| | Открытие Microsoft Python     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
| | Сервер Python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |

::: moniker-end

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>SQL Server 2016 CAB

Для SQL Server 2016 служб R базовые выпуски — это либо версия RTM, либо версия пакета обновления.

|Выпуск  |Ссылка на скачивание  |
|---------|---------------|
|**SQL Server 2016 SP2 CU6**     |
|Microsoft R Open     |[SRO_ 3.2.2.20100 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=2079936&clcid=1033)|
|Microsoft R Server    |[SRS_ 8.0.3.20100 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=2079933&clcid=1033)|
|**SQL Server 2016 с пакетом обновления 2 (SP2) CU1-CU5**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_ 8.0.3.20000 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
|**SQL Server 2016 SP2**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)|
|**SQL Server 2016 SP1 CU14**     |
|Microsoft R Open     |[SRO_ 3.2.2.16100 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=2080130&clcid=1033)|
|Microsoft R Server    |[SRS_ 8.0.3.17200 _1033. cab](https://go.microsoft.com/fwlink/?LinkId=2079935&clcid=1033)|
|**SQL Server 2016 SP1 CU1-CU13**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
|**SQL Server 2016 SP1**     |
|Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)|
|Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)|
|**SQL Server 2016 CU4-CU9**     |
|Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
|Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
|**SQL Server 2016 CU2-CU3**     |
|Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)|
|Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)|
|**SQL Server 2016 CU1**     |
|Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)|
|Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)|
|**SQL Server 2016 RTM**     |
|Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)|
|Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)|

> [!NOTE]
> 
> При установке SQL Server 2016 с пакетом обновления 1 (SP1) CU4 или SP1 CU5 offline Скачайте файл SRO_ 3.2.2.16000 _1033. cab. Если вы скачали SRO_ 3.2.2.13000 _1033. cab из FWLINK 831785, как указано в диалоговом окне установки, переименуйте файл как SRO_ 3.2.2.16000 _1033. cab перед установкой накопительного пакета обновления.

Если вы хотите просмотреть исходный код Microsoft R, он доступен для загрузки в виде архива в формате tar: [Скачать установщики R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

[Применение накопительных обновлений на компьютерах без доступа к Интернету](sql-ml-component-install-without-internet-access.md#apply-cu)

[Применение накопительных обновлений на компьютерах с подключением к Интернету](sql-ml-component-install-without-internet-access.md#apply-cu)

[Применение накопительных обновлений к отдельному серверу](sql-machine-learning-standalone-windows-install.md#apply-cu)
