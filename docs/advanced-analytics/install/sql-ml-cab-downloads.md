---
title: Загружаемые файлы CAB-файла для накопительные пакеты обновления SQL Server | Документация Майкрософт
description: Загрузки CAB-файла для службы машинного обучения SQL Server 2017 и SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6a2893e976e64315a1aad742062e962269439b72
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566325"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>CAB-файлов загрузки для накопительные пакеты обновления анализа в базе данных SQL Server экземпляры

Экземпляров SQL Server, настроенных для аналитики в базе данных включают функции R и Python, которые поставляются в CAB-файлы, установленные и обслуживаемых через программу установки SQL Server. 

На серверах, подключенных к Интернету CAB обычно обновлений через Центр обновления Windows. Отключенные серверы должны обновляться вручную. В этой статье ссылки загрузки на CAB-файлы для каждого накопительного пакета обновления SQL Server 2017 служб машинного обучения (R и Python) - или SQL Server 2016 R Services - таким образом, можно вручную обновить серверы, без подключения к Интернету. 

## <a name="prerequisites"></a>предварительные требования

Начните с установки базовых показателей.

+ В SQL Server 2017 служб машинного обучения первоначальным выпуском является базовой установки. 

+ В SQL Server 2016 R Services можно начать с первоначального выпуска, SP1 или SP2. 

Дополнительные сведения см. в разделе [Установка SQL Server в машинном обучении компоненты без доступа к Интернету](sql-ml-component-install-without-internet-access.md).

После установки базовых показателей, можно выполнить [выполнить интегрированное обновление](sql-ml-component-install-without-internet-access.md#slipstream-upgrades) , включает файлы CAB-файла с помощью функции обновленные машинного обучения.

CAB-файлы, перечислены в обратном хронологическом порядке. При загрузке CAB-файлы и передают их на конечном компьютере, поместить их в папке например **загружает** или папке % temp % пользователя программы установки.

## <a name="sql-server-2017-cabs"></a>SQL Server 2017 CABs

Выпуск  |Ссылка на скачивание  |
---------|---------|
**SQL Server 2017 CU8-CU9** |
Microsoft R Open     |без изменений. использовать предыдущее [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
Откройте Microsoft Python     |без изменений. использовать предыдущее [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Сервер Microsoft Python    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)]|
**SQL Server 2017 CU6-накопительным пакетом обновления 7** |
Microsoft R Open     |без изменений. использовать предыдущее [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
Откройте Microsoft Python     |без изменений. использовать предыдущее [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Сервер Microsoft Python    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)|
**SQL Server 2017 CU5** |
Microsoft R Open     |без изменений. использовать предыдущее [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)|
Откройте Microsoft Python     |без изменений. использовать предыдущее [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Сервер Microsoft Python    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)|
**Накопительным пакетом обновления 4 для SQL Server 2017** |
Microsoft R Open     |без изменений. использовать предыдущее [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
Откройте Microsoft Python     |без изменений. использовать предыдущее [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Сервер Microsoft Python    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
**SQL Server 2017 CU3** |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Откройте Microsoft Python     |без изменений. использовать предыдущее [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Сервер Microsoft Python    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)|
**SQL Server 2017 CU1 — накопительное обновление 2** |
Microsoft R Open     |без изменений. использовать предыдущее [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Откройте Microsoft Python     |без изменений. использовать предыдущее [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Сервер Microsoft Python    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) |
**Первоначальный выпуск SQL Server 2017** |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Откройте Microsoft Python     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Сервер Microsoft Python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |


<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>SQL Server 2016 CABs

Для служб R SQL Server 2016 становятся выпуски базовых показателей, RTM-версии или версии пакета обновления.

Выпуск  |Ссылка на скачивание  |
---------|---------------|
**SQL Server 2016 с пакетом обновления 2 CU1 — накопительное обновление 2**     |
Microsoft R Open     |[SRO_3.2.2.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039)|
Microsoft R Server    |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
**SQL Server 2016 SP1 CU4-CU10**     |
Microsoft R Open     |без изменений. использовать предыдущее [SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)
**SQL Server 2016 SP1 CU1-CU3**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
**SQL Server 2016 с пакетом обновления 1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)=
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

# <a name="see-also"></a>См. также

[Установка SQL Server в машинном обучении компоненты без доступа к Интернету](sql-ml-component-install-without-internet-access.md)
